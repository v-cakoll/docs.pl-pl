---
title: Ładowanie zależności — .NET Core
description: Omówienie ładowania zależności zarządzanej i niezarządzanej w ustom .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416641"
---
# <a name="dependency-loading-in-net-core"></a>Ładowanie zależności w ustom .NET Core

Każda aplikacja .NET Core ma zależności. Nawet prosta `hello world` aplikacja ma zależności od części bibliotek klas .NET Core.

Opis logiki domyślnego ładowania zestawu .NET Core może pomóc w zrozumieniu i debugowaniu typowych problemów z wdrażaniem.

W niektórych aplikacjach zależności są dynamicznie określane w czasie wykonywania. W takich sytuacjach ważne jest, aby zrozumieć, jak są ładowane zestawy zarządzane i niezarządzane zależności.

## <a name="understanding-assemblyloadcontext"></a>Informacje o elemencie AssemblyLoadContext

Interfejs <xref:System.Runtime.Loader.AssemblyLoadContext> API jest centralnym elementem projektu ładowania .NET Core. [Opis AssemblyLoadContext](understanding-assemblyloadcontext.md) artykuł zawiera omówienie koncepcyjne do projektu.

## <a name="loading-details"></a>Ładowanie szczegółów

Szczegóły algorytmu ładowania są krótko omówione w kilku artykułach:

- [Algorytm ładowania zestawu zarządzanego](loading-managed.md)
- [Algorytm ładowania zestawu satelitarnego](loading-resources.md)
- [Niezarządzany (natywny) algorytm ładowania biblioteki](loading-unmanaged.md)
- [Sondowanie domyślne](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Tworzenie aplikacji platformy .NET Core za pomocą wtyczek

Samouczek [Tworzenie aplikacji .NET Core z wtyczkami](../tutorials/creating-app-with-plugin-support.md) opisuje sposób tworzenia niestandardowego AssemblyLoadContext. Używa <xref:System.Runtime.Loader.AssemblyDependencyResolver> do rozwiązywania zależności wtyczki. Samouczek poprawnie izoluje zależności wtyczki od aplikacji hostingowej.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core

[Jak używać i debugować zwalnialność zestawu w](../../standard/assembly/unloadability.md) artykule .NET Core jest samouczek krok po kroku. Pokazuje, jak załadować aplikację .NET Core, wykonać, a następnie zwolnić go. Artykuł zawiera również wskazówki dotyczące debugowania.
