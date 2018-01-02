---
uid: web-forms/overview/ajax-control-toolkit/confirmbutton/using-a-confirmbutton-in-a-repeater-vb
title: "リピータ (VB) で、ConfirmButton の使用 |Microsoft ドキュメント"
author: wenz
description: "AJAX コントロールのツールキットで ConfirmButton extender は、[はい] を作成、ユーザーがボタンをクリックするとポップアップも含め LinkButton コントロール)/です。 場合にのみが [はい] がしています."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: 18c31709-3f9d-4d93-8b01-f1356bf610b4
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/confirmbutton/using-a-confirmbutton-in-a-repeater-vb
msc.type: authoredcontent
ms.openlocfilehash: 5da8491c157ad6f35c2c25803680f262a35ce6e1
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2017
---
<a name="using-a-confirmbutton-in-a-repeater-vb"></a><span data-ttu-id="c7561-104">リピータ (VB) で、ConfirmButton の使用</span><span class="sxs-lookup"><span data-stu-id="c7561-104">Using a ConfirmButton In a Repeater (VB)</span></span>
====================
<span data-ttu-id="c7561-105">によって[Christian Wenz](https://github.com/wenz)</span><span class="sxs-lookup"><span data-stu-id="c7561-105">by [Christian Wenz](https://github.com/wenz)</span></span>

<span data-ttu-id="c7561-106">[コードをダウンロードする](http://download.microsoft.com/download/8/6/d/86dea6c6-bb92-4fa6-aa14-f8c0f82100f5/ConfirmButton1.vb.zip)または[PDF のダウンロード](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/confirmbutton1VB.pdf)</span><span class="sxs-lookup"><span data-stu-id="c7561-106">[Download Code](http://download.microsoft.com/download/8/6/d/86dea6c6-bb92-4fa6-aa14-f8c0f82100f5/ConfirmButton1.vb.zip) or [Download PDF](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/confirmbutton1VB.pdf)</span></span>

> <span data-ttu-id="c7561-107">AJAX コントロールのツールキットで ConfirmButton extender は、[はい] を作成、ユーザーがボタンをクリックするとポップアップも含め LinkButton コントロール)/です。</span><span class="sxs-lookup"><span data-stu-id="c7561-107">The ConfirmButton extender in the AJAX Control Toolkit creates a Yes/No popup when the user clicks on a button (including LinkButton control).</span></span> <span data-ttu-id="c7561-108">のみ [はい] をクリックしたボタンの操作が実行、それ以外の場合はキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="c7561-108">Only if Yes is clicked, the button's action is executed, otherwise cancelled.</span></span> <span data-ttu-id="c7561-109">リピータでこれもできます。</span><span class="sxs-lookup"><span data-stu-id="c7561-109">This is also possible in a repeater.</span></span>


## <a name="overview"></a><span data-ttu-id="c7561-110">概要</span><span class="sxs-lookup"><span data-stu-id="c7561-110">Overview</span></span>

<span data-ttu-id="c7561-111">AJAX コントロールのツールキットで ConfirmButton extender は、[はい] を作成、ユーザーがボタンをクリックするとポップアップも含め LinkButton コントロール)/です。</span><span class="sxs-lookup"><span data-stu-id="c7561-111">The ConfirmButton extender in the AJAX Control Toolkit creates a Yes/No popup when the user clicks on a button (including LinkButton control).</span></span> <span data-ttu-id="c7561-112">のみ [はい] をクリックしたボタンの操作が実行、それ以外の場合はキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="c7561-112">Only if Yes is clicked, the button's action is executed, otherwise cancelled.</span></span> <span data-ttu-id="c7561-113">リピータでこれもできます。</span><span class="sxs-lookup"><span data-stu-id="c7561-113">This is also possible in a repeater.</span></span>

## <a name="steps"></a><span data-ttu-id="c7561-114">手順</span><span class="sxs-lookup"><span data-stu-id="c7561-114">Steps</span></span>

<span data-ttu-id="c7561-115">まず、データ ソースが必要です。</span><span class="sxs-lookup"><span data-stu-id="c7561-115">First of all, a data source is required.</span></span> <span data-ttu-id="c7561-116">このサンプルでは、AdventureWorks データベースと、Microsoft SQL Server 2005 Express Edition を使用します。</span><span class="sxs-lookup"><span data-stu-id="c7561-116">This sample uses the AdventureWorks database and the Microsoft SQL Server 2005 Express Edition.</span></span> <span data-ttu-id="c7561-117">データベース (express エディションを含む)、Visual Studio のインストールのオプションの一部であるし、下にある個別のダウンロードとしても利用[https://go.microsoft.com/fwlink/?LinkId=64064](https://go.microsoft.com/fwlink/?LinkId=64064)です。</span><span class="sxs-lookup"><span data-stu-id="c7561-117">The database is an optional part of a Visual Studio installation (including express edition) and is also available as a separate download under [https://go.microsoft.com/fwlink/?LinkId=64064](https://go.microsoft.com/fwlink/?LinkId=64064).</span></span> <span data-ttu-id="c7561-118">AdventureWorks データベースが SQL Server 2005 サンプルとサンプル データベースの一部 (でダウンロード[https://www.microsoft.com/downloads/details.aspx?FamilyID=e719ecf7-9f46-4312-af89-6ad8702e4e6e&amp;DisplayLang = en](https://www.microsoft.com/downloads/details.aspx?FamilyID=e719ecf7-9f46-4312-af89-6ad8702e4e6e&amp;DisplayLang=en))。</span><span class="sxs-lookup"><span data-stu-id="c7561-118">The AdventureWorks database is part of the SQL Server 2005 Samples and Sample Databases (download at [https://www.microsoft.com/downloads/details.aspx?FamilyID=e719ecf7-9f46-4312-af89-6ad8702e4e6e&amp;DisplayLang=en](https://www.microsoft.com/downloads/details.aspx?FamilyID=e719ecf7-9f46-4312-af89-6ad8702e4e6e&amp;DisplayLang=en)).</span></span> <span data-ttu-id="c7561-119">データベースをセットアップする最も簡単な方法は、Microsoft SQL Server Management Studio Express を使用する ([https://www.microsoft.com/downloads/details.aspx?表示 = c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang = en](https://www.microsoft.com/downloads/details.aspx?FamilyID=c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang=en)) をアタッチし、`AdventureWorks.mdf`データベース ファイル。</span><span class="sxs-lookup"><span data-stu-id="c7561-119">The easiest way to set the database up is to use the Microsoft SQL Server Management Studio Express ([https://www.microsoft.com/downloads/details.aspx?FamilyID=c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang=en](https://www.microsoft.com/downloads/details.aspx?FamilyID=c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang=en)) and attach the `AdventureWorks.mdf` database file.</span></span>

<span data-ttu-id="c7561-120">このサンプルのものと、SQL Server 2005 Express Edition のインスタンスが呼び出される`SQLEXPRESS`web サーバーと同じコンピューター上に存在し、これは既定の設定にもします。</span><span class="sxs-lookup"><span data-stu-id="c7561-120">For this sample, we assume that the instance of the SQL Server 2005 Express Edition is called `SQLEXPRESS` and resides on the same machine as the web server; this is also the default setup.</span></span> <span data-ttu-id="c7561-121">セットアップが異なっている場合は、データベースの接続情報を調整する必要です。</span><span class="sxs-lookup"><span data-stu-id="c7561-121">If your setup differs, you have to adapt the connection information for the database.</span></span>

<span data-ttu-id="c7561-122">ASP.NET AJAX とコントロール Toolkit の機能をアクティブ化するために、`ScriptManager`コントロールを任意の場所 ページで配置する必要があります (ただし内、`<form>`要素)。</span><span class="sxs-lookup"><span data-stu-id="c7561-122">In order to activate the functionality of ASP.NET AJAX and the Control Toolkit, the `ScriptManager` control must be put anywhere on the page (but within the `<form>` element):</span></span>

[!code-aspx[Main](using-a-confirmbutton-in-a-repeater-vb/samples/sample1.aspx)]

<span data-ttu-id="c7561-123">次に、データ ソースが必要です。</span><span class="sxs-lookup"><span data-stu-id="c7561-123">Then, a data source is required.</span></span> <span data-ttu-id="c7561-124">わかりやすくするために、AdventureWorks の仕入先のテーブルの最初の 5 つのエントリのみが取得されます。</span><span class="sxs-lookup"><span data-stu-id="c7561-124">For the sake of simplicity, only the first five entries in AdventureWorks' Vendors table are retrieved.</span></span> <span data-ttu-id="c7561-125">Visual Studio のウィザードを使用して、データ ソースにテーブル名を作成するときに注意してください (`Vendors`) は、現在正しくプレフィックスが付いていない`Purchasing`です。</span><span class="sxs-lookup"><span data-stu-id="c7561-125">Note that when using the Visual Studio wizard to create the data source, the table name (`Vendors`) is currently not correctly prefixed with `Purchasing`.</span></span> <span data-ttu-id="c7561-126">次のマークアップでは、正しいの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="c7561-126">The following markup is the correct one:</span></span>

[!code-aspx[Main](using-a-confirmbutton-in-a-repeater-vb/samples/sample2.aspx)]

<span data-ttu-id="c7561-127">このデータ ソースは、リピータ内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c7561-127">This data source can then be used within a repeater.</span></span> <span data-ttu-id="c7561-128">通常どおり、`DataBinder.Eval()`メソッドは、データ ソースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="c7561-128">As usual, the `DataBinder.Eval()` method retrieves data from the data source.</span></span> <span data-ttu-id="c7561-129">`ConfirmButtonExtender`内でコントロールを配置し、必要があります、`<ItemTemplate>`データ ソース内のすべてのエントリに対して表示されるように中継ぎ局のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="c7561-129">The `ConfirmButtonExtender` control must then be placed within the `<ItemTemplate>` section of the repeater so that it appears for every entry in the data source.</span></span>

[!code-aspx[Main](using-a-confirmbutton-in-a-repeater-vb/samples/sample3.aspx)]


<span data-ttu-id="c7561-130">[![データ ソースからの各エントリの横にある [確認] ボタンが表示されます。](using-a-confirmbutton-in-a-repeater-vb/_static/image2.png)](using-a-confirmbutton-in-a-repeater-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="c7561-130">[![The confirm button appears next to each entry from the data source](using-a-confirmbutton-in-a-repeater-vb/_static/image2.png)](using-a-confirmbutton-in-a-repeater-vb/_static/image1.png)</span></span>

<span data-ttu-id="c7561-131">データ ソースからの各エントリの横にある [確認] ボタンが表示されます ([フルサイズのイメージを表示するをクリックして](using-a-confirmbutton-in-a-repeater-vb/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="c7561-131">The confirm button appears next to each entry from the data source ([Click to view full-size image](using-a-confirmbutton-in-a-repeater-vb/_static/image3.png))</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="c7561-132">前へ</span><span class="sxs-lookup"><span data-stu-id="c7561-132">Previous</span></span>](using-a-confirmbutton-in-a-repeater-cs.md)