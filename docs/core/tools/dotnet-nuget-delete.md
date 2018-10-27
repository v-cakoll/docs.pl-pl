---
title: DotNet nuget Usuwanie polecenia — interfejs wiersza polecenia platformy .NET Core
description: Polecenia dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: f4aa027a465c4adea1de13853063d03e8e295411
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180884"
---
# <a name="dotnet-nuget-delete"></a>Usuń nuget DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet nuget delete` -Usuwa lub unlists pakietu z serwera.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
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

`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera. Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest wyrejestrowanie pakietu.

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwa/identyfikator pakietu do usunięcia.

`PACKAGE_VERSION`

Wersja pakietu do usunięcia.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--force-english-output`

 Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`--no-service-endpoint` Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła.

`--non-interactive`

Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.

`-s|--source <SOURCE>`

Określa adres URL serwera. Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`. Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--force-english-output`

 Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`--non-interactive`

Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.

`-s|--source <SOURCE>`

Określa adres URL serwera. Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`. Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--force-english-output`

 Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`--non-interactive`

Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.

`-s|--source <SOURCE>`

Określa adres URL serwera. Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`. Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).

---

## <a name="examples"></a>Przykłady

Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowania użytkownika o poświadczenia lub inne dane wejściowe:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
