---
title: polecenie Serwer kompilacji DotNet
description: Polecenia dotnet serwer kompilacji wchodzi w interakcję z serwerami, uruchomione przez kompilację.
ms.date: 04/24/2019
ms.openlocfilehash: fa663bc045e8abfc3375a0226be7d16331b49740
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632094"
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
