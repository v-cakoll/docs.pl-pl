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
# <a name="encryption"></a>Szyfrowanie

Program SQLite domyślnie nie obsługuje szyfrowania plików bazy danych. Zamiast tego należy użyć zmodyfikowanej wersji oprogramowania SQLite, takiego jak [See](https://www.hwaci.com/sw/sqlite/see.html), [SQLCIPHER](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)lub [wxSQLite3](https://utelle.github.io/wxsqlite3). W tym artykule pokazano, jak korzystać z nieobsługiwanej kompilacji SQLCIPHER typu open source, ale informacje dotyczą również innych rozwiązań, ponieważ zwykle są one zgodne z tym samym wzorcem.

## <a name="installation"></a>Instalacja programu

### <a name="net-core-clitabnetcore-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

Aby uzyskać więcej informacji na temat korzystania z innej biblioteki natywnej na potrzeby szyfrowania, zobacz [niestandardowe wersje oprogramowania SQLite](custom-versions.md).

## <a name="specify-the-key"></a>Określ klucz

Aby włączyć szyfrowanie, określ klucz za pomocą słowa kluczowego parametrów połączenia `Password`. Użyj <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder>, aby dodać lub zaktualizować wartość z danych wejściowych użytkownika i uniknąć ataków z iniekcją parametrów połączenia.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a>Ponowne tworzenie klucza bazy danych

Jeśli chcesz zmienić klucz szyfrowania bazy danych, wydaj instrukcję `PRAGMA rekey`. Aby odszyfrować bazę danych, określ `NULL`.

Niestety, program SQLite nie obsługuje parametrów w instrukcjach `PRAGMA`. Zamiast tego należy użyć funkcji `quote()`, aby zapobiec iniekcji kodu SQL.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
