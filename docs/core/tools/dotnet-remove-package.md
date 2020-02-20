---
title: polecenie usunięcia pakietu dotnet
description: Polecenie Narzędzia dotnet Remove Package udostępnia wygodną opcję usunięcia odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503631"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Name (Nazwa)

`dotnet remove package` — usuwa odwołanie do pakietu z pliku projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet remove package` udostępnia wygodną opcję usunięcia odwołania do pakietu NuGet z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.

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
