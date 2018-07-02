---
title: ASP.NET Core での Razor ページの概要
author: Rick-Anderson
description: ASP.NET Core の Razor ページを使用して、ページのコーディングに重点を置いたシナリオをより簡略化して、MVC を使用する場合よりも生産性を高める方法について説明します。
monikerRange: '>= aspnetcore-2.0'
ms.author: riande
ms.date: 05/12/2018
uid: razor-pages/index
ms.openlocfilehash: 601d6ac2cb373c40fb1de5427b0ea6c299fa1f32
ms.sourcegitcommit: a1afd04758e663d7062a5bfa8a0d4dca38f42afc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36296749"
---
# <a name="introduction-to-razor-pages-in-aspnet-core"></a><span data-ttu-id="99152-103">ASP.NET Core での Razor ページの概要</span><span class="sxs-lookup"><span data-stu-id="99152-103">Introduction to Razor Pages in ASP.NET Core</span></span>

<span data-ttu-id="99152-104">[Rick Anderson](https://twitter.com/RickAndMSFT) および [Ryan Nowak](https://github.com/rynowak) 著</span><span class="sxs-lookup"><span data-stu-id="99152-104">By [Rick Anderson](https://twitter.com/RickAndMSFT) and [Ryan Nowak](https://github.com/rynowak)</span></span>

<span data-ttu-id="99152-105">Razor ページは、ページ コーディングに重点を置いたシナリオをより簡略化し、生産性を高める ASP.NET Core MVC の新たな側面です。</span><span class="sxs-lookup"><span data-stu-id="99152-105">Razor Pages is a new aspect of ASP.NET Core MVC that makes coding page-focused scenarios easier and more productive.</span></span>

<span data-ttu-id="99152-106">モデル ビュー コントローラーのアプローチを使用するチュートリアルをお探しの場合は、「[Get started with ASP.NET Core MVC](xref:tutorials/first-mvc-app/start-mvc)」 (ASP.NET Core MVC の概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99152-106">If you're looking for a tutorial that uses the Model-View-Controller approach, see [Get started with ASP.NET Core MVC](xref:tutorials/first-mvc-app/start-mvc).</span></span>

<span data-ttu-id="99152-107">このドキュメントでは、Razor ページの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="99152-107">This document provides an introduction to Razor Pages.</span></span> <span data-ttu-id="99152-108">手順を追って説明するチュートリアルではありません。</span><span class="sxs-lookup"><span data-stu-id="99152-108">It's not a step by step tutorial.</span></span> <span data-ttu-id="99152-109">セクションの一部を理解できない場合は、「[Razor ページの概要](xref:tutorials/razor-pages/razor-pages-start)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99152-109">If you find some of the sections too advanced, see [Get started with Razor Pages](xref:tutorials/razor-pages/razor-pages-start).</span></span> <span data-ttu-id="99152-110">ASP.NET Core の概要については、「[ASP.NET Core の概要](xref:index)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99152-110">For an overview of ASP.NET Core, see the [Introduction to ASP.NET Core](xref:index).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99152-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="99152-111">Prerequisites</span></span>

[!INCLUDE [](~/includes/net-core-prereqs.md)]

<a name="rpvs17"></a>

## <a name="creating-a-razor-pages-project"></a><span data-ttu-id="99152-112">Razor ページ プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="99152-112">Creating a Razor Pages project</span></span>

# <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="99152-113">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="99152-113">Visual Studio</span></span>](#tab/visual-studio) 

<span data-ttu-id="99152-114">Visual Studio を使用して Razor ページ プロジェクトを作成する詳細な手順については、「[Razor ページの概要](xref:tutorials/razor-pages/razor-pages-start)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99152-114">See [Get started with Razor Pages](xref:tutorials/razor-pages/razor-pages-start) for detailed instructions on how to create a Razor Pages project using Visual Studio.</span></span>

# <a name="visual-studio-for-mactabvisual-studio-mac"></a>[<span data-ttu-id="99152-115">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="99152-115">Visual Studio for Mac</span></span>](#tab/visual-studio-mac)

::: moniker range=">= aspnetcore-2.1"

<span data-ttu-id="99152-116">コマンド ラインから `dotnet new webapp` を実行します。</span><span class="sxs-lookup"><span data-stu-id="99152-116">Run `dotnet new webapp` from the command line.</span></span>

[!INCLUDE[](~/includes/webapp-alias-notice.md)]

::: moniker-end

::: moniker range="= aspnetcore-2.0"

<span data-ttu-id="99152-118">コマンド ラインから `dotnet new razor` を実行します。</span><span class="sxs-lookup"><span data-stu-id="99152-118">Run `dotnet new razor` from the command line.</span></span>

::: moniker-end

<span data-ttu-id="99152-119">Visual Studio for Mac から生成された *.csproj* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="99152-119">Open the generated *.csproj* file from Visual Studio for Mac.</span></span>

# <a name="visual-studio-codetabvisual-studio-code"></a>[<span data-ttu-id="99152-120">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="99152-120">Visual Studio Code</span></span>](#tab/visual-studio-code) 

::: moniker range=">= aspnetcore-2.1"

<span data-ttu-id="99152-121">コマンド ラインから `dotnet new webapp` を実行します。</span><span class="sxs-lookup"><span data-stu-id="99152-121">Run `dotnet new webapp` from the command line.</span></span>

[!INCLUDE[](~/includes/webapp-alias-notice.md)]

::: moniker-end

::: moniker range="= aspnetcore-2.0"

<span data-ttu-id="99152-123">コマンド ラインから `dotnet new razor` を実行します。</span><span class="sxs-lookup"><span data-stu-id="99152-123">Run `dotnet new razor` from the command line.</span></span>

::: moniker-end

# <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="99152-124">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="99152-124">.NET Core CLI</span></span>](#tab/netcore-cli) 

::: moniker range=">= aspnetcore-2.1"

<span data-ttu-id="99152-125">コマンド ラインから `dotnet new webapp` を実行します。</span><span class="sxs-lookup"><span data-stu-id="99152-125">Run `dotnet new webapp` from the command line.</span></span>

[!INCLUDE[](~/includes/webapp-alias-notice.md)]

::: moniker-end

::: moniker range="= aspnetcore-2.0"

<span data-ttu-id="99152-127">コマンド ラインから `dotnet new razor` を実行します。</span><span class="sxs-lookup"><span data-stu-id="99152-127">Run `dotnet new razor` from the command line.</span></span>

::: moniker-end

---

## <a name="razor-pages"></a><span data-ttu-id="99152-128">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="99152-128">Razor Pages</span></span>

<span data-ttu-id="99152-129">Razor ページは *Startup.cs* で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="99152-129">Razor Pages is enabled in *Startup.cs*:</span></span>

[!code-cs[](index/sample/RazorPagesIntro/Startup.cs?name=snippet_Startup)]

<span data-ttu-id="99152-130">基本ページを検討します。<a name="OnGet"></a></span><span class="sxs-lookup"><span data-stu-id="99152-130">Consider a basic page: <a name="OnGet"></a></span></span>

[!code-cshtml[](index/sample/RazorPagesIntro/Pages/Index.cshtml)]

<span data-ttu-id="99152-131">上記のコードは Razor ビュー ファイルに非常によく似ています。</span><span class="sxs-lookup"><span data-stu-id="99152-131">The preceding code looks a lot like a Razor view file.</span></span> <span data-ttu-id="99152-132">違いは、`@page` ディレクティブにあります。</span><span class="sxs-lookup"><span data-stu-id="99152-132">What makes it different is the `@page` directive.</span></span> <span data-ttu-id="99152-133">`@page` はファイルを MVC アクションにします。つまり、コントローラーを経由せずに要求を直接処理します。</span><span class="sxs-lookup"><span data-stu-id="99152-133">`@page` makes the file into an MVC action - which means that it handles requests directly, without going through a controller.</span></span> <span data-ttu-id="99152-134">`@page` はページで最初の Razor ディレクティブである必要があります。</span><span class="sxs-lookup"><span data-stu-id="99152-134">`@page` must be the first Razor directive on a page.</span></span> <span data-ttu-id="99152-135">`@page` はその他の Razor コンストラクトの動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="99152-135">`@page` affects the behavior of other Razor constructs.</span></span>

<span data-ttu-id="99152-136">`PageModel` クラスを使用している類似したページが、次の 2 つのファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="99152-136">A similar page, using a `PageModel` class, is shown in the following two files.</span></span> <span data-ttu-id="99152-137">*Pages/Index2.cshtml* ファイル:</span><span class="sxs-lookup"><span data-stu-id="99152-137">The *Pages/Index2.cshtml* file:</span></span>

[!code-cshtml[](index/sample/RazorPagesIntro/Pages/Index2.cshtml)]

<span data-ttu-id="99152-138">*Pages/Index2.cshtml.cs* ページ モデル:</span><span class="sxs-lookup"><span data-stu-id="99152-138">The *Pages/Index2.cshtml.cs* page model:</span></span>

[!code-cs[](index/sample/RazorPagesIntro/Pages/Index2.cshtml.cs)]

<span data-ttu-id="99152-139">規則により、`PageModel` クラス ファイルは、Razor ページ ファイルと同じ名前に *.cs* が付加された名前になります。</span><span class="sxs-lookup"><span data-stu-id="99152-139">By convention, the `PageModel` class file has the same name as the Razor Page file with *.cs* appended.</span></span> <span data-ttu-id="99152-140">たとえば、上の Razor ページは *Pages/Index2.cshtml* になります。</span><span class="sxs-lookup"><span data-stu-id="99152-140">For example, the previous Razor Page is *Pages/Index2.cshtml*.</span></span> <span data-ttu-id="99152-141">`PageModel` クラスを含むファイル名は、*Pages/Index2.cshtml.cs* になります。</span><span class="sxs-lookup"><span data-stu-id="99152-141">The file containing the `PageModel` class is named *Pages/Index2.cshtml.cs*.</span></span>

<span data-ttu-id="99152-142">URL パスのページへの関連付けは、ファイル システム内のページの場所によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="99152-142">The associations of URL paths to pages are determined by the page's location in the file system.</span></span> <span data-ttu-id="99152-143">次の表に、Razor ページ パスと一致 URL を示します。</span><span class="sxs-lookup"><span data-stu-id="99152-143">The following table shows a Razor Page path and the matching URL:</span></span>

| <span data-ttu-id="99152-144">ファイル名とパス</span><span class="sxs-lookup"><span data-stu-id="99152-144">File name and path</span></span>               | <span data-ttu-id="99152-145">一致 URL</span><span class="sxs-lookup"><span data-stu-id="99152-145">matching URL</span></span> |
| ----------------- | ------------ |
| <span data-ttu-id="99152-146">*/Pages/Index.cshtml*</span><span class="sxs-lookup"><span data-stu-id="99152-146">*/Pages/Index.cshtml*</span></span> | <span data-ttu-id="99152-147">`/` または `/Index`</span><span class="sxs-lookup"><span data-stu-id="99152-147">`/` or `/Index`</span></span> |
| <span data-ttu-id="99152-148">*/Pages/Contact.cshtml*</span><span class="sxs-lookup"><span data-stu-id="99152-148">*/Pages/Contact.cshtml*</span></span> | `/Contact` |
| <span data-ttu-id="99152-149">*/Pages/Store/Contact.cshtml*</span><span class="sxs-lookup"><span data-stu-id="99152-149">*/Pages/Store/Contact.cshtml*</span></span> | `/Store/Contact` |
| <span data-ttu-id="99152-150">*/Pages/Store/Index.cshtml*</span><span class="sxs-lookup"><span data-stu-id="99152-150">*/Pages/Store/Index.cshtml*</span></span> | <span data-ttu-id="99152-151">`/Store` または `/Store/Index`</span><span class="sxs-lookup"><span data-stu-id="99152-151">`/Store` or `/Store/Index`</span></span> |

<span data-ttu-id="99152-152">メモ:</span><span class="sxs-lookup"><span data-stu-id="99152-152">Notes:</span></span>

* <span data-ttu-id="99152-153">既定では、ランタイムが *Pages* フォルダー内で Razor ページ ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="99152-153">The runtime looks for Razor Pages files in the *Pages* folder by default.</span></span>
* <span data-ttu-id="99152-154">`Index` は、URL にページが含まれない場合の既定のページになります。</span><span class="sxs-lookup"><span data-stu-id="99152-154">`Index` is the default page when a URL doesn't include a page.</span></span>

## <a name="writing-a-basic-form"></a><span data-ttu-id="99152-155">基本フォームの作成</span><span class="sxs-lookup"><span data-stu-id="99152-155">Writing a basic form</span></span>

<span data-ttu-id="99152-156">Razor ページは、アプリの構築時に Web ブラウザーで使用される一般的なパターンを実装しやすくするために設計されています。</span><span class="sxs-lookup"><span data-stu-id="99152-156">Razor Pages is designed to make common patterns used with web browsers easy to implement when building an app.</span></span> <span data-ttu-id="99152-157">[モデル バインド](xref:mvc/models/model-binding)、[タグ ヘルパー](xref:mvc/views/tag-helpers/intro)、および HTML ヘルパーはすべて、Razor ページ クラスで定義されたプロパティで*機能します*。</span><span class="sxs-lookup"><span data-stu-id="99152-157">[Model binding](xref:mvc/models/model-binding), [Tag Helpers](xref:mvc/views/tag-helpers/intro), and HTML helpers all *just work* with the properties defined in a Razor Page class.</span></span> <span data-ttu-id="99152-158">`Contact` モデルの基本的な "お問い合わせ" フォームを実装するページを考察します。</span><span class="sxs-lookup"><span data-stu-id="99152-158">Consider a page that implements a basic "contact us" form for the `Contact` model:</span></span>

<span data-ttu-id="99152-159">このドキュメントのサンプルでは、[Startup.cs](https://github.com/aspnet/Docs/blob/master/aspnetcore/razor-pages/index/sample/RazorPagesContacts/Startup.cs#L15-L16) ファイルで `DbContext` が初期化されます。</span><span class="sxs-lookup"><span data-stu-id="99152-159">For the samples in this document, the `DbContext` is initialized in the [Startup.cs](https://github.com/aspnet/Docs/blob/master/aspnetcore/razor-pages/index/sample/RazorPagesContacts/Startup.cs#L15-L16) file.</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Startup.cs?highlight=15-16)]

<span data-ttu-id="99152-160">データ モデル:</span><span class="sxs-lookup"><span data-stu-id="99152-160">The data model:</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Data/Customer.cs)]

<span data-ttu-id="99152-161">db コンテキスト:</span><span class="sxs-lookup"><span data-stu-id="99152-161">The db context:</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Data/AppDbContext.cs)]

<span data-ttu-id="99152-162">*Pages/Create.cshtml* ビュー ファイル:</span><span class="sxs-lookup"><span data-stu-id="99152-162">The *Pages/Create.cshtml* view file:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts/Pages/Create.cshtml)]

<span data-ttu-id="99152-163">*Pages/Create.cshtml.cs* ページ モデル:</span><span class="sxs-lookup"><span data-stu-id="99152-163">The *Pages/Create.cshtml.cs* page model:</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Pages/Create.cshtml.cs?name=snippet_ALL)]

<span data-ttu-id="99152-164">規則により、`PageModel` クラスは `<PageName>Model` と呼ばれ、ページと同じ名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="99152-164">By convention, the `PageModel` class is called `<PageName>Model` and is in the same namespace as the page.</span></span>

<span data-ttu-id="99152-165">`PageModel` クラスでは、ページの表示からロジックを分離できます。</span><span class="sxs-lookup"><span data-stu-id="99152-165">The `PageModel` class allows separation of the logic of a page from its presentation.</span></span> <span data-ttu-id="99152-166">これは、ページに送信される要求のページ ハンドラーと、ページのレンダリングに使用されるデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="99152-166">It defines page handlers for requests sent to the page and the data used to render the page.</span></span> <span data-ttu-id="99152-167">この分離により、ユーザーは[依存関係の挿入](xref:fundamentals/dependency-injection)を通じてページの依存関係を管理し、ページの[単体テスト](xref:test/razor-pages-tests)を実行できます。</span><span class="sxs-lookup"><span data-stu-id="99152-167">This separation allows you to manage page dependencies through [dependency injection](xref:fundamentals/dependency-injection) and to [unit test](xref:test/razor-pages-tests) the pages.</span></span>

<span data-ttu-id="99152-168">このページには、(ユーザーがフォームを投稿したときに) `POST` 要求で実行される `OnPostAsync` *ハンドラー メソッド*があります。</span><span class="sxs-lookup"><span data-stu-id="99152-168">The page has an `OnPostAsync` *handler method*, which runs on `POST` requests (when a user posts the form).</span></span> <span data-ttu-id="99152-169">任意の HTTP 動詞のハンドラー メソッドを追加できます。</span><span class="sxs-lookup"><span data-stu-id="99152-169">You can add handler methods for any HTTP verb.</span></span> <span data-ttu-id="99152-170">最も一般的なハンドラーは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="99152-170">The most common handlers are:</span></span>

* <span data-ttu-id="99152-171">ページに必要な状態を初期化するための `OnGet`。</span><span class="sxs-lookup"><span data-stu-id="99152-171">`OnGet` to initialize state needed for the page.</span></span> <span data-ttu-id="99152-172">[OnGet](#OnGet) サンプル。</span><span class="sxs-lookup"><span data-stu-id="99152-172">[OnGet](#OnGet) sample.</span></span>
* <span data-ttu-id="99152-173">フォームの送信を処理するための `OnPost`。</span><span class="sxs-lookup"><span data-stu-id="99152-173">`OnPost` to handle form submissions.</span></span>

<span data-ttu-id="99152-174">`Async` 名前付けサフィックスは省略可能ですが、非同期関数の規則でよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="99152-174">The `Async` naming suffix is optional but is often used by convention for asynchronous functions.</span></span> <span data-ttu-id="99152-175">上記の例の `OnPostAsync` コードは、コントローラーで通常に記述するものに似ています。</span><span class="sxs-lookup"><span data-stu-id="99152-175">The `OnPostAsync` code in the preceding example looks similar to what you would normally write in a controller.</span></span> <span data-ttu-id="99152-176">上記のコードは、Razor ページでは一般的です。</span><span class="sxs-lookup"><span data-stu-id="99152-176">The preceding code is typical for Razor Pages.</span></span> <span data-ttu-id="99152-177">[モデル バインド](xref:mvc/models/model-binding)、[検証](xref:mvc/models/validation)、およびアクションの結果などのほとんどの MVC プリミティブは共有されます。</span><span class="sxs-lookup"><span data-stu-id="99152-177">Most of the MVC primitives like [model binding](xref:mvc/models/model-binding), [validation](xref:mvc/models/validation), and action results are shared.</span></span>  <!-- Review: Ryan, can we get a list of what is shared and what isn't? -->

<span data-ttu-id="99152-178">上記の `OnPostAsync` メソッド:</span><span class="sxs-lookup"><span data-stu-id="99152-178">The previous `OnPostAsync` method:</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Pages/Create.cshtml.cs?name=snippet_OnPostAsync)]

<span data-ttu-id="99152-179">`OnPostAsync` の基本的な流れは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="99152-179">The basic flow of `OnPostAsync`:</span></span>

<span data-ttu-id="99152-180">検証エラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="99152-180">Check for validation errors.</span></span>

*  <span data-ttu-id="99152-181">エラーがない場合は、データを保存し、リダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="99152-181">If there are no errors, save the data and redirect.</span></span>
*  <span data-ttu-id="99152-182">エラーがある場合は、検証メッセージとともにページをもう一度表示します。</span><span class="sxs-lookup"><span data-stu-id="99152-182">If there are errors, show the page again with validation messages.</span></span> <span data-ttu-id="99152-183">クライアント側の検証は、従来の ASP.NET Core MVC アプリケーションと同じです。</span><span class="sxs-lookup"><span data-stu-id="99152-183">Client-side validation is identical to traditional ASP.NET Core MVC applications.</span></span> <span data-ttu-id="99152-184">多くの場合、検証エラーはクライアントで検出され、サーバーには送信されません。</span><span class="sxs-lookup"><span data-stu-id="99152-184">In many cases, validation errors would be detected on the client, and never submitted to the server.</span></span>

<span data-ttu-id="99152-185">データが正常に入力されると、`OnPostAsync` ハンドラー メソッドが `RedirectToPage` ヘルパー メソッドを呼び出して `RedirectToPageResult` のインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="99152-185">When the data is entered successfully, the `OnPostAsync` handler method calls the `RedirectToPage` helper method to return an instance of `RedirectToPageResult`.</span></span> <span data-ttu-id="99152-186">`RedirectToPage` は、`RedirectToAction` や `RedirectToRoute` と同じような新しいアクション結果ですが、ページ用にカスタマイズされています。</span><span class="sxs-lookup"><span data-stu-id="99152-186">`RedirectToPage` is a new action result, similar to `RedirectToAction` or `RedirectToRoute`, but customized for pages.</span></span> <span data-ttu-id="99152-187">上記のサンプルでは、ルート インデックス ページ (`/Index`) にリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="99152-187">In the preceding sample, it redirects to the root Index page (`/Index`).</span></span> <span data-ttu-id="99152-188">`RedirectToPage` については、「[ページの URL の生成](#url_gen)」セクションで詳しく説明されています。</span><span class="sxs-lookup"><span data-stu-id="99152-188">`RedirectToPage` is detailed in the [URL generation for Pages](#url_gen) section.</span></span>

<span data-ttu-id="99152-189">送信されたフォームに検証エラー (サーバーに渡される) があると、`OnPostAsync` ハンドラー メソッドが `Page` ヘルパー メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="99152-189">When the submitted form has validation errors (that are passed to the server), the`OnPostAsync` handler method calls the `Page` helper method.</span></span> <span data-ttu-id="99152-190">`Page` は `PageResult` のインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="99152-190">`Page` returns an instance of `PageResult`.</span></span> <span data-ttu-id="99152-191">`Page` を返すのは、コントローラーのアクションが `View` を返す方法に似ています。</span><span class="sxs-lookup"><span data-stu-id="99152-191">Returning `Page` is similar to how actions in controllers return `View`.</span></span> <span data-ttu-id="99152-192">`PageResult` はハンドラー メソッドの既定の<!-- Review  -->戻り値の型です。</span><span class="sxs-lookup"><span data-stu-id="99152-192">`PageResult` is the default <!-- Review  --> return type for a handler method.</span></span> <span data-ttu-id="99152-193">`void` を返すハンドラー メソッドがページをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="99152-193">A handler method that returns `void` renders the page.</span></span>

<span data-ttu-id="99152-194">`Customer` プロパティは `[BindProperty]` 属性を使用してモデル バインドにオプトインします。</span><span class="sxs-lookup"><span data-stu-id="99152-194">The `Customer` property uses `[BindProperty]` attribute to opt in to model binding.</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Pages/Create.cshtml.cs?name=snippet_PageModel&highlight=10-11)]

<span data-ttu-id="99152-195">既定では、Razor ページはプロパティを非 GET 動詞とのみバインドします。</span><span class="sxs-lookup"><span data-stu-id="99152-195">Razor Pages, by default, bind properties only with non-GET verbs.</span></span> <span data-ttu-id="99152-196">プロパティをバインドすることで、記述すべきコードの量を削減できます。</span><span class="sxs-lookup"><span data-stu-id="99152-196">Binding to properties can reduce the amount of code you have to write.</span></span> <span data-ttu-id="99152-197">同じプロパティを使用してバインドすることでコードを減らし、フィールド (`<input asp-for="Customer.Name" />`) からレンダリングして入力を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="99152-197">Binding reduces code by using the same property to render form fields (`<input asp-for="Customer.Name" />`) and accept the input.</span></span>

> [!NOTE]
> <span data-ttu-id="99152-198">セキュリティ上の理由から、ページ モデルのプロパティに対して GET 要求データのバインドを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99152-198">For security reasons, you must opt in to binding GET request data to page model properties.</span></span> <span data-ttu-id="99152-199">プロパティにマップする前に、ユーザー入力を確認してください。</span><span class="sxs-lookup"><span data-stu-id="99152-199">Verify user input before mapping it to properties.</span></span> <span data-ttu-id="99152-200">この動作は、クエリ文字列やルート値に依存するシナリオに対処する場合に選択すると便利です。</span><span class="sxs-lookup"><span data-stu-id="99152-200">Opting in to this behavior is useful when addressing scenarios which rely on query string or route values.</span></span>
>
> <span data-ttu-id="99152-201">GET 要求のプロパティをバインドするには、属性の `[BindProperty]` プロパティを `SupportsGet``true`: `[BindProperty(SupportsGet = true)]` に設定します</span><span class="sxs-lookup"><span data-stu-id="99152-201">To bind a property on GET requests, set the `[BindProperty]` attribute's `SupportsGet` property to `true`: `[BindProperty(SupportsGet = true)]`</span></span>

<span data-ttu-id="99152-202">ホーム ページ (*Index.cshtml*):</span><span class="sxs-lookup"><span data-stu-id="99152-202">The home page (*Index.cshtml*):</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts/Pages/Index.cshtml)]

<span data-ttu-id="99152-203">関連付けられた `PageModel` クラス (*Index.cshtml.cs*):</span><span class="sxs-lookup"><span data-stu-id="99152-203">The associated `PageModel` class (*Index.cshtml.cs*):</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Pages/Index.cshtml.cs)]

<span data-ttu-id="99152-204">*Index.cshtml* ファイルには、各連絡先の編集リンクを作成するために次のマークアップが含まれています。</span><span class="sxs-lookup"><span data-stu-id="99152-204">The *Index.cshtml* file contains the following markup to create an edit link for each contact:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts/Pages/Index.cshtml?range=21)]

<span data-ttu-id="99152-205">[アンカー タグ ヘルパー](xref:mvc/views/tag-helpers/builtin-th/anchor-tag-helper)は `asp-route-{value}` 属性を使用して編集ページへのリンクを生成しました。</span><span class="sxs-lookup"><span data-stu-id="99152-205">The [Anchor Tag Helper](xref:mvc/views/tag-helpers/builtin-th/anchor-tag-helper) used the `asp-route-{value}` attribute to generate a link to the Edit page.</span></span> <span data-ttu-id="99152-206">リンクには、連絡先 ID とともにルート データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="99152-206">The link contains route data with the contact ID.</span></span> <span data-ttu-id="99152-207">たとえば、`http://localhost:5000/Edit/1` のようにします。</span><span class="sxs-lookup"><span data-stu-id="99152-207">For example, `http://localhost:5000/Edit/1`.</span></span>

<span data-ttu-id="99152-208">*Pages/Edit.cshtml* ファイル:</span><span class="sxs-lookup"><span data-stu-id="99152-208">The *Pages/Edit.cshtml* file:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts/Pages/Edit.cshtml?highlight=1)]

<span data-ttu-id="99152-209">最初の行には `@page "{id:int}"` ディレクティブが含まれています。</span><span class="sxs-lookup"><span data-stu-id="99152-209">The first line contains the `@page "{id:int}"` directive.</span></span> <span data-ttu-id="99152-210">ルーティングの制約 `"{id:int}"` は、`int` ルート データを含むページへの要求を受け入れるようにページに指示します。</span><span class="sxs-lookup"><span data-stu-id="99152-210">The routing constraint`"{id:int}"` tells the page to accept requests to the page that contain `int` route data.</span></span> <span data-ttu-id="99152-211">ページへの要求に `int` に変換できるルート データが含まれていない場合は、ランタイムで HTTP 404 (見つかりません) エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="99152-211">If a request to the page doesn't contain route data that can be converted to an `int`, the runtime returns an HTTP 404 (not found) error.</span></span> <span data-ttu-id="99152-212">ID を省略するには、次のように `?` をルート制約に追加します。</span><span class="sxs-lookup"><span data-stu-id="99152-212">To make the ID optional, append `?` to the route constraint:</span></span>

 ```cshtml
@page "{id:int?}"
```

<span data-ttu-id="99152-213">*Pages/Edit.cshtml.cs* ファイル:</span><span class="sxs-lookup"><span data-stu-id="99152-213">The *Pages/Edit.cshtml.cs* file:</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Pages/Edit.cshtml.cs)]

<span data-ttu-id="99152-214">*Index.cshtml* ファイルには、各顧客の連絡先の削除ボタンを作成するマークアップも含まれています。</span><span class="sxs-lookup"><span data-stu-id="99152-214">The *Index.cshtml* file also contains markup to create a delete button for each customer contact:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts/Pages/Index.cshtml?range=22-23)]

<span data-ttu-id="99152-215">HTML で削除ボタンがレンダリングされる場合、その `formaction` には次のパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="99152-215">When the delete button is rendered in HTML, its `formaction` includes parameters for:</span></span>

* <span data-ttu-id="99152-216">`asp-route-id` 属性によって指定された顧客の連絡先 ID。</span><span class="sxs-lookup"><span data-stu-id="99152-216">The customer contact ID specified by the `asp-route-id` attribute.</span></span>
* <span data-ttu-id="99152-217">`asp-page-handler` 属性によって指定された `handler`。</span><span class="sxs-lookup"><span data-stu-id="99152-217">The `handler` specified by the `asp-page-handler` attribute.</span></span>

<span data-ttu-id="99152-218">顧客の連絡先 ID `1` でレンダリングされた削除ボタンの例を示します。</span><span class="sxs-lookup"><span data-stu-id="99152-218">Here is an example of a rendered delete button with a customer contact ID of `1`:</span></span>

```html
<button type="submit" formaction="/?id=1&amp;handler=delete">delete</button>
```

<span data-ttu-id="99152-219">ボタンが選択されると、フォームの `POST` 要求がサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="99152-219">When the button is selected, a form `POST` request is sent to the server.</span></span> <span data-ttu-id="99152-220">慣例により、ハンドラー メソッドの名前はスキーム `OnPost[handler]Async` に従った `handler` パラメーターの値に基づいて選択されます。</span><span class="sxs-lookup"><span data-stu-id="99152-220">By convention, the name of the handler method is selected based the value of the `handler` parameter according to the scheme `OnPost[handler]Async`.</span></span>

<span data-ttu-id="99152-221">この例では `handler` が `delete` であるため、`OnPostDeleteAsync` ハンドラー メソッドを使用して `POST` 要求が処理されます。</span><span class="sxs-lookup"><span data-stu-id="99152-221">Because the `handler` is `delete` in this example, the `OnPostDeleteAsync` handler method is used to process the `POST` request.</span></span> <span data-ttu-id="99152-222">`asp-page-handler` が `remove` などの別の値に設定されている場合、名前が `OnPostRemoveAsync` のページ ハンドラー メソッドが選択されます。</span><span class="sxs-lookup"><span data-stu-id="99152-222">If the `asp-page-handler` is set to a different value, such as `remove`, a page handler method with the name `OnPostRemoveAsync` is selected.</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Pages/Index.cshtml.cs?range=26-37)]

<span data-ttu-id="99152-223">`OnPostDeleteAsync` メソッド:</span><span class="sxs-lookup"><span data-stu-id="99152-223">The `OnPostDeleteAsync` method:</span></span>

* <span data-ttu-id="99152-224">クエリ文字列から `id` を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="99152-224">Accepts the `id` from the query string.</span></span>
* <span data-ttu-id="99152-225">`FindAsync` を使用してデータベースから顧客の連絡先を照会します。</span><span class="sxs-lookup"><span data-stu-id="99152-225">Queries the database for the customer contact with `FindAsync`.</span></span>
* <span data-ttu-id="99152-226">顧客の連絡先が見つかった場合、その連絡先は顧客の連絡先の一覧から削除されています。</span><span class="sxs-lookup"><span data-stu-id="99152-226">If the customer contact is found, they're removed from the list of customer contacts.</span></span> <span data-ttu-id="99152-227">データベースが更新されます。</span><span class="sxs-lookup"><span data-stu-id="99152-227">The database is updated.</span></span>
* <span data-ttu-id="99152-228">ルート インデックス ページ (`/Index`) にリダイレクトされるように、`RedirectToPage` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="99152-228">Calls `RedirectToPage` to redirect to the root Index page (`/Index`).</span></span>

::: moniker range=">= aspnetcore-2.1"

## <a name="mark-page-properties-required"></a><span data-ttu-id="99152-229">マーク ページのプロパティが必要</span><span class="sxs-lookup"><span data-stu-id="99152-229">Mark page properties required</span></span>

<span data-ttu-id="99152-230">`PageModel` 上でのプロパティを [必要](/dotnet/api/system.componentmodel.dataannotations.requiredattribute)属性で装飾できます。</span><span class="sxs-lookup"><span data-stu-id="99152-230">Properties on a `PageModel` can be decorated with the [Required](/dotnet/api/system.componentmodel.dataannotations.requiredattribute) attribute:</span></span>

<span data-ttu-id="99152-231">[!code-cs[](index/sample/Create.cshtml.cs?highlight=3,15-16)]</span><span class="sxs-lookup"><span data-stu-id="99152-231">[!code-cs[](index/sample/Create.cshtml.cs?highlight=3,15-16)]</span></span>

<span data-ttu-id="99152-232">詳細については、[モデルの検証](xref:mvc/models/validation)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="99152-232">See [Model validation](xref:mvc/models/validation) for more information.</span></span>

## <a name="manage-head-requests-with-the-onget-handler"></a><span data-ttu-id="99152-233">OnGet ハンドラーで HEAD 要求を管理する</span><span class="sxs-lookup"><span data-stu-id="99152-233">Manage HEAD requests with the OnGet handler</span></span>

<span data-ttu-id="99152-234">通常、HEAD ハンドラーは HEAD 要求に対して作成され、呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="99152-234">Ordinarily, a HEAD handler is created and called for HEAD requests:</span></span>

```csharp
public void OnHead()
{
    HttpContext.Response.Headers.Add("HandledBy", "Handled by OnHead!");
}
```

<span data-ttu-id="99152-235">HEAD ハンドラー (`OnHead`) が定義されていない場合、ASP.NET Core 2.1 以降では、Razor ページは GET ページ ハンドラー (`OnGet`) の呼び出しにフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="99152-235">If no HEAD handler (`OnHead`) is defined, Razor Pages falls back to calling the GET page handler (`OnGet`) in ASP.NET Core 2.1 or later.</span></span> <span data-ttu-id="99152-236">ASP.NET Core 2.1 から 2.x では、この動作を `Startup.Configure` の [SetCompatibilityVersion メソッド](xref:fundamentals/startup#setcompatibilityversion-for-aspnet-core-mvc)でオプトインします。</span><span class="sxs-lookup"><span data-stu-id="99152-236">Opt in to this behavior with the [SetCompatibilityVersion method](xref:fundamentals/startup#setcompatibilityversion-for-aspnet-core-mvc) in `Startup.Configure` for ASP.NET Core 2.1 to 2.x:</span></span>

```csharp
services.AddMvc()
    .SetCompatibilityVersion(Microsoft.AspNetCore.Mvc.CompatibilityVersion.Version_2_1);
```

<span data-ttu-id="99152-237">`SetCompatibilityVersion` は実質的に Razor ページのオプション `AllowMappingHeadRequestsToGetHandler` を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="99152-237">`SetCompatibilityVersion` effectively sets the Razor Pages option `AllowMappingHeadRequestsToGetHandler` to `true`.</span></span>

<span data-ttu-id="99152-238">`SetCompatibilityVersion` とのすべての 2.1 動作にオプトインするのではなく、明示的に特定の動作にオプトインすることもできます。</span><span class="sxs-lookup"><span data-stu-id="99152-238">Rather than opting into all 2.1 behaviors with `SetCompatibilityVersion`, you can explicitly opt-in to specific behaviors.</span></span> <span data-ttu-id="99152-239">次のコードは、マッピング HEAD 要求から GET ハンドラーへオプトインします。</span><span class="sxs-lookup"><span data-stu-id="99152-239">The following code opts into the mapping HEAD requests to the GET handler.</span></span>


```csharp
services.AddMvc()
    .AddRazorPagesOptions(options =>
    {
        options.AllowMappingHeadRequestsToGetHandler = true;
    });
```
::: moniker-end

<a name="xsrf"></a>

## <a name="xsrfcsrf-and-razor-pages"></a><span data-ttu-id="99152-240">XSRF/CSRF と Razor ページ</span><span class="sxs-lookup"><span data-stu-id="99152-240">XSRF/CSRF and Razor Pages</span></span>

<span data-ttu-id="99152-241">[偽造防止検証](xref:security/anti-request-forgery)のためにコードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="99152-241">You don't have to write any code for [antiforgery validation](xref:security/anti-request-forgery).</span></span> <span data-ttu-id="99152-242">偽造防止トークンの生成と検証は、自動的に Razor ページに含まれます。</span><span class="sxs-lookup"><span data-stu-id="99152-242">Antiforgery token generation and validation are automatically included in Razor Pages.</span></span>

<a name="layout"></a>
## <a name="using-layouts-partials-templates-and-tag-helpers-with-razor-pages"></a><span data-ttu-id="99152-243">Razor ページでのレイアウト、パーシャル、テンプレート、およびタグ ヘルパーの使用</span><span class="sxs-lookup"><span data-stu-id="99152-243">Using Layouts, partials, templates, and Tag Helpers with Razor Pages</span></span>

<span data-ttu-id="99152-244">ページは、Razor ビュー エンジンのすべての機能で動作します。</span><span class="sxs-lookup"><span data-stu-id="99152-244">Pages work with all the capabilities of the Razor view engine.</span></span> <span data-ttu-id="99152-245">レイアウト、パーシャル、テンプレート、タグ ヘルパー、*_ViewStart.cshtml*、*_ViewImports.cshtml* は、従来の Razor ビューと同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="99152-245">Layouts, partials, templates, Tag Helpers, *_ViewStart.cshtml*, *_ViewImports.cshtml* work in the same way they do for conventional Razor views.</span></span>

<span data-ttu-id="99152-246">これらの機能の一部を利用してこのページをまとめてみましょう。</span><span class="sxs-lookup"><span data-stu-id="99152-246">Let's declutter this page by taking advantage of some of those capabilities.</span></span>

<span data-ttu-id="99152-247">[レイアウト ページ](xref:mvc/views/layout)を *Pages/_Layout.cshtml* に追加します。</span><span class="sxs-lookup"><span data-stu-id="99152-247">Add a [layout page](xref:mvc/views/layout) to *Pages/_Layout.cshtml*:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts2/Pages/_LayoutSimple.cshtml)]

<span data-ttu-id="99152-248">[レイアウト](xref:mvc/views/layout)は次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="99152-248">The [Layout](xref:mvc/views/layout):</span></span>

* <span data-ttu-id="99152-249">(ページでレイアウトを止めない限り) 各ページのレイアウトを制御します。</span><span class="sxs-lookup"><span data-stu-id="99152-249">Controls the layout of each page (unless the page opts out of layout).</span></span>
* <span data-ttu-id="99152-250">JavaScript やスタイルシートなどの HTML 構造をインポートします。</span><span class="sxs-lookup"><span data-stu-id="99152-250">Imports HTML structures such as JavaScript and stylesheets.</span></span>

<span data-ttu-id="99152-251">詳細については、[レイアウトのページ](xref:mvc/views/layout)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99152-251">See [layout page](xref:mvc/views/layout) for more information.</span></span>

<span data-ttu-id="99152-252">[Layout](xref:mvc/views/layout#specifying-a-layout) プロパティは *Pages/_ViewStart.cshtml* で設定されています。</span><span class="sxs-lookup"><span data-stu-id="99152-252">The [Layout](xref:mvc/views/layout#specifying-a-layout) property is set in *Pages/_ViewStart.cshtml*:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts2/Pages/_ViewStart.cshtml)]

<span data-ttu-id="99152-253">レイアウトは、*Pages* フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="99152-253">The layout is in the *Pages* folder.</span></span> <span data-ttu-id="99152-254">ページは現在のページと同じフォルダーから開始して、階層的に他のビュー (レイアウト、テンプレート、パーシャル) を検索します。</span><span class="sxs-lookup"><span data-stu-id="99152-254">Pages look for other views (layouts, templates, partials) hierarchically, starting in the same folder as the current page.</span></span> <span data-ttu-id="99152-255">*Pages* フォルダー内のレイアウトは、*Pages* フォルダー配下の任意の Razor ページから使用できます。</span><span class="sxs-lookup"><span data-stu-id="99152-255">A layout in the *Pages* folder can be used from any Razor page under the *Pages* folder.</span></span>

<span data-ttu-id="99152-256">レイアウト ファイルを *Views/Shared* フォルダー内に配置**しない**ことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="99152-256">We recommend you **not** put the layout file in the *Views/Shared* folder.</span></span> <span data-ttu-id="99152-257">*Views/Shared* は MVC ビュー パターンです。</span><span class="sxs-lookup"><span data-stu-id="99152-257">*Views/Shared* is an MVC views pattern.</span></span> <span data-ttu-id="99152-258">Razor ページは、パス規則ではなく、フォルダー階層に依存することを意図しています。</span><span class="sxs-lookup"><span data-stu-id="99152-258">Razor Pages are meant to rely on folder hierarchy, not path conventions.</span></span>

<span data-ttu-id="99152-259">Razor ページからのビュー検索には、*Pages* フォルダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="99152-259">View search from a Razor Page includes the *Pages* folder.</span></span> <span data-ttu-id="99152-260">MVC コントローラーで使用しているレイアウト、テンプレート、およびパーシャルと、従来の Razor ビューは*機能します*。</span><span class="sxs-lookup"><span data-stu-id="99152-260">The layouts, templates, and partials you're using with MVC controllers and conventional Razor views *just work*.</span></span>

<span data-ttu-id="99152-261">*Pages/_ViewImports.cshtml* ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="99152-261">Add a *Pages/_ViewImports.cshtml* file:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts2/Pages/_ViewImports.cshtml)]

<span data-ttu-id="99152-262">`@namespace` はこのチュートリアルで後ほど説明します。</span><span class="sxs-lookup"><span data-stu-id="99152-262">`@namespace` is explained later in the tutorial.</span></span> <span data-ttu-id="99152-263">`@addTagHelper` ディレクティブにより、[組み込みタグ ヘルパー](xref:mvc/views/tag-helpers/builtin-th/Index)が *Pages* フォルダー内のすべてのページにもたらされます。</span><span class="sxs-lookup"><span data-stu-id="99152-263">The `@addTagHelper` directive brings in the [built-in Tag Helpers](xref:mvc/views/tag-helpers/builtin-th/Index) to all the pages in the *Pages* folder.</span></span>

<a name="namespace"></a>

<span data-ttu-id="99152-264">ページで `@namespace` ディレクティブが明示的に使用されている場合:</span><span class="sxs-lookup"><span data-stu-id="99152-264">When the `@namespace` directive is used explicitly on a page:</span></span>

[!code-cshtml[](index/sample/RazorPagesIntro/Pages/Customers/Namespace2.cshtml?highlight=2)]

<span data-ttu-id="99152-265">ディレクティブは、ページの名前空間を設定します。</span><span class="sxs-lookup"><span data-stu-id="99152-265">The directive sets the namespace for the page.</span></span> <span data-ttu-id="99152-266">`@model` ディレクティブには、名前空間を含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="99152-266">The `@model` directive doesn't need to include the namespace.</span></span>

<span data-ttu-id="99152-267">`@namespace` ディレクティブが *_ViewImports.cshtml* に含まれていると、指定した名前空間が `@namespace` ディレクティブをインポートするページで生成された名前空間のプレフィックスを提供します。</span><span class="sxs-lookup"><span data-stu-id="99152-267">When the `@namespace` directive is contained in *_ViewImports.cshtml*, the specified namespace supplies the prefix for the generated namespace in the Page that imports the `@namespace` directive.</span></span> <span data-ttu-id="99152-268">生成された名前空間の残りの部分 (サフィックスの部分) は、*_ViewImports.cshtml* を含むフォルダーとページを含むフォルダー間のドットで区切られた相対パスです。</span><span class="sxs-lookup"><span data-stu-id="99152-268">The rest of the generated namespace (the suffix portion) is the dot-separated relative path between the folder containing *_ViewImports.cshtml* and the folder containing the page.</span></span>

<span data-ttu-id="99152-269">たとえば、`PageModel` クラス *Pages/Customers/Edit.cshtml.cs* は名前空間を明示的に設定します。</span><span class="sxs-lookup"><span data-stu-id="99152-269">For example, the `PageModel` class *Pages/Customers/Edit.cshtml.cs* explicitly sets the namespace:</span></span>

[!code-cs[](index/sample/RazorPagesContacts2/Pages/Customers/Edit.cshtml.cs?name=snippet_namespace)]

<span data-ttu-id="99152-270">*Pages/_ViewImports.cshtml* ファイルは次の名前空間を設定します。</span><span class="sxs-lookup"><span data-stu-id="99152-270">The *Pages/_ViewImports.cshtml* file sets the following namespace:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts2/Pages/_ViewImports.cshtml?highlight=1)]

<span data-ttu-id="99152-271">*Pages/Customers/Edit.cshtml* Razor ページの生成された名前空間は、`PageModel` クラスと同じです。</span><span class="sxs-lookup"><span data-stu-id="99152-271">The generated namespace for the *Pages/Customers/Edit.cshtml* Razor Page is the same as the `PageModel` class.</span></span>

<span data-ttu-id="99152-272">`@namespace`  *は従来の Razor ビューでも機能します。*</span><span class="sxs-lookup"><span data-stu-id="99152-272">`@namespace` *also works with conventional Razor views.*</span></span>

<span data-ttu-id="99152-273">元の *Pages/Create.cshtml* ビュー ファイル:</span><span class="sxs-lookup"><span data-stu-id="99152-273">The original *Pages/Create.cshtml* view file:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts/Pages/Create.cshtml?highlight=2)]

<span data-ttu-id="99152-274">更新された *Pages/Create.cshtml* ビュー ファイル:</span><span class="sxs-lookup"><span data-stu-id="99152-274">The updated *Pages/Create.cshtml* view file:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts2/Pages/Customers/Create.cshtml?highlight=2)]

<span data-ttu-id="99152-275">[Razor ページのスタート プロジェクト](#rpvs17)には、クライアント側の検証をフックする *Pages/_ValidationScriptsPartial.cshtml* が含まれています。</span><span class="sxs-lookup"><span data-stu-id="99152-275">The [Razor Pages starter project](#rpvs17) contains the *Pages/_ValidationScriptsPartial.cshtml*, which hooks up client-side validation.</span></span>

<a name="url_gen"></a>

## <a name="url-generation-for-pages"></a><span data-ttu-id="99152-276">ページの URL の生成</span><span class="sxs-lookup"><span data-stu-id="99152-276">URL generation for Pages</span></span>

<span data-ttu-id="99152-277">上に示した `Create` ページでは、`RedirectToPage` を使用します。</span><span class="sxs-lookup"><span data-stu-id="99152-277">The `Create` page, shown previously, uses `RedirectToPage`:</span></span>

[!code-cs[](index/sample/RazorPagesContacts/Pages/Create.cshtml.cs?name=snippet_OnPostAsync&highlight=10)]

<span data-ttu-id="99152-278">アプリには次のファイル/フォルダー構造があります。</span><span class="sxs-lookup"><span data-stu-id="99152-278">The app has the following file/folder structure:</span></span>

* <span data-ttu-id="99152-279">*/Pages*</span><span class="sxs-lookup"><span data-stu-id="99152-279">*/Pages*</span></span>

  * <span data-ttu-id="99152-280">*Index.cshtml*</span><span class="sxs-lookup"><span data-stu-id="99152-280">*Index.cshtml*</span></span>
  * <span data-ttu-id="99152-281">*/Customers*</span><span class="sxs-lookup"><span data-stu-id="99152-281">*/Customers*</span></span>

    * <span data-ttu-id="99152-282">*Create.cshtml*</span><span class="sxs-lookup"><span data-stu-id="99152-282">*Create.cshtml*</span></span>
    * <span data-ttu-id="99152-283">*Edit.cshtml*</span><span class="sxs-lookup"><span data-stu-id="99152-283">*Edit.cshtml*</span></span>
    * <span data-ttu-id="99152-284">*Index.cshtml*</span><span class="sxs-lookup"><span data-stu-id="99152-284">*Index.cshtml*</span></span>

<span data-ttu-id="99152-285">成功すると、*Pages/Customers/Create.cshtml* ページと *Pages/Customers/Edit.cshtml* ページが *Pages/Index.cshtml* にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="99152-285">The *Pages/Customers/Create.cshtml* and *Pages/Customers/Edit.cshtml* pages redirect to *Pages/Index.cshtml* after success.</span></span> <span data-ttu-id="99152-286">文字列 `/Index` は前のページにアクセスするための URI の一部です。</span><span class="sxs-lookup"><span data-stu-id="99152-286">The string `/Index` is part of the URI to access the preceding page.</span></span> <span data-ttu-id="99152-287">文字列 `/Index` は、*Pages/Index.cshtml* ページへの URI を生成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="99152-287">The string `/Index` can be used to generate URIs to the *Pages/Index.cshtml* page.</span></span> <span data-ttu-id="99152-288">例:</span><span class="sxs-lookup"><span data-stu-id="99152-288">For example:</span></span>

* `Url.Page("/Index", ...)`
* `<a asp-page="/Index">My Index Page</a>`
* `RedirectToPage("/Index")`

<span data-ttu-id="99152-289">ページ名は、先頭の `/` を含む、ルート */Pages* フォルダーからページへのパスです (たとえば `/Index`)。</span><span class="sxs-lookup"><span data-stu-id="99152-289">The page name is the path to the page from the root */Pages* folder including a leading `/` (for example, `/Index`).</span></span> <span data-ttu-id="99152-290">先述の URL 生成サンプルでは、URL のハードコーディングに関する拡張オプションと機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="99152-290">The preceding URL generation samples offer enhanced options and functional capabilities over hardcoding a URL.</span></span> <span data-ttu-id="99152-291">URL の生成は[ルーティング](xref:mvc/controllers/routing)を使用し、ターゲット パスで定義されたルート方法に従って、パラメーターの生成とエンコードができます。</span><span class="sxs-lookup"><span data-stu-id="99152-291">URL generation uses [routing](xref:mvc/controllers/routing) and can generate and encode parameters according to how the route is defined in the destination path.</span></span>

<span data-ttu-id="99152-292">ページの URL 生成は、相対名をサポートします。</span><span class="sxs-lookup"><span data-stu-id="99152-292">URL generation for pages supports relative names.</span></span> <span data-ttu-id="99152-293">次の表に、*Pages/Customers/Create.cshtml* の異なる `RedirectToPage` パラメーターで選択されたインデックス ページを示します。</span><span class="sxs-lookup"><span data-stu-id="99152-293">The following table shows which Index page is selected with different `RedirectToPage` parameters from *Pages/Customers/Create.cshtml*:</span></span>

| <span data-ttu-id="99152-294">RedirectToPage(x)</span><span class="sxs-lookup"><span data-stu-id="99152-294">RedirectToPage(x)</span></span>| <span data-ttu-id="99152-295">ページ</span><span class="sxs-lookup"><span data-stu-id="99152-295">Page</span></span> |
| ----------------- | ------------ |
| <span data-ttu-id="99152-296">RedirectToPage("/Index")</span><span class="sxs-lookup"><span data-stu-id="99152-296">RedirectToPage("/Index")</span></span> | <span data-ttu-id="99152-297">*Pages/Index*</span><span class="sxs-lookup"><span data-stu-id="99152-297">*Pages/Index*</span></span> |
| <span data-ttu-id="99152-298">RedirectToPage("./Index");</span><span class="sxs-lookup"><span data-stu-id="99152-298">RedirectToPage("./Index");</span></span> | <span data-ttu-id="99152-299">*Pages/Customers/Index*</span><span class="sxs-lookup"><span data-stu-id="99152-299">*Pages/Customers/Index*</span></span> |
| <span data-ttu-id="99152-300">RedirectToPage("../Index")</span><span class="sxs-lookup"><span data-stu-id="99152-300">RedirectToPage("../Index")</span></span> | <span data-ttu-id="99152-301">*Pages/Index*</span><span class="sxs-lookup"><span data-stu-id="99152-301">*Pages/Index*</span></span> |
| <span data-ttu-id="99152-302">RedirectToPage("Index")</span><span class="sxs-lookup"><span data-stu-id="99152-302">RedirectToPage("Index")</span></span>  | <span data-ttu-id="99152-303">*Pages/Customers/Index*</span><span class="sxs-lookup"><span data-stu-id="99152-303">*Pages/Customers/Index*</span></span> |

<span data-ttu-id="99152-304">`RedirectToPage("Index")`、`RedirectToPage("./Index")`、および `RedirectToPage("../Index")` は<em>相対名</em>です。</span><span class="sxs-lookup"><span data-stu-id="99152-304">`RedirectToPage("Index")`, `RedirectToPage("./Index")`, and `RedirectToPage("../Index")`  are <em>relative names</em>.</span></span> <span data-ttu-id="99152-305">`RedirectToPage` パラメーターは現在のページのパスと<em>組み合わされて</em>、ターゲット ページの名前を計算します。</span><span class="sxs-lookup"><span data-stu-id="99152-305">The `RedirectToPage` parameter is <em>combined</em> with the path of the current page to compute the name of the destination page.</span></span>  <!-- Review: Original had The provided string is combined with the page name of the current page to compute the name of the destination page.  page name, not page path -->

<span data-ttu-id="99152-306">相対名のリンクは、複雑な構造を持つサイトを構築する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="99152-306">Relative name linking is useful when building sites with a complex structure.</span></span> <span data-ttu-id="99152-307">相対名を使用してフォルダー内のページ間をリンクする場合、そのフォルダー名を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="99152-307">If you use relative names to link between pages in a folder, you can rename that folder.</span></span> <span data-ttu-id="99152-308">すべてのリンクは引き続き機能します (リンクにはフォルダー名が含まれていないため)。</span><span class="sxs-lookup"><span data-stu-id="99152-308">All the links still work (because they didn't include the folder name).</span></span>

::: moniker range=">= aspnetcore-2.1"
## <a name="viewdata-attribute"></a><span data-ttu-id="99152-309">ViewData 属性</span><span class="sxs-lookup"><span data-stu-id="99152-309">ViewData attribute</span></span>

<span data-ttu-id="99152-310">データは [ViewDataAttribute](/dotnet/api/microsoft.aspnetcore.mvc.viewdataattribute) とのページに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="99152-310">Data can be passed to a page with [ViewDataAttribute](/dotnet/api/microsoft.aspnetcore.mvc.viewdataattribute).</span></span> <span data-ttu-id="99152-311">コントローラーまたは `[ViewData]` で装飾された Razor ページのモデルのプロパティは、値を [ViewDataDictionary](/dotnet/api/microsoft.aspnetcore.mvc.viewfeatures.viewdatadictionary) に格納し、読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="99152-311">Properties on controllers or Razor Page models decorated with `[ViewData]` have their values stored and loaded from the [ViewDataDictionary](/dotnet/api/microsoft.aspnetcore.mvc.viewfeatures.viewdatadictionary).</span></span>

<span data-ttu-id="99152-312">次の例では、`AboutModel` には `[ViewData]` で装飾された `Title` プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="99152-312">In the following example, the `AboutModel` contains a `Title` property decorated with `[ViewData]`.</span></span> <span data-ttu-id="99152-313">`Title` プロパティは、[About] ページのタイトルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="99152-313">The `Title` property is set to the title of the About page:</span></span>

```csharp
public class AboutModel : PageModel
{
    [ViewData]
    public string Title { get; } = "About";

    public void OnGet()
    {
    }
}
```

<span data-ttu-id="99152-314">[About] ページでは、モデル プロパティとして `Title` プロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="99152-314">In the About page, access the `Title` property as a model property:</span></span>

```cshtml
<h1>@Model.Title</h1>
```

<span data-ttu-id="99152-315">レイアウトでは、タイトルは ViewData ディクショナリから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="99152-315">In the layout, the title is read from the ViewData dictionary:</span></span>

```cshtml
<!DOCTYPE html>
<html lang="en">
<head>
    <title>@ViewData["Title"] - WebApplication</title>
    ...
```
::: moniker-end

## <a name="tempdata"></a><span data-ttu-id="99152-316">TempData</span><span class="sxs-lookup"><span data-stu-id="99152-316">TempData</span></span>

<span data-ttu-id="99152-317">ASP.NET Core は [コントローラー](/dotnet/api/microsoft.aspnetcore.mvc.controller)上で [TempData](/dotnet/api/microsoft.aspnetcore.mvc.controller.tempdata?view=aspnetcore-2.0#Microsoft_AspNetCore_Mvc_Controller_TempData) プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="99152-317">ASP.NET Core exposes the [TempData](/dotnet/api/microsoft.aspnetcore.mvc.controller.tempdata?view=aspnetcore-2.0#Microsoft_AspNetCore_Mvc_Controller_TempData) property on a [controller](/dotnet/api/microsoft.aspnetcore.mvc.controller).</span></span> <span data-ttu-id="99152-318">このプロパティは、読み取られるまでデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="99152-318">This property stores data until it's read.</span></span> <span data-ttu-id="99152-319">`Keep` メソッドと `Peek` メソッドは、削除せずにデータを確認するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="99152-319">The `Keep` and `Peek` methods can be used to examine the data without deletion.</span></span> <span data-ttu-id="99152-320">`TempData` は、複数の要求にデータが必要な場合のリダイレクトに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="99152-320">`TempData` is  useful for redirection, when data is needed for more than a single request.</span></span>

<span data-ttu-id="99152-321">`[TempData]` は ASP.NET Core 2.0 の新しい属性で、コントローラーとページでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="99152-321">The `[TempData]` attribute is new in ASP.NET Core 2.0 and is supported on controllers and pages.</span></span>

<span data-ttu-id="99152-322">次のコードは、`TempData` を使用して `Message` の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="99152-322">The following code sets the value of `Message` using `TempData`:</span></span>

[!code-cs[](index/sample/RazorPagesContacts2/Pages/Customers/CreateDot.cshtml.cs?highlight=10-11,25&name=snippet_Temp)]

<span data-ttu-id="99152-323">*Pages/Customers/Index.cshtml* ファイル内の次のマークアップは、`TempData` を使用して `Message` の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="99152-323">The following markup in the *Pages/Customers/Index.cshtml* file displays the value of `Message` using `TempData`.</span></span>

```cshtml
<h3>Msg: @Model.Message</h3>
```

<span data-ttu-id="99152-324">*Pages/Customers/Index.cshtml.cs* ページは、`[TempData]` 属性を `Message` プロパティに適用します。</span><span class="sxs-lookup"><span data-stu-id="99152-324">The *Pages/Customers/Index.cshtml.cs* page model applies the `[TempData]` attribute to the `Message` property.</span></span>

```cs
[TempData]
public string Message { get; set; }
```

<span data-ttu-id="99152-325">詳細については、「[TempData](xref:fundamentals/app-state#tempdata)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99152-325">See [TempData](xref:fundamentals/app-state#tempdata) for more information.</span></span>

<a name="mhpp"></a>
## <a name="multiple-handlers-per-page"></a><span data-ttu-id="99152-326">ページあたり複数のハンドラー</span><span class="sxs-lookup"><span data-stu-id="99152-326">Multiple handlers per page</span></span>

<span data-ttu-id="99152-327">次のページは、`asp-page-handler` タグ ヘルパーを使用して 2 つのページ ハンドラーにマークアップを生成します。</span><span class="sxs-lookup"><span data-stu-id="99152-327">The following page generates markup for two page handlers using the `asp-page-handler` Tag Helper:</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts2/Pages/Customers/CreateFATH.cshtml?highlight=12-13)]

<!-- Review: the FormActionTagHelper applies to all <form /> elements on a Razor page, even when there's no `asp-` attribute   -->

<span data-ttu-id="99152-328">前の例のフォームには、それぞれが `FormActionTagHelper` を使用して異なる URL に送信する 2 つの送信ボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="99152-328">The form in the preceding example has two submit buttons, each using the `FormActionTagHelper` to submit to a different URL.</span></span> <span data-ttu-id="99152-329">`asp-page-handler` 属性は、`asp-page` のコンパニオンです。</span><span class="sxs-lookup"><span data-stu-id="99152-329">The `asp-page-handler` attribute is a companion to `asp-page`.</span></span> <span data-ttu-id="99152-330">`asp-page-handler` はページごとに定義されている各ハンドラー メソッドに送信する URL を生成します。</span><span class="sxs-lookup"><span data-stu-id="99152-330">`asp-page-handler` generates URLs that submit to each of the handler methods defined by a page.</span></span> <span data-ttu-id="99152-331">サンプルは現在のページにリンクしているため、`asp-page` は指定されません。</span><span class="sxs-lookup"><span data-stu-id="99152-331">`asp-page` isn't specified because the sample is linking to the current page.</span></span>

<span data-ttu-id="99152-332">ページ モデル: </span><span class="sxs-lookup"><span data-stu-id="99152-332">The page model:</span></span>

[!code-cs[](index/sample/RazorPagesContacts2/Pages/Customers/CreateFATH.cshtml.cs?highlight=20,32)]

<span data-ttu-id="99152-333">上記のコードは、*名前付きハンドラー メソッド*を使用しています。</span><span class="sxs-lookup"><span data-stu-id="99152-333">The preceding code uses *named handler methods*.</span></span> <span data-ttu-id="99152-334">名前付きハンドラー メソッドは、名前の `On<HTTP Verb>` の後および `Async` の前 (ある場合) のテキストを取得して作成されます。</span><span class="sxs-lookup"><span data-stu-id="99152-334">Named handler methods are created by taking the text in the name after `On<HTTP Verb>` and before `Async` (if present).</span></span> <span data-ttu-id="99152-335">前の例では、ページ メソッドは OnPost**JoinList**Async と OnPost**JoinListUC**Async です。</span><span class="sxs-lookup"><span data-stu-id="99152-335">In the preceding example, the page methods are OnPost**JoinList**Async and OnPost**JoinListUC**Async.</span></span> <span data-ttu-id="99152-336">*OnPost* と *Async* を削除すると、ハンドラー名は `JoinList` と `JoinListUC` になります。</span><span class="sxs-lookup"><span data-stu-id="99152-336">With *OnPost* and *Async* removed, the handler names are `JoinList` and `JoinListUC`.</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts2/Pages/Customers/CreateFATH.cshtml?range=12-13)]

<span data-ttu-id="99152-337">上記のコードを使用すると、`OnPostJoinListAsync` に送信される URL パスは `http://localhost:5000/Customers/CreateFATH?handler=JoinList` になります。</span><span class="sxs-lookup"><span data-stu-id="99152-337">Using the preceding code, the URL path that submits to `OnPostJoinListAsync` is `http://localhost:5000/Customers/CreateFATH?handler=JoinList`.</span></span> <span data-ttu-id="99152-338">`OnPostJoinListUCAsync` に送信される URL パスは `http://localhost:5000/Customers/CreateFATH?handler=JoinListUC` です。</span><span class="sxs-lookup"><span data-stu-id="99152-338">The URL path that submits to `OnPostJoinListUCAsync` is `http://localhost:5000/Customers/CreateFATH?handler=JoinListUC`.</span></span>

## <a name="custom-routes"></a><span data-ttu-id="99152-339">カスタム ルート</span><span class="sxs-lookup"><span data-stu-id="99152-339">Custom routes</span></span>

<span data-ttu-id="99152-340">`@page` ディレクティブを次に使用します: </span><span class="sxs-lookup"><span data-stu-id="99152-340">Use the `@page` directive to:</span></span>

* <span data-ttu-id="99152-341">カスタム ルートをページに指定します。</span><span class="sxs-lookup"><span data-stu-id="99152-341">Specify a custom route to a page.</span></span> <span data-ttu-id="99152-342">たとえば、[バージョン情報] ページへのルートを `@page "/Some/Other/Path"` を使用して `/Some/Other/Path` に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="99152-342">For example, the route to the About page can be set to `/Some/Other/Path` with `@page "/Some/Other/Path"`.</span></span>
* <span data-ttu-id="99152-343">ページの既定のルートにセグメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="99152-343">Append segments to a page's default route.</span></span> <span data-ttu-id="99152-344">たとえば、"item" セグメントを `@page "item"` を使用してページの既定のルートに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="99152-344">For example, an "item" segment can be added to a page's default route with `@page "item"`.</span></span>
* <span data-ttu-id="99152-345">ページの既定のルートにパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="99152-345">Append parameters to a page's default route.</span></span> <span data-ttu-id="99152-346">たとえば、`@page "{id}"` を含むページに ID パラメーター `id` を必須とすることができます。</span><span class="sxs-lookup"><span data-stu-id="99152-346">For example, an ID parameter, `id`, can be required for a page with `@page "{id}"`.</span></span>

<span data-ttu-id="99152-347">パスの先頭のチルダ (`~`) によって指定されたルートの相対パスがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="99152-347">A root-relative path designated by a tilde (`~`) at the beginning of the path is supported.</span></span> <span data-ttu-id="99152-348">たとえば、`@page "~/Some/Other/Path"` は `@page "/Some/Other/Path"` と同じです。</span><span class="sxs-lookup"><span data-stu-id="99152-348">For example, `@page "~/Some/Other/Path"` is the same as `@page "/Some/Other/Path"`.</span></span>

<span data-ttu-id="99152-349">ルート テンプレート `@page "{handler?}"` を指定することで、URL のクエリ文字列 `?handler=JoinList` をルート セグメント `/JoinList` に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="99152-349">You can change the query string `?handler=JoinList` in the URL to a route segment `/JoinList` by specifying the route template `@page "{handler?}"`.</span></span>

<span data-ttu-id="99152-350">URL 内のクエリ文字列 `?handler=JoinList` が気に入らない場合は、ルートを変更して URL のパス部分にハンドラー名を挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="99152-350">If you don't like the query string `?handler=JoinList` in the URL, you can change the route to put the handler name in the path portion of the URL.</span></span> <span data-ttu-id="99152-351">`@page` ディレクティブの後に二重引用符で囲んだルート テンプレートを追加して、ルートをカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="99152-351">You can customize the route by adding a route template enclosed in double quotes after the `@page` directive.</span></span>

[!code-cshtml[](index/sample/RazorPagesContacts2/Pages/Customers/CreateRoute.cshtml?highlight=1)]

<span data-ttu-id="99152-352">上記のコードを使用すると、`OnPostJoinListAsync` に送信される URL パスは `http://localhost:5000/Customers/CreateFATH/JoinList` になります。</span><span class="sxs-lookup"><span data-stu-id="99152-352">Using the preceding code, the URL path that submits to `OnPostJoinListAsync` is `http://localhost:5000/Customers/CreateFATH/JoinList`.</span></span> <span data-ttu-id="99152-353">`OnPostJoinListUCAsync` に送信される URL パスは `http://localhost:5000/Customers/CreateFATH/JoinListUC` です。</span><span class="sxs-lookup"><span data-stu-id="99152-353">The URL path that submits to `OnPostJoinListUCAsync` is `http://localhost:5000/Customers/CreateFATH/JoinListUC`.</span></span>

<span data-ttu-id="99152-354">`handler` の後の `?` は、ルート パラメーターが省略可能なことを意味します。</span><span class="sxs-lookup"><span data-stu-id="99152-354">The `?` following `handler` means the route parameter is optional.</span></span>

## <a name="configuration-and-settings"></a><span data-ttu-id="99152-355">構成と設定</span><span class="sxs-lookup"><span data-stu-id="99152-355">Configuration and settings</span></span>

<span data-ttu-id="99152-356">高度なオプションを構成するには、MVC ビルダーで拡張メソッド `AddRazorPagesOptions` を使用します。</span><span class="sxs-lookup"><span data-stu-id="99152-356">To configure advanced options, use the extension method `AddRazorPagesOptions` on the MVC builder:</span></span>

[!code-cs[](index/sample/RazorPagesContacts/StartupAdvanced.cs?name=snippet_1)]

<span data-ttu-id="99152-357">現在は、`RazorPagesOptions` を使用してページのルート ディレクトリを設定したり、ページのアプリケーション モデルの規則を追加したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="99152-357">Currently you can use the `RazorPagesOptions` to set the root directory for pages, or add application model conventions for pages.</span></span> <span data-ttu-id="99152-358">将来、この方法でより多くの機能拡張を可能にしたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="99152-358">We'll enable more extensibility this way in the future.</span></span>

<span data-ttu-id="99152-359">ビューをプリコンパイルするには、「[Razor view compilation](xref:mvc/views/view-compilation)」 (Razor ビュー コンパイル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99152-359">To precompile views, see [Razor view compilation](xref:mvc/views/view-compilation) .</span></span>

<span data-ttu-id="99152-360">[サンプル コードをダウンロードまたは表示します](https://github.com/aspnet/Docs/tree/master/aspnetcore/razor-pages/index/sample)。</span><span class="sxs-lookup"><span data-stu-id="99152-360">[Download or view sample code](https://github.com/aspnet/Docs/tree/master/aspnetcore/razor-pages/index/sample).</span></span>

<span data-ttu-id="99152-361">この概要に基づく、「[Razor ページの概要](xref:tutorials/razor-pages/razor-pages-start)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99152-361">See [Get started with Razor Pages](xref:tutorials/razor-pages/razor-pages-start), which builds on this introduction.</span></span>

### <a name="specify-that-razor-pages-are-at-the-content-root"></a><span data-ttu-id="99152-362">Razor ページをコンテンツのルートに指定する</span><span class="sxs-lookup"><span data-stu-id="99152-362">Specify that Razor Pages are at the content root</span></span>

<span data-ttu-id="99152-363">Razor ページのルートは既定で */Pages* ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="99152-363">By default, Razor Pages are rooted in the */Pages* directory.</span></span> <span data-ttu-id="99152-364">Razor ページをアプリのコンテンツ ルート ([ContentRootPath](/dotnet/api/microsoft.aspnetcore.hosting.ihostingenvironment.contentrootpath)) に指定するには、[WithRazorPagesAtContentRoot](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.withrazorpagesatcontentroot) を [AddMvc](/dotnet/api/microsoft.extensions.dependencyinjection.mvcservicecollectionextensions.addmvc#Microsoft_Extensions_DependencyInjection_MvcServiceCollectionExtensions_AddMvc_Microsoft_Extensions_DependencyInjection_IServiceCollection_) に追加します。</span><span class="sxs-lookup"><span data-stu-id="99152-364">Add [WithRazorPagesAtContentRoot](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvcbuilderextensions.withrazorpagesatcontentroot) to [AddMvc](/dotnet/api/microsoft.extensions.dependencyinjection.mvcservicecollectionextensions.addmvc#Microsoft_Extensions_DependencyInjection_MvcServiceCollectionExtensions_AddMvc_Microsoft_Extensions_DependencyInjection_IServiceCollection_) to specify that your Razor Pages are at the content root ([ContentRootPath](/dotnet/api/microsoft.aspnetcore.hosting.ihostingenvironment.contentrootpath)) of the app:</span></span>

```csharp
services.AddMvc()
    .AddRazorPagesOptions(options =>
    {
        ...
    })
    .WithRazorPagesAtContentRoot();
```

### <a name="specify-that-razor-pages-are-at-a-custom-root-directory"></a><span data-ttu-id="99152-365">Razor ページをカスタム ルート ディレクトリに指定する</span><span class="sxs-lookup"><span data-stu-id="99152-365">Specify that Razor Pages are at a custom root directory</span></span>

<span data-ttu-id="99152-366">(相対パスを指定して) Razor ページをアプリのカスタム ルート ディレクトリに指定するには、[WithRazorPagesRoot](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvccorebuilderextensions.withrazorpagesroot) を [AddMvc](/dotnet/api/microsoft.extensions.dependencyinjection.mvcservicecollectionextensions.addmvc#Microsoft_Extensions_DependencyInjection_MvcServiceCollectionExtensions_AddMvc_Microsoft_Extensions_DependencyInjection_IServiceCollection_) に追加します。</span><span class="sxs-lookup"><span data-stu-id="99152-366">Add [WithRazorPagesRoot](/dotnet/api/microsoft.extensions.dependencyinjection.mvcrazorpagesmvccorebuilderextensions.withrazorpagesroot) to [AddMvc](/dotnet/api/microsoft.extensions.dependencyinjection.mvcservicecollectionextensions.addmvc#Microsoft_Extensions_DependencyInjection_MvcServiceCollectionExtensions_AddMvc_Microsoft_Extensions_DependencyInjection_IServiceCollection_) to specify that your Razor Pages are at a custom root directory in the app (provide a relative path):</span></span>

```csharp
services.AddMvc()
    .AddRazorPagesOptions(options =>
    {
        ...
    })
    .WithRazorPagesRoot("/path/to/razor/pages");
```

## <a name="see-also"></a><span data-ttu-id="99152-367">関連項目</span><span class="sxs-lookup"><span data-stu-id="99152-367">See also</span></span>

* [<span data-ttu-id="99152-368">ASP.NET Core の概要</span><span class="sxs-lookup"><span data-stu-id="99152-368">Introduction to ASP.NET Core</span></span>](xref:index)
* [<span data-ttu-id="99152-369">Razor の構文</span><span class="sxs-lookup"><span data-stu-id="99152-369">Razor syntax</span></span>](xref:mvc/views/razor)
* [<span data-ttu-id="99152-370">Razor ページの概要</span><span class="sxs-lookup"><span data-stu-id="99152-370">Get started with Razor Pages</span></span>](xref:tutorials/razor-pages/razor-pages-start)
* [<span data-ttu-id="99152-371">Razor ページの承認規則</span><span class="sxs-lookup"><span data-stu-id="99152-371">Razor Pages authorization conventions</span></span>](xref:security/authorization/razor-pages-authorization)
* [<span data-ttu-id="99152-372">Razor ページのカスタム ルートとページ モデル プロバイダー</span><span class="sxs-lookup"><span data-stu-id="99152-372">Razor Pages custom route and page model providers</span></span>](xref:razor-pages/razor-pages-conventions)
* [<span data-ttu-id="99152-373">Razor ページの単体テスト</span><span class="sxs-lookup"><span data-stu-id="99152-373">Razor Pages unit tests</span></span>](xref:test/razor-pages-tests)