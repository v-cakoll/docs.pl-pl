---
title: polecenie programu MSBuild programu dotnet
description: Polecenie MSBuild programu dotnet umożliwia dostęp do wiersza polecenia MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733196"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet msbuild` — kompiluje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Opis

`dotnet msbuild` polecenie umożliwia dostęp do w pełni funkcjonalnego programu MSBuild.

Polecenie ma takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild tylko dla projektów w stylu zestawu SDK. Opcje są takie same. Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Polecenie [budowania dotnet](dotnet-build.md) jest równoważne `dotnet msbuild -restore -target:Build`. [kompilacja dotnet](dotnet-build.md) jest częściej używana do kompilowania projektów, ale ponieważ zawsze uruchamia element docelowy kompilacji, można użyć `dotnet msbuild`, gdy nie chcesz kompilować projektu. Na przykład jeśli masz konkretny cel, który chcesz uruchomić bez kompilowania projektu, użyj `dotnet msbuild` i określ element docelowy.

## <a name="examples"></a>Przykłady

* Kompiluj projekt i jego zależności:

  ```dotnetcli
  dotnet msbuild
  ```

* Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* Uruchom element docelowy publikowania i Opublikuj dla `osx.10.11-x64` RID:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* Zobacz cały projekt ze wszystkimi obiektami docelowymi zawartymi w zestawie SDK:

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
