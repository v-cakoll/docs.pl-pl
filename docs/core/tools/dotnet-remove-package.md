---
title: dotnet usunąć pakiet, polecenie
description: Polecenie dotnet remove package zapewnia wygodną opcję usunięcia odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463456"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet remove package`- Usuwa odwołanie do pakietu z pliku projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet remove package` zapewnia wygodną opcję, aby usunąć odwołanie do pakietu NuGet z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego.

`PACKAGE_NAME`

Odwołanie do pakietu do usunięcia.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="examples"></a>Przykłady

- Usuń `Newtonsoft.Json` pakiet NuGet z projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
