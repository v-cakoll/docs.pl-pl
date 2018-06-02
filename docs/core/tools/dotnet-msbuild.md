---
title: polecenie msbuild DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie msbuild dotnet zapewnia dostęp do wiersza polecenia programu MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 58aac2a5314758b8711c0b014154022168fb671c
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696848"
---
# <a name="dotnet-msbuild"></a>DotNet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet msbuild` -Tworzy projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Opis

`dotnet msbuild` Polecenia umożliwia dostęp do pełnej funkcjonalności programu MSBuild.

Polecenie ma dokładnie takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild. Opcje są takie same. Aby uzyskać więcej informacji o dostępnych opcjach, zobacz [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

## <a name="examples"></a>Przykłady

Tworzenie projektu i jego zależności:

`dotnet msbuild`

Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:

`dotnet msbuild /p:Configuration=Release`

Uruchom lokalizacja docelowa publikowania i publikowania dla `osx.10.11-x64` identyfikatorów RID:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

Zobacz całego projektu z wszystkie elementy docelowe uwzględniony przez zestaw SDK:

`dotnet msbuild /pp`
