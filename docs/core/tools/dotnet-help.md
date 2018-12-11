---
title: polecenie pomocy DotNet
description: Polecenia dotnet pomocy zawiera bardziej szczegółowe dokumentację online dla określonego polecenia.
ms.date: 12/04/2018
ms.openlocfilehash: 44274b698ed83bd3cdb58787f433eeb5c555bc6d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168959"
---
# <a name="dotnet-help-reference"></a>Dokumentacja pomocy DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Nazwa

`dotnet help` -Przedstawiono bardziej szczegółowe dokumentację online dla określonego polecenia.

## <a name="synopsis"></a>Streszczenie

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Opis

`dotnet help` Polecenie otwiera stronę odwołania, aby uzyskać szczegółowe informacje dotyczące określonego polecenia w witrynie docs.microsoft.com.

## <a name="arguments"></a>Argumenty

* **`COMMAND_NAME`**

  Nazwa polecenia interfejsu wiersza polecenia platformy .NET Core. Aby uzyskać listę prawidłowych poleceń interfejsu wiersza polecenia, zobacz [poleceń interfejsu wiersza polecenia](index.md#cli-commands).

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

## <a name="examples"></a>Przykłady

* Otwiera stronę dokumentacji [dotnet nowe](dotnet-new.md) polecenia:

  ```console
  dotnet help new
  ```