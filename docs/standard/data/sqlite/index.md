---
title: Omówienie
ms.date: 12/13/2019
description: Omówienie pliku Microsoft.Data.Sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543602"
---
# <a name="microsoftdatasqlite-overview"></a>Omówienie programu Microsoft.Data.Sqlite

Microsoft.Data.Sqlite jest lekkim [dostawcą ADO.NET](../../../framework/data/adonet/index.md) dla SQLite. Dostawca [entity framework core](/ef/core/) dla SQLite jest zbudowany na tej bibliotece. Jednak może być również używany niezależnie lub z innymi bibliotekami dostępu do danych.

## <a name="installation"></a>Instalacja

Najnowsza stabilna wersja jest dostępna na [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

### <a name="net-core-cli"></a>[Interfejs wiersza polecenia platformy .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Sposób użycia

Ta biblioteka implementuje wspólne abstrakcje ADO.NET dla połączeń, poleceń, czytników danych i tak dalej.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Zobacz też

* [Parametry połączeń](connection-strings.md)
* [Dokumentacja interfejsu API](/dotnet/api/?view=msdata-sqlite-3.0)
* [Składnia SQL](https://www.sqlite.org/lang.html)
