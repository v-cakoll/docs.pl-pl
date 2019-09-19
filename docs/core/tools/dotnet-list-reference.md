---
title: polecenie odwołania do listy dotnet
description: Polecenie odwołania do listy dotnet udostępnia wygodną opcję wyświetlania listy odwołań do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: b4b82ca1e7aeb2b73d9f99aff1c97452b2166770
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117681"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Ten temat dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet list reference`-Wyświetla odwołania projektu do projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Opis

`dotnet list reference` Polecenie udostępnia wygodną opcję wyświetlania listy odwołań projektu dla danego projektu lub rozwiązania.

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
