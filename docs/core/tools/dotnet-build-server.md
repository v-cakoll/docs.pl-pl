---
title: Kompilacja dotnet — polecenie serwera
description: Polecenie programu dotnet Build-Server współdziała z serwerami uruchomionymi przez kompilację.
ms.date: 04/24/2019
ms.openlocfilehash: 89d1aba104e2cb07b46766a3768eed68d85a7aa7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117770"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Ten artykuł dotyczy: ✓** .net Core 2,1 SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Nazwa

`dotnet build-server`— Współdziała z serwerami uruchomionymi przez kompilację.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Polecenia

* **`shutdown`**

  Zamyka serwery kompilacji uruchomione z programu dotnet. Domyślnie wszystkie serwery są wyłączone.

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--msbuild`**

  Zamyka serwer kompilacji MSBuild.

* **`--razor`**

  Zamyka serwer kompilacji Razor.

* **`--vbcscompiler`**

  Zamyka serwer kompilacji VB/C# kompilatora.
