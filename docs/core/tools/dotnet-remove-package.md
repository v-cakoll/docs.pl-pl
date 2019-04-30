---
title: polecenia DotNet Usuń polecenie pakietu
description: Polecenia dotnet Usuń pakiet zapewnia wygodny sposób, aby usunąć odwołanie do pakietu NuGet do projektu.
ms.date: 05/29/2018
ms.openlocfilehash: 4cc8ac927b761547dc5e53be9abeba827bf1e1d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664860"
---
# <a name="dotnet-remove-package"></a>polecenia DotNet Usuń pakiet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet remove package` -Usuwa odwołanie do pakietu z pliku projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Opis

`dotnet remove package` Polecenie zapewnia wygodny sposób, aby usunąć odwołanie do pakietu NuGet z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Określa plik projektu. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.

`PACKAGE_NAME`

Odwołanie pakietu do usunięcia.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

## <a name="examples"></a>Przykłady

Usuwa `Newtonsoft.Json` pakietu NuGet z projektu w bieżącym katalogu:

`dotnet remove package Newtonsoft.Json`