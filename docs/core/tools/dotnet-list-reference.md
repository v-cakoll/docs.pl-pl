---
title: polecenie odwołania list DotNet
description: Polecenia dotnet list odwołania zapewnia wygodny sposób do listy odwołania projekt-projekt.
ms.date: 12/03/2018
ms.openlocfilehash: c0b88c4a0af4469d7ddc9e0a9368bb1b2d9d20b6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632409"
---
# <a name="dotnet-list-reference"></a>Odwołanie do listy DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet list reference` — Wyświetla listę odwołania projekt projekt.

## <a name="synopsis"></a>Streszczenie

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Opis

`dotnet list reference` Polecenia oferuje wygodne opcję do listy odwołań projektu dla danego projektu lub rozwiązania.

## <a name="arguments"></a>Argumenty

* **`PROJECT`**

  Określa plik projektu na potrzeby wyświetlania listy odwołania. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla pliku projektu.

## <a name="options"></a>Opcje

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

## <a name="examples"></a>Przykłady

* Utwórz listę odwołań projektu dla określonego projektu.

  ```console
  dotnet list app/app.csproj reference
  ```

* Listy odwołań projektu dla projektu w bieżącym katalogu:

  ```console
  dotnet list reference
  ```
