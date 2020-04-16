---
title: polecenie dotnet build-server
description: Polecenie dotnet build-server współdziała z serwerami uruchomionymi przez kompilację.
ms.date: 02/14/2020
ms.openlocfilehash: 882b697c07aac0e20266f3ad4e6c11888a0b7acc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463727"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet build-server`- Współdziała z serwerami uruchomionymi przez kompilację.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]

dotnet build-server shutdown -h|--help

dotnet build-server -h|--help
```

## <a name="commands"></a>Polecenia

- **`shutdown`**

  Zamyka serwery kompilacji, które są uruchamiane z dotnet. Domyślnie wszystkie serwery są zamykane.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--msbuild`**

  Zamyka serwer kompilacji MSBuild.

- **`--razor`**

  Wyłącza serwer kompilacji Razor.

- **`--vbcscompiler`**

  Zamyka serwer kompilacji kompilatora VB/C#.
