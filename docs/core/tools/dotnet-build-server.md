---
title: polecenie Serwer kompilacji DotNet - interfejsu wiersza polecenia platformy .NET Core
description: Polecenia dotnet serwer kompilacji wchodzi w interakcję z serwerami, uruchomione przez kompilację.
author: mairaw
ms.author: mairaw
ms.date: 07/02/2018
ms.openlocfilehash: 1c59c85f246b79c7e2552f704db5b4f076f9b502
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404336"
---
# <a name="dotnet-build-server"></a>Serwer kompilacji DotNet

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet build-server` -Współdziała z serwerami, uruchomione przez kompilację.

## <a name="synopsis"></a>Streszczenie

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Polecenia

`shutdown`

Zamyka serwerów kompilacji, które są uruchamiane z dotnet. Domyślnie wszystkie serwery są zamykane.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--msbuild`

Serwer kompilacji zostanie zamknięte MSBuild.

`--razor`

Serwer kompilacji zamknięciem elementu Razor.

`--vbcscompiler`

Zamyka VB / serwer kompilacji kompilator języka C#.
