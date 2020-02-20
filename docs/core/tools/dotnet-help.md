---
title: polecenie pomocy dotnet
description: Polecenie pomocy dotnet zawiera bardziej szczegółową dokumentację w trybie online dla określonego polecenia.
ms.date: 02/14/2020
ms.openlocfilehash: f5d9221ae18653451a3bf97dc82fae396ae4e288
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503728"
---
# <a name="dotnet-help-reference"></a>informacje pomocy dotyczące dotnet

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet help` — zawiera bardziej szczegółową dokumentację w trybie online dla określonego polecenia.

## <a name="synopsis"></a>Streszczenie

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Opis

`dotnet help` polecenie otwiera stronę referencyjną, aby uzyskać bardziej szczegółowe informacje na temat określonego polecenia w docs.microsoft.com.

## <a name="arguments"></a>Argumenty

- **`COMMAND_NAME`**

  Nazwa polecenia interfejs wiersza polecenia platformy .NET Core. Aby uzyskać listę prawidłowych poleceń interfejsu wiersza polecenia, zobacz [poleceń interfejsu wiersza polecenia](index.md#cli-commands).

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="examples"></a>Przykłady

- Otwiera stronę dokumentacji dla nowego polecenia [dotnet](dotnet-new.md) :

  ```dotnetcli
  dotnet help new
  ```
