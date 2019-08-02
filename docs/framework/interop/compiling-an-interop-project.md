---
title: Kompilowanie projektu międzyoperacyjnego
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 153df821b0dacccdcbf279bd20bfb106580f3392
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733422"
---
# <a name="compiling-an-interop-project"></a>Kompilowanie projektu międzyoperacyjnego

Projekty międzyoperacyjności modelu COM, które odwołują się do co najmniej jednego zestawu zawierającego zaimportowane typy COM, są kompilowane jak każdy inny projekt zarządzany. Można odwoływać się do zestawów międzyoperacyjnych w środowisku deweloperskim, takim jak Visual Studio, lub można się do nich odwoływać przy użyciu kompilatora wiersza polecenia. W obu przypadkach w celu poprawnego skompilowania zestaw międzyoperacyjny musi znajdować się w tym samym katalogu co inne pliki projektu.

 Istnieją dwa sposoby odwoływania się do zestawów międzyoperacyjnych:

- Osadzone typy międzyoperacyjnych: Począwszy od .NET Framework 4 i programu Visual Studio 2010, można nakazać kompilatorowi osadzenie informacji o typie z zestawu międzyoperacyjnego do pliku wykonywalnego. Jest to zalecana technika.

- Wdrażanie zestawów międzyoperacyjnych: Można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W takim przypadku zestaw międzyoperacyjny musi zostać wdrożony wraz z aplikacją.

 Różnice między tymi dwoma technikami zostały omówione bardziej szczegółowo w temacie [Korzystanie z typów com w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).

 Osadzanie typów międzyoperacyjnych w programie Visual Studio jest [zademonstrowane w przewodniku: Typy osadzania z zestawów zarządzanych w programie Visual StudioC#(](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)) i [wskazówki: Osadzanie typów z zestawów zarządzanych w programie Visual Studio (Visual Basic](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)).

 Aby odwołać się do zestawu międzyoperacyjnego przy użyciu kompilatora wiersza polecenia i informacje o typie osadzania w plikach wykonywalnych, należy użyć [opcji/link (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub/ [/lub/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) kompilatora i określić nazwę zestawu międzyoperacyjnego.

> [!NOTE]
> Aplikacje C++ wizualne nie mogą osadzić informacji o typie, ale mogą współdziałać z aplikacjami lub dodatkami, które wykonują operacje.

 Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny podczas jego wdrażania, użyj przełącznika kompilatora **/Reference** i określ nazwę zestawu międzyoperacyjnego.

## <a name="see-also"></a>Zobacz także

- [Udostępnianie składników COM programowi .NET Framework](exposing-com-components.md)
- [Niezależność od języka i składniki niezależne od języka](../../standard/language-independence-and-language-independent-components.md)
- [Używanie typów COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual StudioC#()](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
