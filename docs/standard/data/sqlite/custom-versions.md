---
title: Niestandardowe wersje programu SQLite
ms.date: 12/13/2019
description: Dowiedz się, jak używać niestandardowej wersji natywnej biblioteki programu SQLite.
ms.openlocfilehash: dd27278c1dbe17b12e5067d04d19043bf259b1e8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746992"
---
# <a name="custom-sqlite-versions"></a>Niestandardowe wersje programu SQLite

Microsoft. Data. SQLite jest oparty na SQLitePCLRaw. Możesz użyć niestandardowych wersji natywnej biblioteki programu SQLite przy użyciu pakietu lub przez skonfigurowanie dostawcy SQLitePCLRaw.

## <a name="bundles"></a>Pakiety

Program SQLitePCLRaw udostępnia pakiety pakietów, które ułatwiają wprowadzanie odpowiednich zależności między różnymi platformami.

Główny pakiet Microsoft. Data. sqlite domyślnie znajduje się w SQLitePCLRaw. bundle_e_sqlite3.

Aby użyć innego pakietu, zainstaluj pakiet `Microsoft.Data.Sqlite.Core` zamiast niego wraz z pakietem pakietu, którego chcesz użyć. Pakiety są automatycznie inicjowane przez firmę Microsoft. Data. sqlite.

| Powiązane | Opis |
| --- | --- |
| SQLitePCLRaw. bundle_e_sqlite3 | Zapewnia spójną wersję oprogramowania SQLite na wszystkich platformach. Obejmuje rozszerzenia drzewa FTS4, FTS5, JSON1 i R *. Jest to domyślne ustawienie. |
| SQLitePCLRaw. bundle_green | Analogicznie jak bundle_e_sqlite3, z wyjątkiem systemu iOS, gdzie używa biblioteki oprogramowania SQLite. |
| SQLitePCLRaw. bundle_zetetic | Używa oficjalnych kompilacji SQLCIPHER z Zetetic (nieuwzględnione). |
| SQLitePCLRaw. bundle_winsqlite3 | Używa winsqlite3. dll, systemowej biblioteki oprogramowania SQLite w systemie Windows 10. |
| SQLitePCLRaw. bundle_e_sqlcipher | Zapewnia nieoficjalną kompilację SQLCIPHER typu open source. |

Na przykład, aby użyć nieoficjalnej kompilacji SQLCIPHER typu open source, użyj następujących poleceń.

### <a name="net-core-clitabnetcore-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a>Dostawcy SQLitePCLRaw

Możesz użyć własnej kompilacji oprogramowania SQLite, wykorzystując pakiet `SQLitePCLRaw.provider.dynamic_cdecl`. W takim przypadku użytkownik jest odpowiedzialny za wdrożenie biblioteki natywnej w aplikacji. Uwaga Szczegóły wdrażania bibliotek macierzystych w aplikacji różnią się w zależności od używanej platformy .NET i środowiska uruchomieniowego.

Najpierw musisz zaimplementować IGetFunctionPointer. Implementacja jest stosunkowo prosta w programie .NET Core.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

Następnie skonfiguruj dostawcę SQLitePCLRaw. Upewnij się, że w aplikacji jest używany program Microsoft. Data. sqlite. Należy również unikać używania pakietu pakietów SQLitePCLRaw, który może zastąpić dostawcę.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
