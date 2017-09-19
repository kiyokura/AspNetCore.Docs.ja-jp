---
title: "Details メソッドと Delete メソッドの確認"
author: rick-anderson
description: "単純な ASP.NET Core MVC アプリの Details コントローラー メソッドとビュー。"
keywords: ASP.NET Core,
ms.author: riande
manager: wpickett
ms.date: 03/07/2017
ms.topic: get-started-article
ms.assetid: 870192b4-8d4f-45c7-8c14-83d02bc0ad79
ms.technology: aspnet
ms.prod: asp.net-core
uid: tutorials/first-mvc-app/details
ms.openlocfilehash: bab93a2faa122d9d6d2e71367519baa09bd76bd1
ms.sourcegitcommit: 0b6c8e6d81d2b3c161cd375036eecbace46a9707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/11/2017
---
# <a name="examining-the-details-and-delete-methods"></a><span data-ttu-id="d05bc-104">Details メソッドと Delete メソッドの確認</span><span class="sxs-lookup"><span data-stu-id="d05bc-104">Examining the Details and Delete methods</span></span>

<span data-ttu-id="d05bc-105">作成者: [Rick Anderson](https://twitter.com/RickAndMSFT)</span><span class="sxs-lookup"><span data-stu-id="d05bc-105">By [Rick Anderson](https://twitter.com/RickAndMSFT)</span></span>

<span data-ttu-id="d05bc-106">Movie コントローラーを開き、`Details` メソッドを調べます。</span><span class="sxs-lookup"><span data-stu-id="d05bc-106">Open the Movie controller and examine the `Details` method:</span></span>

<span data-ttu-id="d05bc-107">[!code-csharp[Main](start-mvc/sample/MvcMovie/Controllers/MoviesController.cs?name=snippet_details)]</span><span class="sxs-lookup"><span data-stu-id="d05bc-107">[!code-csharp[Main](start-mvc/sample/MvcMovie/Controllers/MoviesController.cs?name=snippet_details)]</span></span>

<span data-ttu-id="d05bc-108">このアクション メソッドを作成した MVC スキャフォールディング エンジンがコメントを追加します。そのコメントには、メソッドを呼び出した HTTP 要求が示されます。</span><span class="sxs-lookup"><span data-stu-id="d05bc-108">The MVC scaffolding engine that created this action method adds a comment showing an HTTP request that invokes the method.</span></span> <span data-ttu-id="d05bc-109">今回の例では、URL セグメントが 3 つある GET 要求です。セグメントの内訳は、`Movies` コントローラー、`Details` メソッド、`id` 値です。</span><span class="sxs-lookup"><span data-stu-id="d05bc-109">In this case it's a GET request with three URL segments, the `Movies` controller, the `Details` method and an `id` value.</span></span> <span data-ttu-id="d05bc-110">これらのセグメントは *Startup.cs* で定義されていることを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="d05bc-110">Recall these segments are defined in *Startup.cs*.</span></span>

<span data-ttu-id="d05bc-111">[!code-csharp[Main](start-mvc/sample/MvcMovie/Startup.cs?highlight=5&name=snippet_1)]</span><span class="sxs-lookup"><span data-stu-id="d05bc-111">[!code-csharp[Main](start-mvc/sample/MvcMovie/Startup.cs?highlight=5&name=snippet_1)]</span></span>

<span data-ttu-id="d05bc-112">EF は、`SingleOrDefaultAsync` メソッドによるデータの検索を簡単にします。</span><span class="sxs-lookup"><span data-stu-id="d05bc-112">EF makes it easy to search for data using the `SingleOrDefaultAsync` method.</span></span> <span data-ttu-id="d05bc-113">このメソッドには重要なセキュリティ機能が組み込まれています。それは、検索メソッドがムービーを見つけたということをコードが確認し、それからその見つけたムービーで何らかの処理を行うということです。</span><span class="sxs-lookup"><span data-stu-id="d05bc-113">An important security feature built into the method is that the code verifies that the search method has found a movie before it tries to do anything with it.</span></span> <span data-ttu-id="d05bc-114">たとえば、リンクが作成する URL を `http://localhost:xxxx/Movies/Details/1` から `http://localhost:xxxx/Movies/Details/12345` のようなものに変更することで、ハッカーはサイトにエラーを誘発できます。</span><span class="sxs-lookup"><span data-stu-id="d05bc-114">For example, a hacker could introduce errors into the site by changing the URL created by the links from `http://localhost:xxxx/Movies/Details/1` to something like  `http://localhost:xxxx/Movies/Details/12345` (or some other value that doesn't represent an actual movie).</span></span> <span data-ttu-id="d05bc-115">null のムービーを確認しなかった場合、アプリは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="d05bc-115">If you did not check for a null movie, the app would throw an exception.</span></span>

<span data-ttu-id="d05bc-116">`Delete` メソッドと `DeleteConfirmed` メソッドを調べます。</span><span class="sxs-lookup"><span data-stu-id="d05bc-116">Examine the `Delete` and `DeleteConfirmed` methods.</span></span>

<span data-ttu-id="d05bc-117">[!code-csharp[Main](start-mvc/sample/MvcMovie/Controllers/MoviesController.cs?name=snippet_delete)]</span><span class="sxs-lookup"><span data-stu-id="d05bc-117">[!code-csharp[Main](start-mvc/sample/MvcMovie/Controllers/MoviesController.cs?name=snippet_delete)]</span></span>

<span data-ttu-id="d05bc-118">`HTTP GET Delete` メソッドは指定のムービーを削除せず、削除を送信 (HttpPost) できるムービービューを返します。</span><span class="sxs-lookup"><span data-stu-id="d05bc-118">Note that the `HTTP GET Delete` method doesn't delete the specified movie, it returns a view of the movie where you can submit (HttpPost) the deletion.</span></span> <span data-ttu-id="d05bc-119">GET 要求の応答で削除操作を実行すると (さらに言えば、編集操作、作成操作、データを変更するその他のあらゆる操作を実行すると)、セキュリティに穴が空きます。</span><span class="sxs-lookup"><span data-stu-id="d05bc-119">Performing a delete operation in response to a GET request (or for that matter, performing an edit operation, create operation, or any other operation that changes data) opens up a security hole.</span></span>

<span data-ttu-id="d05bc-120">データを削除する `[HttpPost]` メソッドの名前は「`DeleteConfirmed`」になり、HTTP POST メソッドに一意のシグネチャまたは名前が与えられます。</span><span class="sxs-lookup"><span data-stu-id="d05bc-120">The `[HttpPost]` method that deletes the data is named `DeleteConfirmed` to give the HTTP POST method a unique signature or name.</span></span> <span data-ttu-id="d05bc-121">2 つのメソッド シグネチャは下の画像のようになります。</span><span class="sxs-lookup"><span data-stu-id="d05bc-121">The two method signatures are shown below:</span></span>

<span data-ttu-id="d05bc-122">[!code-csharp[Main](start-mvc/sample/MvcMovie/Controllers/MoviesController.cs?name=snippet_delete2)]</span><span class="sxs-lookup"><span data-stu-id="d05bc-122">[!code-csharp[Main](start-mvc/sample/MvcMovie/Controllers/MoviesController.cs?name=snippet_delete2)]</span></span>

<span data-ttu-id="d05bc-123">[!code-csharp[Main](start-mvc/sample/MvcMovie/Controllers/MoviesController.cs?name=snippet_delete3)]</span><span class="sxs-lookup"><span data-stu-id="d05bc-123">[!code-csharp[Main](start-mvc/sample/MvcMovie/Controllers/MoviesController.cs?name=snippet_delete3)]</span></span>


<span data-ttu-id="d05bc-124">共通言語ランタイム (CLR) は、オーバーロードのメソッドに一意のパラメーター シグネチャを持つことを要求します (メソッド名は同じであるが、パラメーターの一覧が異なる)。</span><span class="sxs-lookup"><span data-stu-id="d05bc-124">The common language runtime (CLR) requires overloaded methods to have a unique parameter signature (same method name but different list of parameters).</span></span> <span data-ttu-id="d05bc-125">ただし、ここでは、同じパラメーター シグネチャを持つ 2 つの `Delete` メソッドが必要です。GET に 1 つ、POST に 1 つです。</span><span class="sxs-lookup"><span data-stu-id="d05bc-125">However, here you need two `Delete` methods -- one for GET and one for POST -- that both have the same parameter signature.</span></span> <span data-ttu-id="d05bc-126">(いずれも、1 つの整数をパラメーターとして受け取る必要があります。)</span><span class="sxs-lookup"><span data-stu-id="d05bc-126">(They both need to accept a single integer as a parameter.)</span></span>

<span data-ttu-id="d05bc-127">この問題には 2 つの取り組み方があります。その 1 つは、メソッドに異なる名前を与えることです。</span><span class="sxs-lookup"><span data-stu-id="d05bc-127">There are two approaches to this problem, one is to give the methods different names.</span></span> <span data-ttu-id="d05bc-128">先の例では、スキャフォールディング メカニズムがこれを行いました。</span><span class="sxs-lookup"><span data-stu-id="d05bc-128">That's what the scaffolding mechanism did in the preceding example.</span></span> <span data-ttu-id="d05bc-129">ただし、これは小さな問題を引き起こします。ASP.NET が URL のセグメントをアクション メソッドに名前でマッピングします。メソッドの名前を変更すると、通常、ルーティングでそのメソッドが見つからなくなります。</span><span class="sxs-lookup"><span data-stu-id="d05bc-129">However, this introduces a small problem: ASP.NET maps segments of a URL to action methods by name, and if you rename a method, routing normally wouldn't be able to find that method.</span></span> <span data-ttu-id="d05bc-130">この解決策はこの例で確認できます。`ActionName("Delete")` 属性を `DeleteConfirmed` メソッドに追加しています。</span><span class="sxs-lookup"><span data-stu-id="d05bc-130">The solution is what you see in the example, which is to add the `ActionName("Delete")` attribute to the `DeleteConfirmed` method.</span></span> <span data-ttu-id="d05bc-131">この属性はルーティング システムにマッピングを実行します。POST 要求の /Delete/ を含む URL が `DeleteConfirmed` メソッドを見つけます。</span><span class="sxs-lookup"><span data-stu-id="d05bc-131">That attribute performs mapping for the routing system so that a URL that includes /Delete/ for a POST request will find the `DeleteConfirmed` method.</span></span>

<span data-ttu-id="d05bc-132">同じ名前とシグネチャを持つメソッドに対するもう 1 つの一般的な回避策は、POST メソッドのシグネチャを人為的に変更し、(使用されない) 余分のパラメーターを追加することです。</span><span class="sxs-lookup"><span data-stu-id="d05bc-132">Another common work around for methods that have identical names and signatures is to artificially change the signature of the POST method to include an extra (unused) parameter.</span></span> <span data-ttu-id="d05bc-133">前の投稿ではこれを行いました。`notUsed` パラメーターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="d05bc-133">That's what we did in a previous post when we added the `notUsed` parameter.</span></span> <span data-ttu-id="d05bc-134">同じことをここで、`[HttpPost] Delete` メソッドに対して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d05bc-134">You could do the same thing here for the `[HttpPost] Delete` method:</span></span>

```csharp
// POST: Movies/Delete/6
[ValidateAntiForgeryToken]
public async Task<IActionResult> Delete(int id, bool notUsed)
```

<span data-ttu-id="d05bc-135">このたびは、ASP.NET Core MVC の紹介を最後までお読みいただきありがとうございました。</span><span class="sxs-lookup"><span data-stu-id="d05bc-135">Thanks for completing this introduction to ASP.NET Core MVC.</span></span> <span data-ttu-id="d05bc-136">コメントを残していただければ幸いです。</span><span class="sxs-lookup"><span data-stu-id="d05bc-136">We appreciate any comments you leave.</span></span> <span data-ttu-id="d05bc-137">このチュートリアルの後は、「[Getting started with MVC and EF Core](xref:data/ef-mvc/intro)」 (MVC と EF Core の概要) にお進みいただくことが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="d05bc-137">[Getting started with MVC and EF Core](xref:data/ef-mvc/intro) is an excellent follow up to this tutorial.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="d05bc-138">前へ</span><span class="sxs-lookup"><span data-stu-id="d05bc-138">Previous</span></span>](validation.md)