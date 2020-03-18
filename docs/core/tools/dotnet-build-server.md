---
title: polecenie dotnet build-server
description: Polecenie dotnet build-server współdziała z serwerami uruchomionymi przez kompilację.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503778"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet build-server`- Współdziała z serwerami uruchomionymi przez kompilację.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
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

  Zamyka serwer kompilacji Razor.

- **`--vbcscompiler`**

  Zamyka serwer kompilacji kompilatora VB/C#.
