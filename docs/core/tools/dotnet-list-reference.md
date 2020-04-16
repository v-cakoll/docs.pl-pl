---
title: polecenie odwołania do listy dotnet
description: Polecenie referencyjne listy dotnet zapewnia wygodną opcję listy odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: c0ea46298123e69ae527870e50d204d8fcf5cc85
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463645"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet list reference`- Wyświetla listę odwołań do projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] reference

dotnet list -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet list reference` zapewnia wygodną opcję listy odwołań do projektu dla danego projektu lub rozwiązania.

## <a name="arguments"></a>Argumenty

* **`PROJECT | SOLUTION`**

  Określa plik projektu lub rozwiązania, który ma być używany do wyświetlania odwołań do listy. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu pliku projektu.

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="examples"></a>Przykłady

* Lista odwołań do projektu dla określonego projektu:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Wyświetl listę odwołań do projektu dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet list reference
  ```
