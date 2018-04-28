---
title: polecenie msbuild DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie msbuild dotnet zapewnia dostęp do wiersza polecenia programu MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 9e6f8b3063b4cd2a3a36cae8839d6f83e0466e03
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-msbuild"></a>DotNet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet msbuild` -Tworzy projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Opis

`dotnet msbuild` Polecenia umożliwia dostęp do pełnej funkcjonalności programu MSBuild.

Polecenie ma dokładnie takie same możliwości jak istniejący klient wiersza polecenia programu MSBuild. Opcje są takie same. Użyj [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) uzyskiwania informacji na temat dostępnych opcji. 

## <a name="examples"></a>Przykłady

Tworzenie projektu i jego zależności:

`dotnet msbuild`

Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:

`dotnet msbuild /p:Configuration=Release`

Uruchom lokalizacja docelowa publikowania i publikowania dla `osx.10.11-x64` identyfikatorów RID:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

Zobacz całego projektu z wszystkie elementy docelowe uwzględniony przez zestaw SDK:

`dotnet msbuild /pp`
