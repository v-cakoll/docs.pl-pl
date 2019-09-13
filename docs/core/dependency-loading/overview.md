---
title: Ładowanie zależności — .NET Core
description: Omówienie zarządzanego i niezarządzanego ładowania zależności w programie .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 0388bd1fa29ce1caad93c917503dac9eed8974e1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926398"
---
# <a name="dependency-loading-in-net-core"></a>Ładowanie zależności w programie .NET Core

Każda aplikacja .NET Core ma zależności. Nawet prosta `hello world` aplikacja ma zależności dotyczące części bibliotek klas .NET Core.

Informacje o standardowej logiki ładowania zestawów programu .NET Core mogą pomóc w zrozumieniu i debugowaniu typowych problemów z wdrażaniem.

W niektórych aplikacjach zależności są określane dynamicznie w czasie wykonywania. W takich sytuacjach ważne jest, aby zrozumieć, jak są ładowane zestawy zarządzane i niezarządzane zależności.

## <a name="understanding-assemblyloadcontext"></a>Informacje o elemencie AssemblyLoadContext

<xref:System.Runtime.Loader.AssemblyLoadContext> Interfejs API jest centralny w projekcie ładowania .NET Core. Artykuł dotyczący [poznania AssemblyLoadContext](understanding-assemblyloadcontext.md) zawiera omówienie pojęć dotyczących projektu.

## <a name="loading-details"></a>Ładowanie szczegółów

Szczegóły algorytmu ładowania zostały omówione krótko w kilku artykułach:

- [Algorytm ładowania zestawu zarządzanego](loading-managed.md)
- [Algorytm ładowania zestawu satelitarnego](loading-resources.md)
- [Algorytm ładowania biblioteki niezarządzanej (natywnej)](loading-unmanaged.md)
- [Domyślna sonda](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Tworzenie aplikacji platformy .NET Core za pomocą wtyczek

Samouczek [Tworzenie aplikacji platformy .NET Core z wtyczkami](../tutorials/creating-app-with-plugin-support.md) zawiera opis sposobu tworzenia niestandardowego AssemblyLoadContext. Używa <xref:System.Runtime.Loader.AssemblyDependencyResolver> do rozpoznawania zależności wtyczki. Samouczek prawidłowo izoluje zależności wtyczki od aplikacji hostingowej.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core

[Użycie i debugowanie zestawu do odciążania w artykule .NET Core](../../standard/assembly/unloadability-howto.md) to samouczek krok po kroku. Pokazuje sposób ładowania aplikacji platformy .NET Core, wykonywania, a następnie zwalniania jej. Artykuł zawiera również porady dotyczące debugowania.
