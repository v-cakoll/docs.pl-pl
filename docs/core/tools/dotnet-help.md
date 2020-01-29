---
title: polecenie pomocy dotnet
description: Polecenie pomocy dotnet zawiera bardziej szczegółową dokumentację w trybie online dla określonego polecenia.
ms.date: 08/08/2019
ms.openlocfilehash: 9bb4e54d2634c000707752edf53b38af43c4344e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734232"
---
# <a name="dotnet-help-reference"></a>informacje pomocy dotyczące dotnet

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a>Nazwa

`dotnet help` — zawiera bardziej szczegółową dokumentację w trybie online dla określonego polecenia.

## <a name="synopsis"></a>Streszczenie

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Opis

`dotnet help` polecenie otwiera stronę referencyjną, aby uzyskać bardziej szczegółowe informacje na temat określonego polecenia w docs.microsoft.com.

## <a name="arguments"></a>Argumenty

* **`COMMAND_NAME`**

  Nazwa polecenia interfejs wiersza polecenia platformy .NET Core. Aby uzyskać listę prawidłowych poleceń interfejsu wiersza polecenia, zobacz [poleceń interfejsu wiersza polecenia](index.md#cli-commands).

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="examples"></a>Przykłady

* Otwiera stronę dokumentacji dla nowego polecenia [dotnet](dotnet-new.md) :

  ```dotnetcli
  dotnet help new
  ```
