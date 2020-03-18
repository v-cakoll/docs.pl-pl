---
title: polecenie dotnet remove package
description: Polecenie dotnet remove package zapewnia wygodną opcję usunięcia odwołania nuget do pakietu do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503631"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet remove package`- Usuwa odwołanie do pakietu z pliku projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet remove package` zawiera wygodną opcję, aby usunąć odwołanie nuget pakietu z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego.

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
