---
title: polecenie msbuild DotNet — interfejs wiersza polecenia platformy .NET Core
description: Polecenie msbuild dotnet zapewnia dostęp do wiersza polecenia programu MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 76165590478b0e76d19d546c87e012da4716b6db
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082334"
---
# <a name="dotnet-msbuild"></a>Program msbuild DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet msbuild` -Kompiluje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Opis

`dotnet msbuild` Polecenia umożliwia dostęp do pełnej funkcjonalności programu MSBuild.

Polecenie ma dokładnie te same możliwości co istniejący klient wiersza polecenia programu MSBuild. Opcje są takie same. Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

## <a name="examples"></a>Przykłady

Tworzenie projektu i jego zależności:

`dotnet msbuild`

Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:

`dotnet msbuild -p:Configuration=Release`

Uruchom docelową lokalizację publikacji i publikowania dla `osx.10.11-x64` identyfikatorów RID:

`dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64`

Zobacz całego projektu za pomocą wszystkie elementy docelowe uwzględniony przez zestaw SDK:

`dotnet msbuild -pp`
