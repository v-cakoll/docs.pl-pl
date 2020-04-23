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
ms.openlocfilehash: 32102910ae674a97e941e1346a1898585f503527
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123683"
---
# <a name="compiling-an-interop-project"></a>Kompilowanie projektu międzyoperacyjnego

Projekty międzyoperacyjności modelu COM, które odwołują się do co najmniej jednego zestawu zawierającego zaimportowane typy COM, są kompilowane jak każdy inny projekt zarządzany. Można odwoływać się do zestawów międzyoperacyjnych w środowisku deweloperskim, takim jak Visual Studio, lub można się do nich odwoływać przy użyciu kompilatora wiersza polecenia. W obu przypadkach w celu poprawnego skompilowania zestaw międzyoperacyjny musi znajdować się w tym samym katalogu co inne pliki projektu.

 Istnieją dwa sposoby odwoływania się do zestawów międzyoperacyjnych:

- Osadzone typy międzyoperacyjnych: począwszy od .NET Framework 4 i programu Visual Studio 2010, można wydać kompilatorowi możliwość osadzenia informacji o typie z zestawu międzyoperacyjnego w pliku wykonywalnym. Jest to zalecana technika.

- Wdrażanie zestawów międzyoperacyjnych: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W takim przypadku zestaw międzyoperacyjny musi zostać wdrożony wraz z aplikacją.

 Różnice między tymi dwoma technikami zostały omówione bardziej szczegółowo w temacie [Korzystanie z typów com w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).

 Osadzanie typów międzyoperacyjnych w programie Visual Studio jest zademonstrowane w [przewodniku: osadzanie typów z zestawów zarządzanych w programie Visual Studio](../../standard/assembly/embed-types-visual-studio.md).

 Aby odwołać się do zestawu międzyoperacyjnego przy użyciu kompilatora wiersza polecenia i osadzić informacje o typie w plikach wykonywalnych, użyj [linku (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub przełącznika [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) kompilatora i określ nazwę zestawu międzyoperacyjnego.

> [!NOTE]
> Aplikacje Visual C++ nie mogą osadzić informacji o typie, ale mogą współdziałać z aplikacjami lub dodatkami, które wykonują operacje.

 Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny podczas jego wdrażania, użyj przełącznika kompilatora **/Reference** i określ nazwę zestawu międzyoperacyjnego.

## <a name="see-also"></a>Zobacz też

- [Udostępnianie składników COM programowi.NET Framework](exposing-com-components.md)
- [Niezależność od języka i składniki niezależne od języka](../../standard/language-independence-and-language-independent-components.md)
- [Używanie typów COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Przewodnik: osadzanie typów z zarządzanych zestawów w programie Visual Studio](../../standard/assembly/embed-types-visual-studio.md)
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
