---
title: Omówienie
ms.date: 12/13/2019
description: Omówienie programu Microsoft. Data. sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543602"
---
# <a name="microsoftdatasqlite-overview"></a>Microsoft. Data. sqlite — Omówienie

Microsoft. Data. sqlite to lekki dostawca [ADO.NET](../../../framework/data/adonet/index.md) dla oprogramowania SQLite. Dostawca [Entity Framework Core](/ef/core/) dla oprogramowania SQLite został utworzony na podstawie tej biblioteki. Można go również używać niezależnie lub z innymi bibliotekami dostępu do danych.

## <a name="installation"></a>Instalacja

Najnowsza stabilna wersja jest dostępna w programie [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Sposób użycia

Ta biblioteka implementuje typowe abstrakcje ADO.NET dla połączeń, poleceń, czytników danych i tak dalej.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Zobacz też

* [Parametry połączenia](connection-strings.md)
* [Dokumentacja interfejsu API](/dotnet/api/?view=msdata-sqlite-3.0)
* [Składnia języka SQL](https://www.sqlite.org/lang.html)
