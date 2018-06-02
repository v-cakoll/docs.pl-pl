---
title: polecenie - .NET Core interfejsu wiersza polecenia delete DotNet nuget
description: Polecenie dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a56ddaba72f8e1a76db810231e64993c657e908e
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697245"
---
# <a name="dotnet-nuget-delete"></a>Usuń nuget DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet nuget delete` — Usuwa lub unlists pakietu z serwera.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera. Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest unlist pakietu.

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwa/identyfikator pakietu do usunięcia.

`PACKAGE_VERSION`

Wersja pakietu do usunięcia.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)

`--force-english-output`

 Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

` --no-service-endpoint` Nie dołącza "interfejsu api w wersji 2/packages" adres URL źródła.

`--non-interactive`

Nie monituj o dane wejściowe użytkownika lub potwierdzeń.

`-s|--source <SOURCE>`

Określa adres URL serwera. Obsługiwane adresy URL to nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, i `http://www.nuget.org/api/v2/package`. Dla prywatnych źródeł danych, zastąp nazwą hosta (na przykład `%hostname%/api/v3`).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--force-english-output`

 Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`--non-interactive`

Nie monituj o dane wejściowe użytkownika lub potwierdzeń.

`-s|--source <SOURCE>`

Określa adres URL serwera. Obsługiwane adresy URL to nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, i `http://www.nuget.org/api/v2/package`. Dla prywatnych źródeł danych, zastąp nazwą hosta (na przykład `%hostname%/api/v3`).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--force-english-output`

 Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`--non-interactive`

Nie monituj o dane wejściowe użytkownika lub potwierdzeń.

`-s|--source <SOURCE>`

Określa adres URL serwera. Obsługiwane adresy URL to nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, i `http://www.nuget.org/api/v2/package`. Dla prywatnych źródeł danych, zastąp nazwą hosta (na przykład `%hostname%/api/v3`).

---

## <a name="examples"></a>Przykłady

Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowanie użytkownika o poświadczenia lub innych danych wejściowych:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`