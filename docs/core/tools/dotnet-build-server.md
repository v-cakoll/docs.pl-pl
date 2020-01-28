---
title: Kompilacja dotnet — polecenie serwera
description: Polecenie programu dotnet Build-Server współdziała z serwerami uruchomionymi przez kompilację.
ms.date: 04/24/2019
ms.openlocfilehash: e77a4d9f49f555ac847bb13380380599eef881b1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734377"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Nazwa

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
