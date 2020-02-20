---
title: Kompilacja dotnet — polecenie serwera
description: Polecenie programu dotnet Build-Server współdziała z serwerami uruchomionymi przez kompilację.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503778"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet build-server` — współdziała z serwerami uruchomionymi przez kompilację.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Polecenia

- **`shutdown`**

  Zamyka serwery kompilacji uruchomione z programu dotnet. Domyślnie wszystkie serwery są wyłączone.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--msbuild`**

  Zamyka serwer kompilacji MSBuild.

- **`--razor`**

  Zamyka serwer kompilacji Razor.

- **`--vbcscompiler`**

  Zamyka serwer kompilacji VB/C# kompilatora.
