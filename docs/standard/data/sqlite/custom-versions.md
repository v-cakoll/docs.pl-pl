---
title: Niestandardowe wersje programu SQLite
ms.date: 05/14/2020
description: Dowiedz się, jak używać niestandardowej wersji natywnej biblioteki programu SQLite.
ms.openlocfilehash: 15db10db26bc7c5017313ca020a0e1e528ba207a
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83440840"
---
# <a name="custom-sqlite-versions"></a>Niestandardowe wersje programu SQLite

`Microsoft.Data.Sqlite`jest zbudowany w oparciu o `SQLitePCLRaw` . Możesz użyć niestandardowych wersji natywnej biblioteki programu SQLite przy użyciu pakietu lub przez skonfigurowanie `SQLitePCLRaw` dostawcy.

## <a name="bundles"></a>Pakiety

`SQLitePCLRaw`zapewnia wygodną obsługę pakietów pakietu, dzięki czemu można łatwo korzystać z odpowiednich zależności na różnych platformach. Pakiet główny domyślnie jest przypisuje `Microsoft.Data.Sqlite` `SQLitePCLRaw.bundle_e_sqlite3` . Aby użyć innego pakietu, zainstaluj `Microsoft.Data.Sqlite.Core` pakiet wraz z pakietem pakietu, którego chcesz użyć. Pakiety są automatycznie inicjowane przez `Microsoft.Data.Sqlite` .

| Pakiet | Opis |
|--|--|
| [SQLitePCLRaw. bundle_e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | Zapewnia spójną wersję oprogramowania SQLite na wszystkich platformach. Obejmuje rozszerzenia drzewa FTS4, FTS5, JSON1 i R *. Domyślnie włączone. |
| [SQLitePCLRaw. bundle_e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | Zapewnia nieoficjalną kompilację typu open source `SQLCipher` . |
| [SQLitePCLRaw. bundle_green](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | Analogicznie jak `bundle_e_sqlite3` w przypadku systemu iOS, gdzie używa biblioteki oprogramowania SQLite. |
| [SQLitePCLRaw. bundle_winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | `winsqlite3.dll`Program używa biblioteki SQLite systemu w systemie Windows 10. |
| [SQLitePCLRaw. bundle_zetetic](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | Używa oficjalnych `SQLCipher` kompilacji z Zetetic (nieuwzględnione). |

Na przykład, aby użyć nieoficjalnej kompilacji typu "open source", `SQLCipher` Użyj następujących poleceń.

### <a name="net-core-cli"></a>[interfejs wiersza polecenia programu .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a>SQLitePCLRaw dostępne dostawcy

Jeśli nie korzystasz z pakietu, możesz użyć dostępnych dostawców oprogramowania SQLite z zestawem podstawowym.

| Dostawca | Opis |
|--|--|
| [SQLitePCLRaw. Provider. Dynamic](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | `dynamic`Dostawca ładuje bibliotekę natywną zamiast używać <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> atrybutów. Aby uzyskać więcej informacji na temat korzystania z tego dostawcy, zobacz [Korzystanie z dostawcy dynamicznego](#use-the-dynamic-provider). |
| [SQLitePCLRaw. Provider. e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | `e_sqlite3`Jest to domyślny dostawca. |
| [SQLitePCLRaw. Provider. e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | `e_sqlcipher`Dostawca jest nieoficjalny i nieobsługiwany `SQLCipher` . |
| [SQLitePCLRaw. Provider. sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | `sqlite3`Dostawca jest systemem `SQLite` dla systemów iOS, MacOS i Linux. |
| [SQLitePCLRaw. Provider. SQLCIPHER](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | `sqlcipher`Dostawca jest przeznaczony do oficjalnych `SQLCipher` kompilacji z `Zetetic` . |
| [SQLitePCLRaw. Provider. winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | `winsqlite3`Dostawca dotyczy środowisk systemu Windows 10. |

Aby użyć `sqlite3` dostawcy, użyj następujących poleceń:

### <a name="net-core-cli"></a>[interfejs wiersza polecenia programu .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

Po zainstalowaniu pakietów należy ustawić dostawcę na `sqlite3` wystąpienie.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a>Korzystanie z dostawcy dynamicznego

Możesz użyć własnej kompilacji oprogramowania SQLite, wykorzystując `SQLitePCLRaw.provider.dynamic_cdecl` pakiet. W takim przypadku użytkownik jest odpowiedzialny za wdrożenie biblioteki natywnej w aplikacji. Uwaga Szczegóły wdrażania bibliotek macierzystych w aplikacji różnią się w zależności od używanej platformy .NET i środowiska uruchomieniowego.

Najpierw należy zaimplementować `IGetFunctionPointer` . Implementacja programu .NET Core jest następująca:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

Następnie skonfiguruj `SQLitePCLRaw` dostawcę. Upewnij się, że jest to gotowe `Microsoft.Data.Sqlite` do użycia w aplikacji. Należy również unikać używania `SQLitePCLRaw` pakietu zbiorczego, który może zastąpić dostawcę.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
