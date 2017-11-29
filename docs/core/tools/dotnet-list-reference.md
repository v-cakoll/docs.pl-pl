---
title: "polecenie odwołania listy DotNet - .NET Core interfejsu wiersza polecenia"
description: "Polecenie dotnet listy odwołania zapewnia to wygodny sposób na liście odwołań projektów."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: b3e903c15a7486faa279d47ad5e2e00c090b19af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-list-reference"></a>Odwołanie do listy DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet list reference`-Listy odwołań projektów.

## <a name="synopsis"></a>Streszczenie

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Opis

`dotnet list reference` Polecenie zapewnia to wygodny sposób na liście odwołań do projektu dla danego projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Określa plik projektu, który będzie używany do wyświetlania listy odwołania. Jeśli nie zostanie określony, polecenie będzie szukał bieżący katalog dla pliku projektu.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

## <a name="examples"></a>Przykłady

Lista odwołań do projektu dla określonego projektu:

`dotnet list app/app.csproj reference`

Lista odwołań do projektu dla projektu w bieżącym katalogu:

`dotnet list reference`
