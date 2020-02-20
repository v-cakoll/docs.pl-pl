---
title: polecenie odwołania do listy dotnet
description: Polecenie odwołania do listy dotnet udostępnia wygodną opcję wyświetlania listy odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503719"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Name (Nazwa)

`dotnet list reference` — wyświetla odwołania projektu do projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Opis

Polecenie `dotnet list reference` udostępnia wygodną opcję wyświetlania listy odwołań projektu dla danego projektu lub rozwiązania.

## <a name="arguments"></a>Argumenty

* **`PROJECT | SOLUTION`**

  Określa plik projektu lub rozwiązania, który ma być używany na potrzeby wyświetlania listy odwołań. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla pliku projektu.

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="examples"></a>Przykłady

* Wyświetl listę odwołań projektu dla określonego projektu:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Wyświetl listę odwołań projektu dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet list reference
  ```
