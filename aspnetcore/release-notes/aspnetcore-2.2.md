---
title: ASP.NET Core 2.2 の新機能
author: tdykstra
description: ASP.NET Core 2.2 の新機能について説明します。
ms.author: tdykstra
ms.custom: mvc
ms.date: 12/03/2018
uid: aspnetcore-2.2
ms.openlocfilehash: d0bb0698526e2f7af8f0e99b0393f3ce48657b34
ms.sourcegitcommit: a3a15d3ad4d6e160a69614a29c03bbd50db110a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2018
ms.locfileid: "52952058"
---
# <a name="whats-new-in-aspnet-core-22"></a><span data-ttu-id="4abbc-103">ASP.NET Core 2.2 の新機能</span><span class="sxs-lookup"><span data-stu-id="4abbc-103">What's new in ASP.NET Core 2.2</span></span>

<span data-ttu-id="4abbc-104">この記事では、ASP.NET Core 2.2 の最も大きな変更点について説明します。また、その変更点のドキュメントへのリンクも示します。</span><span class="sxs-lookup"><span data-stu-id="4abbc-104">This article highlights the most significant changes in ASP.NET Core 2.2, with links to relevant documentation.</span></span>

## <a name="open-api-analyzers--conventions"></a><span data-ttu-id="4abbc-105">Open API のアナライザーと規則</span><span class="sxs-lookup"><span data-stu-id="4abbc-105">Open API Analyzers & Conventions</span></span>

<span data-ttu-id="4abbc-106">Open API (Swagger とも呼ばれます) は、REST API を記述するために、言語に関係なく使える仕様です。</span><span class="sxs-lookup"><span data-stu-id="4abbc-106">Open API (also known as Swagger) is a language-agnostic specification for describing REST APIs.</span></span> <span data-ttu-id="4abbc-107">Open API エコシステムには、この仕様を使用してクライアント コードの検出、テスト、および作成を行うことができるツールがあります。</span><span class="sxs-lookup"><span data-stu-id="4abbc-107">The Open API ecosystem has tools that allow for discovering, testing, and producing client code using the specification.</span></span> <span data-ttu-id="4abbc-108">ASP.NET Core MVC での Open API ドキュメントの生成と視覚化のサポートは、[NSwag](https://github.com/RSuter/NSwag)、[Swashbuckle.AspNetCore](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) などのコミュニティ主導のプロジェクトを介して提供されています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-108">Support for generating and visualizing Open API documents in ASP.NET Core MVC is provided via community driven projects such as [NSwag](https://github.com/RSuter/NSwag), and [Swashbuckle.AspNetCore](https://github.com/domaindrivendev/Swashbuckle.AspNetCore).</span></span> <span data-ttu-id="4abbc-109">ASP.NET Core 2.2 では、Open API ドキュメントを作成するためのツールとランタイム エクスペリエンスが改善されています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-109">ASP.NET Core 2.2 provides improved tooling and runtime experiences for creating Open API documents.</span></span>

<span data-ttu-id="4abbc-110">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-110">For more information, see the following resources:</span></span>

* <xref:web-api/advanced/analyzers>
* <xref:web-api/advanced/conventions>
* [<span data-ttu-id="4abbc-111">ASP.NET Core 2.2.0-preview1: Open API のアナライザーと規則</span><span class="sxs-lookup"><span data-stu-id="4abbc-111">ASP.NET Core 2.2.0-preview1: Open API Analyzers & Conventions</span></span>](https://blogs.msdn.microsoft.com/webdev/2018/08/23/asp-net-core-2-20-preview1-open-api-analyzers-conventions/)

## <a name="problem-details-support"></a><span data-ttu-id="4abbc-112">問題の詳細のサポート</span><span class="sxs-lookup"><span data-stu-id="4abbc-112">Problem details support</span></span>

<span data-ttu-id="4abbc-113">ASP.NET Core 2.1 では、HTTP 応答でエラーの詳細を伝達するための RFC 7807 仕様に基づいて `ProblemDetails` が導入されました。</span><span class="sxs-lookup"><span data-stu-id="4abbc-113">ASP.NET Core 2.1 introduced `ProblemDetails`, based on the RFC 7807 specification for carrying details of an error with an HTTP Response.</span></span> <span data-ttu-id="4abbc-114">2.2 で、`ProblemDetails` は、属性が `ApiControllerAttribute` のコントローラーのクライアント エラー コードに対する標準の応答です。</span><span class="sxs-lookup"><span data-stu-id="4abbc-114">In 2.2, `ProblemDetails` is the standard response for client error codes in controllers attributed with `ApiControllerAttribute`.</span></span> <span data-ttu-id="4abbc-115">クライアント エラー状態コード (4xx) を返している `IActionResult` は、`ProblemDetails` の本文を返すようになりました。</span><span class="sxs-lookup"><span data-stu-id="4abbc-115">An `IActionResult` returning a client error status code (4xx) now returns a `ProblemDetails` body.</span></span> <span data-ttu-id="4abbc-116">この結果には、要求ログを使用してエラーを関連付けるために使用できる相関関係 ID も含まれています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-116">The result also includes a correlation ID that can be used to correlate the error using request logs.</span></span> <span data-ttu-id="4abbc-117">クライアント エラーの場合、`ProducesResponseType` の既定では `ProblemDetails` が応答の種類として使用されます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-117">For client errors, `ProducesResponseType` defaults to using `ProblemDetails` as the response type.</span></span> <span data-ttu-id="4abbc-118">これは、NSwag または Swashbuckle.AspNetCore を使用して生成される Open API/Swagger 出力にドキュメント化されます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-118">This is documented in Open API / Swagger output generated using NSwag or Swashbuckle.AspNetCore.</span></span>

## <a name="endpoint-routing"></a><span data-ttu-id="4abbc-119">エンドポイント ルーティング</span><span class="sxs-lookup"><span data-stu-id="4abbc-119">Endpoint Routing</span></span>

<span data-ttu-id="4abbc-120">ASP.NET Core 2.2 では、要求のディスパッチを改善するために新しい*エンドポイント ルーティング* システムを使用しています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-120">ASP.NET Core 2.2 uses a new *endpoint routing* system for improved dispatching of requests.</span></span> <span data-ttu-id="4abbc-121">この変更には、新しいリンク生成 API メンバーとルート パラメーター変換機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-121">The changes include new link generation API members and route parameter transformers.</span></span>

<span data-ttu-id="4abbc-122">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-122">For more information, see the following resources:</span></span>

* [<span data-ttu-id="4abbc-123">2.2 のエンドポイント ルーティング</span><span class="sxs-lookup"><span data-stu-id="4abbc-123">Endpoint routing in 2.2</span></span>](https://blogs.msdn.microsoft.com/webdev/2018/08/27/asp-net-core-2-2-0-preview1-endpoint-routing/)
* <span data-ttu-id="4abbc-124">[ルート パラメーターの変換機能](https://www.hanselman.com/blog/ASPNETCore22ParameterTransformersForCleanURLGenerationAndSlugsInRazorPagesOrMVC.aspx) (**ルーティング**に関するセクションを参照してください)</span><span class="sxs-lookup"><span data-stu-id="4abbc-124">[Route parameter transformers](https://www.hanselman.com/blog/ASPNETCore22ParameterTransformersForCleanURLGenerationAndSlugsInRazorPagesOrMVC.aspx) (see **Routing** section)</span></span>
* [<span data-ttu-id="4abbc-125">IRouter ベースのルーティングとエンドポイントベースのルーティングの違い</span><span class="sxs-lookup"><span data-stu-id="4abbc-125">Differences between IRouter- and endpoint-based routing</span></span>](xref:fundamentals/routing?view=aspnetcore-2.2#differences-from-earlier-versions-of-routing)

## <a name="health-checks"></a><span data-ttu-id="4abbc-126">正常性チェック</span><span class="sxs-lookup"><span data-stu-id="4abbc-126">Health checks</span></span>

<span data-ttu-id="4abbc-127">新しい正常性チェック サービスを使用すると、Kubernetes などの正常性チェックが必要な環境で ASP.NET Core を簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-127">A new health checks service makes it easier to use ASP.NET Core in environments that require health checks, such as Kubernetes.</span></span> <span data-ttu-id="4abbc-128">正常性チェックには、ミドルウェアと、`IHealthCheck` の抽象化とサービスを定義する一連のライブラリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-128">Health checks includes middleware and a set of libraries that define an `IHealthCheck` abstraction and service.</span></span>

<span data-ttu-id="4abbc-129">正常性チェックは、システムが正常に要求に応答しているかどうかを迅速に判断するために、コンテナー オーケストレーターまたはロード バランサーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-129">Health checks are used by a container orchestrator or load balancer to quickly determine if a system is responding to requests normally.</span></span> <span data-ttu-id="4abbc-130">正常性に問題が確認された場合、コンテナー オーケストレーターは実行中の展開を停止したり、コンテナーを再起動したりします。</span><span class="sxs-lookup"><span data-stu-id="4abbc-130">A container orchestrator might respond to a failing health check by halting a rolling deployment or restarting a container.</span></span> <span data-ttu-id="4abbc-131">ロード バランサーは、正常性チェックに対して、障害が発生したサービスのインスタンスからトラフィックをルーティングすることで応答する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4abbc-131">A load balancer might respond to a health check by routing traffic away from the failing instance of the service.</span></span>

<span data-ttu-id="4abbc-132">正常性チェックは、監視システムから使用される HTTP エンドポイントとして、アプリケーションによって公開されています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-132">Health checks are exposed by an application as an HTTP endpoint used by monitoring systems.</span></span> <span data-ttu-id="4abbc-133">正常性チェックは、さまざまなリアルタイム監視シナリオや監視システムに合わせて構成できます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-133">Health checks can be configured for a variety of real-time monitoring scenarios and monitoring systems.</span></span> <span data-ttu-id="4abbc-134">正常性チェック サービスは、[BeatPulse プロジェクト](https://github.com/Xabaril/BeatPulse)と統合されています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-134">The health checks service integrates with the [BeatPulse project](https://github.com/Xabaril/BeatPulse).</span></span> <span data-ttu-id="4abbc-135">そのため、数多くの一般的なシステムや依存関係のチェックを簡単に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-135">which makes it easier to add checks for dozens of popular systems and dependencies.</span></span>

<span data-ttu-id="4abbc-136">詳細については、「[Health checks in ASP.NET Core](xref:host-and-deploy/health-checks)」(ASP.NET Core の正常性チェック) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-136">For more information, see [Health checks in ASP.NET Core](xref:host-and-deploy/health-checks).</span></span>

## <a name="http2-in-kestrel"></a><span data-ttu-id="4abbc-137">Kestrel の HTTP/2</span><span class="sxs-lookup"><span data-stu-id="4abbc-137">HTTP/2 in Kestrel</span></span>

<span data-ttu-id="4abbc-138">ASP.NET Core 2.2 では HTTP/2 のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="4abbc-138">ASP.NET Core 2.2 adds support for HTTP/2.</span></span> 

<span data-ttu-id="4abbc-139">HTTP/2 は HTTP プロトコルのメジャー リビジョンです。</span><span class="sxs-lookup"><span data-stu-id="4abbc-139">HTTP/2 is a major revision of the HTTP protocol.</span></span> <span data-ttu-id="4abbc-140">HTTP/2 の注目すべき機能として、ヘッダーの圧縮や、単一の接続での完全に多重化されたストリームのサポートなどがあります。</span><span class="sxs-lookup"><span data-stu-id="4abbc-140">Some of the notable features of HTTP/2 are support for header compression and fully multiplexed streams over a single connection.</span></span> <span data-ttu-id="4abbc-141">HTTP/2 は HTTP のセマンティクス (HTTP ヘッダー、メソッドなど) を維持していますが、このデータがフレーム化され、ネットワーク経由で送信される方法については、HTTP/1.x からの破壊的変更があります。</span><span class="sxs-lookup"><span data-stu-id="4abbc-141">While HTTP/2 preserves HTTP’s semantics (HTTP headers, methods, etc) it's a breaking change from HTTP/1.x on how this data is framed and sent over the wire.</span></span>

<span data-ttu-id="4abbc-142">フレーム化に関するこの変更の結果、サーバーとクライアントは、使用されているプロトコル バージョンのネゴシエートが必要になりました。</span><span class="sxs-lookup"><span data-stu-id="4abbc-142">As a consequence of this change in framing, servers and clients need to negotiate the protocol version used.</span></span> <span data-ttu-id="4abbc-143">アプリケーション層プロトコル ネゴシエーション (ALPN) は、TLS の拡張機能です。これにより、サーバーとクライアントは、TLS ハンドシェイクの一環として、使用されているプロトコル バージョンをネゴシエートすることができます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-143">Application-Layer Protocol Negotiation (ALPN) is a TLS extension that allows the server and client negotiate the protocol version used as part of their TLS handshake.</span></span> <span data-ttu-id="4abbc-144">プロトコルに関してサーバーとクライアント間に事前の情報を持たせることはできますが、すべての主要なブラウザーは、HTTP/2 接続を確立する唯一の方法として ALPN をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-144">While it is possible to have prior knowledge between the server and the client on the protocol, all major browsers support ALPN as the only way to establish an HTTP/2 connection.</span></span>

<span data-ttu-id="4abbc-145">詳細については、「[HTTP/2 のサポート](xref:fundamentals/servers/index?view=aspnetcore-2.2#http2-support)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-145">For more information, see [HTTP/2 support](xref:fundamentals/servers/index?view=aspnetcore-2.2#http2-support).</span></span>

## <a name="kestrel-configuration"></a><span data-ttu-id="4abbc-146">Kestrel の構成</span><span class="sxs-lookup"><span data-stu-id="4abbc-146">Kestrel configuration</span></span>

<span data-ttu-id="4abbc-147">以前のバージョンの ASP.NET Core では、`UseKestrel` を呼び出して Kestrel のオプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="4abbc-147">In earlier versions of ASP.NET Core, Kestrel options are configured by calling `UseKestrel`.</span></span> <span data-ttu-id="4abbc-148">2.2 で Kestrel のオプションを構成するには、ホスト ビルダー上で `ConfigureKestrel` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4abbc-148">In 2.2, Kestrel options are configured by calling `ConfigureKestrel` on the host builder.</span></span> <span data-ttu-id="4abbc-149">この変更により、インプロセス ホスティングの `IServer` の登録順に関する問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-149">This change resolves an issue with the order of `IServer` registrations for in-process hosting.</span></span> <span data-ttu-id="4abbc-150">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-150">For more information, see the following resources:</span></span>

* [<span data-ttu-id="4abbc-151">UseIIS の競合を軽減する</span><span class="sxs-lookup"><span data-stu-id="4abbc-151">Mitigate UseIIS conflict</span></span>](https://github.com/aspnet/KestrelHttpServer/issues/2760)
* [<span data-ttu-id="4abbc-152">ConfigureKestrel を使用して Kestrel サーバーのオプションを構成する</span><span class="sxs-lookup"><span data-stu-id="4abbc-152">Configure Kestrel server options with ConfigureKestrel</span></span>](xref:fundamentals/servers/kestrel?view=aspnetcore-2.2#how-to-use-kestrel-in-aspnet-core-apps)

## <a name="iis-in-process-hosting"></a><span data-ttu-id="4abbc-153">IIS のインプロセス ホスティング</span><span class="sxs-lookup"><span data-stu-id="4abbc-153">IIS in-process hosting</span></span>

<span data-ttu-id="4abbc-154">以前のバージョンの ASP.NET Core では、IIS はリバース プロキシとして機能しています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-154">In earlier versions of ASP.NET Core, IIS serves as a reverse proxy.</span></span> <span data-ttu-id="4abbc-155">2.2 では、ASP.NET Core モジュールで CoreCLR を起動し、IIS worker プロセス (*w3wp.exe*) 内でアプリをホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-155">In 2.2, the ASP.NET Core Module can boot the CoreCLR and host an app inside the IIS worker process (*w3wp.exe*).</span></span> <span data-ttu-id="4abbc-156">インプロセス ホスティングを IIS で実行すると、パフォーマンスと診断機能が向上します。</span><span class="sxs-lookup"><span data-stu-id="4abbc-156">In-process hosting provides performance and diagnostic gains when running with IIS.</span></span>

<span data-ttu-id="4abbc-157">詳細については、[IIS のインプロセス ホスティング](xref:fundamentals/servers/aspnet-core-module?view=aspnetcore-2.2#in-process-hosting-model)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-157">For more information, see [IIS in-process hosting](xref:fundamentals/servers/aspnet-core-module?view=aspnetcore-2.2#in-process-hosting-model).</span></span>

## <a name="signalr-java-client"></a><span data-ttu-id="4abbc-158">SignalR Java クライアント</span><span class="sxs-lookup"><span data-stu-id="4abbc-158">SignalR Java client</span></span>

<span data-ttu-id="4abbc-159">ASP.NET Core 2.2 には SignalR 用の Java クライアントが導入されました。</span><span class="sxs-lookup"><span data-stu-id="4abbc-159">ASP.NET Core 2.2 introduces a Java Client for SignalR.</span></span> <span data-ttu-id="4abbc-160">このクライアントは、Android アプリを含め、Java コードから ASP.NET Core SignalR サーバーへの接続をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-160">This client supports connecting to an ASP.NET Core SignalR Server from Java code, including Android apps.</span></span>

<span data-ttu-id="4abbc-161">詳細については、「[ASP.NET Core SignalR Java client](https://docs.microsoft.com/aspnet/core/signalr/java-client?view=aspnetcore-2.2)」(ASP.NET Core SignalR Java クライアント) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-161">For more information, see [ASP.NET Core SignalR Java client](https://docs.microsoft.com/aspnet/core/signalr/java-client?view=aspnetcore-2.2).</span></span>

## <a name="cors-improvements"></a><span data-ttu-id="4abbc-162">CORS の機能強化</span><span class="sxs-lookup"><span data-stu-id="4abbc-162">CORS improvements</span></span>

<span data-ttu-id="4abbc-163">以前のバージョンの ASP.NET Core では、`CorsPolicy.Headers` に構成されている値に関係なく、CORS ミドルウェアから `Accept`、`Accept-Language`、`Content-Language`、`Origin` ヘッダーを送信できます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-163">In earlier versions of ASP.NET Core, CORS Middleware allows `Accept`, `Accept-Language`, `Content-Language`, and `Origin` headers to be sent regardless of the values configured in `CorsPolicy.Headers`.</span></span> <span data-ttu-id="4abbc-164">2.2 では、CORS ミドルウェア ポリシーの一致は、`Access-Control-Request-Headers` で送信されたヘッダーが `WithHeaders` に示されているヘッダーと正確に一致する場合にのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="4abbc-164">In 2.2, a CORS Middleware policy match is only possible when the headers sent in `Access-Control-Request-Headers` exactly match the headers stated in `WithHeaders`.</span></span>

<span data-ttu-id="4abbc-165">詳細については、[CORS ミドルウェア](xref:security/cors?view=aspnetcore-2.2#set-the-allowed-request-headers)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-165">For more information, see [CORS Middleware](xref:security/cors?view=aspnetcore-2.2#set-the-allowed-request-headers).</span></span>

## <a name="response-compression"></a><span data-ttu-id="4abbc-166">応答圧縮</span><span class="sxs-lookup"><span data-stu-id="4abbc-166">Response compression</span></span>

<span data-ttu-id="4abbc-167">ASP.NET Core 2.2 は、[Brotli 圧縮形式](https://tools.ietf.org/html/rfc7932)で応答を圧縮できます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-167">ASP.NET Core 2.2 can compress responses with the [Brotli compression format](https://tools.ietf.org/html/rfc7932).</span></span>

<span data-ttu-id="4abbc-168">詳細については、[応答圧縮ミドルウェアによる Brotli 圧縮のサポート](xref:performance/response-compression?view=aspnetcore-2.2#brotli-compression-provider)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-168">For more information, see [Response Compression Middleware supports Brotli compression](xref:performance/response-compression?view=aspnetcore-2.2#brotli-compression-provider).</span></span>

## <a name="project-templates"></a><span data-ttu-id="4abbc-169">プロジェクト テンプレート</span><span class="sxs-lookup"><span data-stu-id="4abbc-169">Project templates</span></span>

<span data-ttu-id="4abbc-170">ASP.NET Core Web プロジェクト テンプレートは、[Bootstrap 4](https://getbootstrap.com/docs/4.1/migration/) と [Angular 6](https://blog.angular.io/version-6-of-angular-now-available-cc56b0efa7a4) に更新されました。</span><span class="sxs-lookup"><span data-stu-id="4abbc-170">ASP.NET Core web project templates were updated to [Bootstrap 4](https://getbootstrap.com/docs/4.1/migration/) and [Angular 6](https://blog.angular.io/version-6-of-angular-now-available-cc56b0efa7a4).</span></span> <span data-ttu-id="4abbc-171">新しい外観は視覚的にシンプルになり、アプリの重要な構造を簡単に把握できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4abbc-171">The new look is visually simpler and makes it easier to see the important structures of the app.</span></span>

![ホームまたはインデックス ページ](~/tutorials/razor-pages/razor-pages-start/_static/home2.2.png)

## <a name="validation-performance"></a><span data-ttu-id="4abbc-173">検証のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="4abbc-173">Validation performance</span></span>

<span data-ttu-id="4abbc-174">MVC の検証システムは、拡張性と柔軟性を考慮して設計されており、特定のモデルにどの検証コントロールが適用されるかを要求単位で判断することができます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-174">MVC’s validation system is designed to be extensible and flexible, allowing you to determine on a per request basis which validators apply to a given model.</span></span> <span data-ttu-id="4abbc-175">そのため、複雑な検証プロバイダーを作成する場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="4abbc-175">This is great for authoring complex validation providers.</span></span> <span data-ttu-id="4abbc-176">ただし、最も一般的なケースでは、アプリケーションは組み込みの検証コントロールのみを使用し、このような追加の柔軟性は不要です。</span><span class="sxs-lookup"><span data-stu-id="4abbc-176">However, in the most common case an application only uses the built-in validators and don’t require this extra flexibility.</span></span> <span data-ttu-id="4abbc-177">組み込みの検証コントロールには、[Required]、[StringLength] などの DataAnnotations や、`IValidatableObject` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4abbc-177">Built-in validators include DataAnnotations such as [Required] and [StringLength], and `IValidatableObject`.</span></span>

<span data-ttu-id="4abbc-178">ASP.NET Core 2.2 では、特定のモデル グラフに検証が不要と判断された場合、MVC で検証を省略することができます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-178">In ASP.NET Core 2.2, MVC can short-circuit validation if it determines that a given model graph doesn't require validation.</span></span> <span data-ttu-id="4abbc-179">検証をスキップすると、検証モデルに検証コントロールを含めることができない場合や含めない場合に大幅に改善されます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-179">Skipping validation results in significant improvements when validating models that can't or don't have any validators.</span></span> <span data-ttu-id="4abbc-180">これには、プリミティブ型のコレクション (`byte[]`、`string[]`、`Dictionary<string, string>` など) のオブジェクトや、多数の検証コントロールがない複雑なオブジェクト グラフが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4abbc-180">This includes objects such as collections of primitives (such as `byte[]`, `string[]`, `Dictionary<string, string>`), or complex object graphs without many validators.</span></span>

## <a name="http-client-performance"></a><span data-ttu-id="4abbc-181">HTTP クライアントのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="4abbc-181">HTTP Client performance</span></span>

<span data-ttu-id="4abbc-182">ASP.NET Core 2.2 では、接続プールのロック競合を減らすことで、`SocketsHttpHandler` のパフォーマンスが向上しました。</span><span class="sxs-lookup"><span data-stu-id="4abbc-182">In ASP.NET Core 2.2, the performance of `SocketsHttpHandler` was improved by reducing connection pool locking contention.</span></span> <span data-ttu-id="4abbc-183">一部のマイクロサービス アーキテクチャなど、多くの送信 HTTP 要求を作成するアプリの場合、スループットが向上します。</span><span class="sxs-lookup"><span data-stu-id="4abbc-183">For apps that make many outgoing HTTP requests, such as some microservices architectures, throughput is improved.</span></span> <span data-ttu-id="4abbc-184">読み込み時には、`HttpClient` のスループットが Linux では最大 60%、Windows では 20% 向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4abbc-184">Under load, `HttpClient` throughput can be improved by up to 60% on Linux and 20% on Windows.</span></span>

<span data-ttu-id="4abbc-185">詳細については、[このような改善を実現したプル要求](https://github.com/dotnet/corefx/pull/32568)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-185">For more information, see [the pull request that made this improvement](https://github.com/dotnet/corefx/pull/32568).</span></span>

## <a name="additional-information"></a><span data-ttu-id="4abbc-186">追加情報</span><span class="sxs-lookup"><span data-stu-id="4abbc-186">Additional information</span></span>

<span data-ttu-id="4abbc-187">変更の全一覧については、[ASP.NET Core 2.2 のリリース ノート](https://github.com/aspnet/Home/releases/tag/2.2.0)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abbc-187">For the complete list of changes, see the [ASP.NET Core 2.2 Release Notes](https://github.com/aspnet/Home/releases/tag/2.2.0).</span></span>