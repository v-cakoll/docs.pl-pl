---
title: Szyfrowanie
ms.date: 12/13/2019
description: Dowiedz się, jak zaszyfrować plik bazy danych.
ms.openlocfilehash: ccdd4b6b8642b3cde1c2667c9ca432a9b0ef21f2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447266"
---
# <a name="encryption"></a><span data-ttu-id="b7526-103">Szyfrowanie</span><span class="sxs-lookup"><span data-stu-id="b7526-103">Encryption</span></span>

<span data-ttu-id="b7526-104">Program SQLite domyślnie nie obsługuje szyfrowania plików bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b7526-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="b7526-105">Zamiast tego należy użyć zmodyfikowanej wersji oprogramowania SQLite, takiego jak [See](https://www.hwaci.com/sw/sqlite/see.html), [SQLCIPHER](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)lub [wxSQLite3](https://utelle.github.io/wxsqlite3).</span><span class="sxs-lookup"><span data-stu-id="b7526-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="b7526-106">W tym artykule pokazano, jak korzystać z nieobsługiwanej kompilacji SQLCIPHER typu open source, ale informacje dotyczą również innych rozwiązań, ponieważ zwykle są one zgodne z tym samym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="b7526-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="b7526-107">Instalacja programu</span><span class="sxs-lookup"><span data-stu-id="b7526-107">Installation</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="b7526-108">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="b7526-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="b7526-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b7526-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="b7526-110">Aby uzyskać więcej informacji na temat korzystania z innej biblioteki natywnej na potrzeby szyfrowania, zobacz [niestandardowe wersje oprogramowania SQLite](custom-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b7526-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="b7526-111">Określ klucz</span><span class="sxs-lookup"><span data-stu-id="b7526-111">Specify the key</span></span>

<span data-ttu-id="b7526-112">Aby włączyć szyfrowanie, określ klucz za pomocą słowa kluczowego parametrów połączenia `Password`.</span><span class="sxs-lookup"><span data-stu-id="b7526-112">To enable encryption, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="b7526-113">Użyj <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder>, aby dodać lub zaktualizować wartość z danych wejściowych użytkownika i uniknąć ataków z iniekcją parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="b7526-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a><span data-ttu-id="b7526-114">Ponowne tworzenie klucza bazy danych</span><span class="sxs-lookup"><span data-stu-id="b7526-114">Rekeying the database</span></span>

<span data-ttu-id="b7526-115">Jeśli chcesz zmienić klucz szyfrowania bazy danych, wydaj instrukcję `PRAGMA rekey`.</span><span class="sxs-lookup"><span data-stu-id="b7526-115">If you want to change the encryption key of a database, issue a `PRAGMA rekey` statement.</span></span> <span data-ttu-id="b7526-116">Aby odszyfrować bazę danych, określ `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b7526-116">To decrypt the database, specify `NULL`.</span></span>

<span data-ttu-id="b7526-117">Niestety, program SQLite nie obsługuje parametrów w instrukcjach `PRAGMA`.</span><span class="sxs-lookup"><span data-stu-id="b7526-117">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="b7526-118">Zamiast tego należy użyć funkcji `quote()`, aby zapobiec iniekcji kodu SQL.</span><span class="sxs-lookup"><span data-stu-id="b7526-118">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
