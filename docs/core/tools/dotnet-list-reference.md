---
title: polecenie odwołania do listy dotnet
description: Polecenie odwołania do listy dotnet udostępnia wygodną opcję wyświetlania listy odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802766"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet list reference`-Wyświetla odwołania projektu do projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a>Opis

`dotnet list reference`Polecenie udostępnia wygodną opcję wyświetlania listy odwołań projektu dla danego projektu.

## <a name="arguments"></a>Argumenty

* **`PROJECT`**

  Plik projektu do działania. Jeśli plik nie zostanie określony, polecenie przeszuka bieżący katalog.

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
