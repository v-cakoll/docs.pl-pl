---
title: polecenie Serwer kompilacji DotNet
description: Polecenia dotnet serwer kompilacji wchodzi w interakcję z serwerami, uruchomione przez kompilację.
ms.date: 04/24/2019
ms.openlocfilehash: 491ac37e7f75f930423b3c7e43e3c090ec1ed07d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754276"
---
# <a name="dotnet-build-server"></a>Serwer kompilacji DotNet

**Ten artykuł dotyczy: ✓** zestawu SDK programu .NET Core 2.1 i nowsze wersje

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

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