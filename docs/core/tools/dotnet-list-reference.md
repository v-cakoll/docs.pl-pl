---
title: polecenie odwołania listy DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie dotnet listy odwołania zapewnia to wygodny sposób na liście odwołań projektów.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 821e6d276af44bf984c8ac1b42b4e954dbe69556
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697186"
---
# <a name="dotnet-list-reference"></a>Odwołanie do listy DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet list reference` -Listy odwołania projektu do projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Opis

`dotnet list reference` Polecenie zapewnia to wygodny sposób na liście odwołań do projektu dla danego projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Określa plik projektu, który będzie używany do wyświetlania listy odwołania. Jeśli nie zostanie określony, polecenie wyszukuje bieżący katalog dla pliku projektu.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

## <a name="examples"></a>Przykłady

Lista odwołań do projektu dla określonego projektu:

`dotnet list app/app.csproj reference`

Lista odwołań do projektu dla projektu w bieżącym katalogu:

`dotnet list reference`