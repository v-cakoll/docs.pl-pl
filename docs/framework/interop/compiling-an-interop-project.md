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
ms.openlocfilehash: 4369ce9c9ce82ecdbf11d76f3b043778b8374d8b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489755"
---
# <a name="compiling-an-interop-project"></a>Kompilowanie projektu międzyoperacyjnego

COM projektów międzyoperacyjnych, które odwołują się jeden lub więcej zestawów, zawierające zaimportowane typy modelu COM są kompilowane takich jak zarządzanego projektu. Możesz odwoływać się do zestawów międzyoperacyjnych w środowisku programowania, takiego jak Visual Studio lub można się odwołać je korzystając z wiersza polecenia kompilatora. W obu przypadkach aby skompilować poprawnie, zestaw międzyoperacyjny musi być w tym samym katalogu co innych plików projektów.

 Istnieją dwa sposoby, aby odwoływać się do zestawów międzyoperacyjnych:

- Osadzone typy międzyoperacyjne: Począwszy od programu .NET Framework 4 i Visual Studio 2010, można nakazać kompilatorowi do osadzenia informacji o typie z zestawu międzyoperacyjnego, w programie wykonywalnym. Jest to zalecana technika.

- Wdrażanie zestawów międzyoperacyjnych: Można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W tym przypadku zestaw międzyoperacyjny musi zostać wdrożony z aplikacją.

 Różnice między te dwie metody zostały omówione bardziej szczegółowo w [przy użyciu typów modelu COM w kodzie zarządzany](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).

 Osadzanie typów międzyoperacyjnych z programem Visual Studio została przedstawiona w [instruktażu: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), i [instruktażu: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).

 Aby odwoływać się do zestawu międzyoperacyjnego, za pomocą kompilatora wiersza polecenia i osadzić informacje o typie w swoje pliki wykonywalne, użyj [/Link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) przełącznika kompilatora i Określ nazwę zestawu międzyoperacyjnego.

> [!NOTE]
> Aplikacje programu Visual C++ nie można osadzić informacje o typie, ale mogą współdziałać aplikacji lub dodatki, które wykonują.

 Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny, gdy aplikacja jest wdrożona, użyj **/reference** kompilatora przełącznika i określ nazwę zestawu międzyoperacyjnego.

## <a name="see-also"></a>Zobacz także

- [Udostępnianie składników COM programowi .NET Framework](exposing-com-components.md)
- [Niezależność od języka i składniki niezależne od języka](../../standard/language-independence-and-language-independent-components.md)
- [Używanie typów modelu COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
