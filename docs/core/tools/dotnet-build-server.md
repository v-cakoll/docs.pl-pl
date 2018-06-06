---
title: polecenie serwera kompilacji DotNet - .NET Core interfejsu wiersza polecenia
description: Serwer kompilacji dotnet wchodzi w interakcję z serwerami uruchomione przez kompilację.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 929b8d74aa5f3f0ad73b108be8a5bf22f86e30d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696257"
---
# <a name="dotnet-build"></a>dotnet-build

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet build-server` -Współdziała z serwerami uruchomione przez kompilację.

## <a name="synopsis"></a>Streszczenie

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Polecenia

`shutdown`

Zamyka serwery kompilacji, które są uruchamiane z dotnet. Domyślnie wszystkie serwery są zamknięte.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--msbuild`

Serwer kompilacji zamknięciu programu MSBuild.

`--razor`

Serwer kompilacji zamknięciu elementu Razor.

`--vbcscompiler`

Zamyka VB / serwer kompilacji kompilator języka C#.
