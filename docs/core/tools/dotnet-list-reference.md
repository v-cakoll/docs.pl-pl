---
title: polecenie odwołania do listy dotnet
description: Polecenie odwołania do listy dotnet udostępnia wygodną opcję wyświetlania listy odwołań do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733225"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

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
