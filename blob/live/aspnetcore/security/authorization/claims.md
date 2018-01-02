---
title: "クレーム ベースの承認"
author: rick-anderson
description: "このドキュメントでは、ASP.NET Core アプリケーションの承認の要求の確認を追加する方法について説明します。"
keywords: "ASP.NET Core、承認、信頼性情報します。"
ms.author: riande
manager: wpickett
ms.date: 10/14/2016
ms.topic: article
ms.assetid: 737be5cd-3511-4f1c-b0ce-65403fb5eed3
ms.technology: aspnet
ms.prod: asp.net-core
uid: security/authorization/claims
ms.openlocfilehash: eebaddabdd360f34b6ff44e8f4f9f1f10fda6406
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2017
---
# <a name="claims-based-authorization"></a><span data-ttu-id="ffdfb-104">クレーム ベースの承認</span><span class="sxs-lookup"><span data-stu-id="ffdfb-104">Claims-Based Authorization</span></span>

<a name="security-authorization-claims-based"></a>

<span data-ttu-id="ffdfb-105">Id を作成、割り当てることができます、信頼された相手によって発行された 1 つまたは複数のクレーム。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-105">When an identity is created it may be assigned one or more claims issued by a trusted party.</span></span> <span data-ttu-id="ffdfb-106">クレームはどのような件名を表すペアが値の名前、どのようなサブジェクトではなく操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-106">A claim is name value pair that represents what the subject is, not what the subject can do.</span></span> <span data-ttu-id="ffdfb-107">たとえば、ローカルの推進ライセンス機関によって発行された、運転免許証があります。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-107">For example, you may have a driver's license, issued by a local driving license authority.</span></span> <span data-ttu-id="ffdfb-108">免許証生年月日になっています。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-108">Your driver's license has your date of birth on it.</span></span> <span data-ttu-id="ffdfb-109">ここでは、要求の名前になります`DateOfBirth`、要求の値になります、生年月日たとえば`8th June 1970`発行者を推進するライセンス権限となります。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-109">In this case the claim name would be `DateOfBirth`, the claim value would be your date of birth, for example `8th June 1970` and the issuer would be the driving license authority.</span></span> <span data-ttu-id="ffdfb-110">クレーム ベースの承認、簡単に言うは、要求の値をチェックし、その値に基づいてリソースへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-110">Claims based authorization, at its simplest, checks the value of a claim and allows access to a resource based upon that value.</span></span> <span data-ttu-id="ffdfb-111">夜間クラブ承認プロセスにアクセスする場合の例可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-111">For example if you want access to a night club the authorization process might be:</span></span>

<span data-ttu-id="ffdfb-112">ドア セキュリティ責任者は、生年月日要求とにアクセスを許可する前に、発行者 (駆動ライセンス機関) を信頼するかどうかの日付の値に評価されます。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-112">The door security officer would evaluate the value of your date of birth claim and whether they trust the issuer (the driving license authority) before granting you access.</span></span>

<span data-ttu-id="ffdfb-113">Id は、複数の値を持つ複数の信頼性情報を含めることができ、同じ種類の複数の要求を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-113">An identity can contain multiple claims with multiple values and can contain multiple claims of the same type.</span></span>

## <a name="adding-claims-checks"></a><span data-ttu-id="ffdfb-114">チェックの要求を追加します。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-114">Adding claims checks</span></span>

<span data-ttu-id="ffdfb-115">要求ベースの承認チェックが宣言型 - 開発者は、そのファイルを埋め込みますコント ローラーや、コント ローラー内のアクションに対して、コード内で、現在のユーザーが所有する必要があります、および必要に応じて、クレームの値がアクセスするを保持する信頼性情報を指定する、要求されたリソース。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-115">Claim based authorization checks are declarative - the developer embeds them within their code, against a controller or an action within a controller, specifying claims which the current user must possess, and optionally the value the claim must hold to access the requested resource.</span></span> <span data-ttu-id="ffdfb-116">要件は、ポリシー ベースの信頼性情報、開発者は、する必要がありますビルドして、クレーム要件を表現するポリシーを登録します。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-116">Claims requirements are policy based, the developer must build and register a policy expressing the claims requirements.</span></span>

<span data-ttu-id="ffdfb-117">最も単純な種類では、クレーム、クレームが存在するポリシーを検索し、値をチェックしません。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-117">The simplest type of claim policy looks for the presence of a claim and does not check the value.</span></span>

<span data-ttu-id="ffdfb-118">最初のビルドし、ポリシーを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-118">First you need to build and register the policy.</span></span> <span data-ttu-id="ffdfb-119">通常は、一部を承認サービスの構成の一部として行われるこの`ConfigureServices()`で、 *Startup.cs*ファイル。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-119">This takes place as part of the Authorization service configuration, which normally takes part in `ConfigureServices()` in your *Startup.cs* file.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();

    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

<span data-ttu-id="ffdfb-120">ここでは、`EmployeeOnly`ポリシーの存在を確認、`EmployeeNumber`現在の id を要求します。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-120">In this case the `EmployeeOnly` policy checks for the presence of an `EmployeeNumber` claim on the current identity.</span></span>

<span data-ttu-id="ffdfb-121">ポリシーを使用して、適用する、`Policy`プロパティを`AuthorizeAttribute`ポリシーの名前を指定する属性</span><span class="sxs-lookup"><span data-stu-id="ffdfb-121">You then apply the policy using the `Policy` property on the `AuthorizeAttribute` attribute to specify the policy name;</span></span>

```csharp
[Authorize(Policy = "EmployeeOnly")]
public IActionResult VacationBalance()
{
    return View();
}
```

<span data-ttu-id="ffdfb-122">`AuthorizeAttribute`コント ローラーのポリシーに一致するユーザーが任意のアクションへのアクセスを許可するだけでは、このインスタンスで、全体のコント ローラーに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-122">The `AuthorizeAttribute` attribute can be applied to an entire controller, in this instance only identities matching the policy will be allowed access to any Action on the controller.</span></span>

```csharp
[Authorize(Policy = "EmployeeOnly")]
public class VacationController : Controller
{
    public ActionResult VacationBalance()
    {
    }
}
```

<span data-ttu-id="ffdfb-123">によって保護されているコント ローラーがある場合、`AuthorizeAttribute`属性しますが、適用する特定の操作への匿名アクセスを許可する、`AllowAnonymousAttribute`属性。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-123">If you have a controller that is protected by the `AuthorizeAttribute` attribute, but want to allow anonymous access to particular actions you apply the `AllowAnonymousAttribute` attribute.</span></span>

```csharp
[Authorize(Policy = "EmployeeOnly")]
public class VacationController : Controller
{
    public ActionResult VacationBalance()
    {
    }

    [AllowAnonymous]
    public ActionResult VacationPolicy()
    {
    }
}
```

<span data-ttu-id="ffdfb-124">ほとんどの要求は、値が付属します。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-124">Most claims come with a value.</span></span> <span data-ttu-id="ffdfb-125">ポリシーを作成するときに、有効な値の一覧を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-125">You can specify a list of allowed values when creating the policy.</span></span> <span data-ttu-id="ffdfb-126">次の例のみに成功の従業員の従業員数が 1、2、3、4 または 5。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-126">The following example would only succeed for employees whose employee number was 1, 2, 3, 4 or 5.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();

    services.AddAuthorization(options =>
    {
        options.AddPolicy("Founders", policy =>
                          policy.RequireClaim("EmployeeNumber", "1", "2", "3", "4", "5"));
    });
}
```

## <a name="multiple-policy-evaluation"></a><span data-ttu-id="ffdfb-127">複数のポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="ffdfb-127">Multiple Policy Evaluation</span></span>

<span data-ttu-id="ffdfb-128">コント ローラーまたはアクションに複数のポリシーを適用する場合は、アクセスが許可される前に、すべてのポリシーは渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-128">If you apply multiple policies to a controller or action, then all policies must pass before access is granted.</span></span> <span data-ttu-id="ffdfb-129">例:</span><span class="sxs-lookup"><span data-stu-id="ffdfb-129">For example:</span></span>

```csharp
[Authorize(Policy = "EmployeeOnly")]
public class SalaryController : Controller
{
    public ActionResult Payslip()
    {
    }

    [Authorize(Policy = "HumanResources")]
    public ActionResult UpdateSalary()
    {
    }
}
```

<span data-ttu-id="ffdfb-130">上記の例では満たされている id、`EmployeeOnly`ポリシーがアクセスできる、`Payslip`そのポリシーの処理は、コント ローラーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-130">In the above example any identity which fulfills the `EmployeeOnly` policy can access the `Payslip` action as that policy is enforced on the controller.</span></span> <span data-ttu-id="ffdfb-131">ただし呼び出すために、 `UpdateSalary` id が満たす必要がありますアクション*両方*、`EmployeeOnly`ポリシーおよび`HumanResources`ポリシー。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-131">However in order to call the `UpdateSalary` action the identity must fulfill *both* the `EmployeeOnly` policy and the `HumanResources` policy.</span></span>

<span data-ttu-id="ffdfb-132">などの生年月日要求の日付を取得するには、そこから年齢を計算する場合、経過期間のチェックは 21 以上経過し、記述する必要がより複雑なポリシーを実行する場合に、[カスタム ポリシー ハンドラー](policies.md)です。</span><span class="sxs-lookup"><span data-stu-id="ffdfb-132">If you want more complicated policies, such as taking a date of birth claim, calculating an age from it then checking the age is 21 or older then you need to write [custom policy handlers](policies.md).</span></span>