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
ms.openlocfilehash: 8a6099764fb98604726da99ef71b9c82e9a931bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiling-an-interop-project"></a>Kompilowanie projektu międzyoperacyjnego
COM interop projektów, odwołujące się do jednego lub więcej zestawów zawierających importowanych typów COM są kompilowane jak zarządzanego projektu. Możesz odwoływać się do zestawów międzyoperacyjnych w środowisku programowania, takiego jak Visual Studio, lub możesz odwoływać się do ich używania kompilatora wiersza polecenia. W obu przypadkach skompilować poprawnie, zestawu międzyoperacyjnego musi być w tym samym katalogu co plik projektu.  
  
 Istnieją dwa sposoby odwołania zestawów międzyoperacyjnych:  
  
-   Osadzone typy współdziałania: począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] i [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], można nakazać kompilatorowi osadzanie informacji o typie z zestawu międzyoperacyjnego do pliku wykonywalnego. Jest to zalecana technika.  
  
-   Zestawy międzyoperacyjne wdrażania: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W takim przypadku należy wdrożyć zestawu międzyoperacyjnego z aplikacją.  
  
 Różnice między te dwie metody omówiono bardziej szczegółowo w [przy użyciu typów COM w kod zarządzany](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).  
  
 Osadzanie typów międzyoperacyjnych z programem Visual Studio jest przedstawiona w [wskazówki: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) i [wskazówki: osadzanie typów z zarządzanych zestawów](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Odwołanie do zestawu międzyoperacyjnego z wiersza polecenia kompilatora i osadzanie informacji o typie w Twoje pliki wykonywalne, użyj [/Link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) przełącznika kompilatora i Określ nazwę zestawu międzyoperacyjnego.  
  
> [!NOTE]
>  Aplikacje programu Visual C++ nie można osadzić typu informacji, ale mogą współdziałać aplikacji lub dodatki, które wykonują.  
  
 Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny po jej wdrożeniu, należy użyć **/reference** kompilatora przełącznika i określ nazwę zestawu międzyoperacyjnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie składników COM programowi .NET Framework](exposing-com-components.md)  
 [Niezależność od języka i składniki niezależne od języka](../../standard/language-independence-and-language-independent-components.md)  
 [Używanie typów COM w kodzie zarządzanym](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
 [Przewodnik: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))  
 [Przewodnik: osadzanie typów z zarządzanych zestawów](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
