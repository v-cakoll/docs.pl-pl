---
title: polecenie Serwer kompilacji DotNet
description: Polecenia dotnet serwer kompilacji wchodzi w interakcję z serwerami, uruchomione przez kompilację.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169664"
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

* **`shutdown`**

  Zamyka serwerów kompilacji, które są uruchamiane z dotnet. Domyślnie wszystkie serwery są zamykane.

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`--msbuild`**

  Serwer kompilacji zostanie zamknięte MSBuild.

* **`--razor`**

  Serwer kompilacji zamknięciem elementu Razor.

* **`--vbcscompiler`**

  Zamyka VB / serwer kompilacji kompilator języka C#.