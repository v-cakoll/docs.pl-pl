---
title: polecenie programu MSBuild programu dotnet
description: Polecenie MSBuild programu dotnet umożliwia dostęp do wiersza polecenia MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117705"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet msbuild`-Kompiluje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Opis

`dotnet msbuild` Polecenie umożliwia dostęp do w pełni funkcjonalnego programu MSBuild.

Polecenie ma takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild tylko dla projektu w stylu zestawu SDK. Opcje są takie same. Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Polecenie [budowania dotnet](dotnet-build.md) jest równoważne z `dotnet msbuild -restore -target:Build`. `dotnet build`jest często używany do kompilowania projektów, ale `dotnet msbuild` daje większą kontrolę. Na przykład jeśli masz konkretny cel, który chcesz uruchomić (bez uruchamiania elementu docelowego kompilacji), prawdopodobnie chcesz użyć `dotnet msbuild`.

## <a name="examples"></a>Przykłady

* Kompiluj projekt i jego zależności:

  ```dotnetcli
  dotnet msbuild
  ```

* Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* Uruchom element docelowy publikowania i opublikuj go `osx.10.11-x64` pod kątem identyfikatora RID:

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* Zobacz cały projekt ze wszystkimi obiektami docelowymi zawartymi w zestawie SDK:

  ```dotnetcli
  dotnet msbuild -pp
  ```
