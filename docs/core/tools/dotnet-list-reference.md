---
title: polecenie odwołania do listy dotnet
description: Polecenie odwołania do listy dotnet zapewnia wygodną opcję listy projektów do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503719"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet list reference`- Wyświetla listę odniesień do projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Opis

Polecenie `dotnet list reference` zapewnia wygodną opcję listy odwołań do projektu dla danego projektu lub rozwiązania.

## <a name="arguments"></a>Argumenty

* **`PROJECT | SOLUTION`**

  Określa plik projektu lub rozwiązania, który ma być używany do wyświetlania odwołań do aukcji. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu pliku projektu.

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="examples"></a>Przykłady

* Lista odwołań do projektu dla określonego projektu:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Lista odwołań do projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet list reference
  ```
