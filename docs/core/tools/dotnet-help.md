---
title: polecenie pomocy dotnet
description: Polecenie pomocy dotnet zawiera bardziej szczegółową dokumentację w trybie online dla określonego polecenia.
ms.date: 08/08/2019
ms.openlocfilehash: 533f2c47fa7ec14d31368538092fec2490234820
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117719"
---
# <a name="dotnet-help-reference"></a>informacje pomocy dotyczące dotnet

**Ten artykuł dotyczy: ✓** .net Core 2,0 SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a>Nazwa

`dotnet help`-Wyświetla bardziej szczegółową dokumentację w trybie online dla określonego polecenia.

## <a name="synopsis"></a>Streszczenie

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Opis

`dotnet help` Polecenie otwiera stronę referencyjną, aby uzyskać bardziej szczegółowe informacje na temat określonego polecenia w docs.Microsoft.com.

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
