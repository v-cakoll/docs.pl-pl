---
title: DotNet Usuń polecenie pakietu - .NET Core interfejsu wiersza polecenia
description: Polecenie pakietu Usuń dotnet zapewnia to wygodny sposób, aby usunąć odwołanie do pakietu NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: bdb66a24526b04e8300e654a991719bb607971b8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
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

Określa plik projektu. Jeśli nie zostanie określony, polecenie będzie wyszukać bieżącego katalogu.

`PACKAGE_NAME`

Odwołanie pakietu do usunięcia.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

## <a name="examples"></a>Przykłady

Usuwa `Newtonsoft.Json` pakietu NuGet z projektu w bieżącym katalogu:

`dotnet remove package Newtonsoft.Json`
