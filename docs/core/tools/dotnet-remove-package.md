---
title: DotNet Usuń polecenie pakietu - .NET Core interfejsu wiersza polecenia
description: Polecenie pakietu Usuń dotnet zapewnia to wygodny sposób, aby usunąć odwołanie do pakietu NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ed6086bfdfadaa06494c857fc74687f1273af971
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696861"
---
# <a name="dotnet-remove-package"></a>Pakiet Usuń DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet remove package` — Usuwa odwołanie do pakietu z pliku projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Opis

`dotnet remove package` Polecenie zapewnia to wygodny sposób, aby usunąć odwołanie do pakietu NuGet z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Określa plik projektu. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.

`PACKAGE_NAME`

Odwołanie pakietu do usunięcia.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

## <a name="examples"></a>Przykłady

Usuwa `Newtonsoft.Json` pakietu NuGet z projektu w bieżącym katalogu:

`dotnet remove package Newtonsoft.Json`