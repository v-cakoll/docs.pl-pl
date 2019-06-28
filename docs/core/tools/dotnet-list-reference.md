---
title: polecenie odwołania list DotNet
description: Polecenia dotnet list odwołania zapewnia wygodny sposób do listy odwołania projekt-projekt.
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421830"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet list reference` — Wyświetla listę odwołania projekt projekt.

## <a name="synopsis"></a>Streszczenie

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Opis

`dotnet list reference` Polecenia oferuje wygodne opcję do listy odwołań projektu dla danego projektu lub rozwiązania.

## <a name="arguments"></a>Argumenty

* **`PROJECT | SOLUTION`**

  Określa plik projektu lub rozwiązania służące do wyświetlania listy odwołania. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla pliku projektu.

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
