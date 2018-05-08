---
title: polecenie - .NET Core interfejsu wiersza polecenia delete DotNet nuget
description: Polecenie dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 639ade54bfed5eb2de89bdb3b7f451393b4be187
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-nuget-delete"></a>Usuń nuget DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet nuget delete` — Usuwa lub unlists pakietu z serwera.

## <a name="synopsis"></a>Streszczenie

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a>Opis

`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera. Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest unlist pakietu.

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Pakiet do usunięcia.

`PACKAGE_VERSION`

Wersja pakietu do usunięcia.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-s|--source <SOURCE>`

Określa adres URL serwera. Obsługiwane adresy URL to nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, i `http://www.nuget.org/api/v2/package`. Dla prywatnych źródeł danych, zastąp nazwą hosta (na przykład `%hostname%/api/v3`).

`--non-interactive`

Nie monituj o dane wejściowe użytkownika lub potwierdzeń.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`--force-english-output`

Wiersza polecenia wymusza dane wyjściowe w języku angielskim.

## <a name="examples"></a>Przykłady

Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowanie użytkownika o poświadczenia lub innych danych wejściowych:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`