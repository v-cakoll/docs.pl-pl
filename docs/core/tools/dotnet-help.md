---
title: polecenie pomocy dotnet
description: Polecenie pomocy dotnet zawiera bardziej szczegółową dokumentację dla określonego polecenia.
ms.date: 02/14/2020
ms.openlocfilehash: a59e74a318118b6fd39d1895df02d76daa6fc9e1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463690"
---
# <a name="dotnet-help-reference"></a>odwołanie do pomocy dotnet

**Ten artykuł dotyczy:** ✔️.NET Core 2.0 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet help`- Pokazuje bardziej szczegółową dokumentację online dla określonego polecenia.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet help <COMMAND_NAME> [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet help` otwiera stronę referencyjną, aby uzyskać bardziej szczegółowe informacje o określonym poleceniu w docs.microsoft.com.

## <a name="arguments"></a>Argumenty

- **`COMMAND_NAME`**

  Nazwa polecenia .NET Core CLI. Aby uzyskać listę prawidłowych poleceń interfejsu wiersza polecenia, zobacz [polecenia interfejsu wiersza polecenia](index.md#cli-commands).

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="examples"></a>Przykłady

- Otwiera stronę dokumentacji nowego polecenia [dotnet:](dotnet-new.md)

  ```dotnetcli
  dotnet help new
  ```
