---
title: polecenie msbuild DotNet
description: Polecenie msbuild dotnet zapewnia dostęp do wiersza polecenia programu MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: f025b5b92e57c7b804b9bdd59c8b4a4a806796da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648701"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet msbuild` -Kompiluje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Opis

`dotnet msbuild` Polecenia umożliwia dostęp do pełnej funkcjonalności programu MSBuild.

Polecenie ma dokładnie te same możliwości co istniejący klient wiersza polecenia MSBuild tylko projekt w stylu zestawu SDK. Opcje są takie same. Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

[Kompilacji dotnet](dotnet-build.md) polecenie jest odpowiednikiem `dotnet msbuild -restore -target:Build`. `dotnet build` jest częściej używany do tworzenia projektów, ale `dotnet msbuild` daje większą kontrolę. Na przykład, jeśli określony element docelowy ma zostać uruchomiony (bez konieczności uruchamiania docelowej kompilacji), prawdopodobnie chcesz użyć `dotnet msbuild`.

## <a name="examples"></a>Przykłady

* Tworzenie projektu i jego zależności:

  ```console
  dotnet msbuild
  ```

* Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:

  ```console
  dotnet msbuild -p:Configuration=Release
  ```

* Uruchom docelową lokalizację publikacji i publikowania dla `osx.10.11-x64` identyfikatorów RID:

  ```console
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* Zobacz całego projektu za pomocą wszystkie elementy docelowe uwzględniony przez zestaw SDK:

  ```console
  dotnet msbuild -pp
  ```