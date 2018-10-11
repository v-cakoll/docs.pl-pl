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
ms.openlocfilehash: 7088c7f7765f0c5cfc4d6151dcda6f57b8de10d2
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086651"
---
# <a name="compiling-an-interop-project"></a>Kompilowanie projektu międzyoperacyjnego

COM projektów międzyoperacyjnych, które odwołują się jeden lub więcej zestawów, zawierające zaimportowane typy modelu COM są kompilowane takich jak zarządzanego projektu. Możesz odwoływać się do zestawów międzyoperacyjnych w środowisku programowania, takiego jak Visual Studio lub można się odwołać je korzystając z wiersza polecenia kompilatora. W obu przypadkach aby skompilować poprawnie, zestaw międzyoperacyjny musi być w tym samym katalogu co innych plików projektów.

 Istnieją dwa sposoby, aby odwoływać się do zestawów międzyoperacyjnych:

-   Osadzone typy współdziałania: począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] i Visual Studio 2010, można nakazać kompilatorowi osadzanie informacji o typie z zestawu międzyoperacyjnego, w programie wykonywalnym. Jest to zalecana technika.

-   Wdrażanie zestawów międzyoperacyjnych: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W tym przypadku zestaw międzyoperacyjny musi zostać wdrożony z aplikacją.

 Różnice między te dwie metody zostały omówione bardziej szczegółowo w [przy użyciu typów modelu COM w kodzie zarządzany](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).

 Osadzanie typów międzyoperacyjnych z programem Visual Studio została przedstawiona w [wskazówki: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) i [wskazówki: osadzanie typów z zarządzanych zestawów](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).

 Aby odwoływać się do zestawu międzyoperacyjnego, za pomocą kompilatora wiersza polecenia i osadzić informacje o typie w swoje pliki wykonywalne, użyj [/Link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) przełącznika kompilatora i Określ nazwę zestawu międzyoperacyjnego.

> [!NOTE]
> Aplikacje programu Visual C++ nie można osadzić informacje o typie, ale mogą współdziałać aplikacji lub dodatki, które wykonują.

 Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny, gdy aplikacja jest wdrożona, użyj **/reference** kompilatora przełącznika i określ nazwę zestawu międzyoperacyjnego.

## <a name="see-also"></a>Zobacz też

- [Udostępnianie składników COM programowi .NET Framework](exposing-com-components.md)
- [Niezależność od języka i składniki niezależne od języka](../../standard/language-independence-and-language-independent-components.md)
- [Używanie typów modelu COM w kodzie zarządzanym](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))
- [Przewodnik: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))
- [Przewodnik: osadzanie typów z zarządzanych zestawów](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)