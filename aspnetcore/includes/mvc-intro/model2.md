---
ms.openlocfilehash: 82c0f3076e846045ca85697e150ff0ab9be75dba
ms.sourcegitcommit: 5f299daa7c8102d56a63b214b9a34cc4bc87bc42
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58214369"
---
<a name="dc"></a>

次の `MvcMovieContext` クラスを *Models* フォルダーに追加します。  

[!code-csharp[](~/tutorials/first-mvc-app/start-mvc/sample/MvcMovie22/Data/MvcMovieContext.cs)]

上記のコードによって、エンティティ セットの `DbSet` プロパティが作成されます。 Entity Framework の用語では、エンティティ セットは通常はデータベース テーブルに対応し、エンティティはテーブルの行に対応します。

<a name="cs"></a>

### <a name="add-a-database-connection-string"></a>データベース接続文字列の追加

*appsettings.json* ファイルに接続文字列を追加します。

[!code-json[](~/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie/appsettings_SQLite.json?highlight=8-10)]

### <a name="add-required-nuget-packages"></a>必要な NuGet パッケージの追加

次の .NET Core CLI コマンドを実行し、SQLite と CodeGeneration.Design をプロジェクトに追加します。

```console
dotnet add package Microsoft.EntityFrameworkCore.SQLite
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
```

スキャフォールディングには `Microsoft.VisualStudio.Web.CodeGeneration.Design` パッケージが必要です。

<a name="reg"></a>

### <a name="register-the-database-context"></a>データベース コンテキストの登録

*Startup.cs* の先頭に次の `using` ステートメントを追加します。

```csharp
using MvcMovie.Models;
using Microsoft.EntityFrameworkCore;
```

`Startup.ConfigureServices` で[依存性の挿入](xref:fundamentals/dependency-injection)コンテナーを使用し、データベース コンテキストを登録します。

[!code-csharp[](~/tutorials/first-mvc-app/start-mvc/sample/MvcMovie22/Startup.cs?name=snippet_UseSqlite&highlight=11-12)]

エラー チェックとしてプロジェクトをビルドします。