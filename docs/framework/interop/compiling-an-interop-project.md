---
title: "Kompilowanie projektu międzyoperacyjnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc541911670c533caa97c645085ad09bde5eefdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="compiling-an-interop-project"></a>Kompilowanie projektu międzyoperacyjnego
COM interop projektów, odwołujące się do jednego lub więcej zestawów zawierających importowanych typów COM są kompilowane jak zarządzanego projektu. Możesz odwoływać się do zestawów międzyoperacyjnych w środowisku programowania, takiego jak Visual Studio, lub możesz odwoływać się do ich używania kompilatora wiersza polecenia. W obu przypadkach skompilować poprawnie, zestawu międzyoperacyjnego musi być w tym samym katalogu co plik projektu.  
  
 Istnieją dwa sposoby odwołania zestawów międzyoperacyjnych:  
  
-   Osadzone typy współdziałania: począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] i [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], można nakazać kompilatorowi osadzanie informacji o typie z zestawu międzyoperacyjnego do pliku wykonywalnego. Jest to zalecana technika.  
  
-   Zestawy międzyoperacyjne wdrażania: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W takim przypadku należy wdrożyć zestawu międzyoperacyjnego z aplikacją.  
  
 Różnice między te dwie metody omówiono bardziej szczegółowo w [przy użyciu typów COM w kod zarządzany](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).  
  
 Osadzanie typów międzyoperacyjnych z programem Visual Studio jest przedstawiona w [wskazówki: osadzanie informacji o typie z zestawów Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) i [wskazówki: osadzanie typów z zarządzanych zestawów](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Odwołanie do zestawu międzyoperacyjnego z wiersza polecenia kompilatora i osadzanie informacji o typie w Twoje pliki wykonywalne, użyj [/Link (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) przełącznika kompilatora i Określ nazwę zestawu międzyoperacyjnego.  
  
> [!NOTE]
>  Aplikacje programu Visual C++ nie można osadzić typu informacji, ale mogą współdziałać aplikacji lub dodatki, które wykonują.  
  
 Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny po jej wdrożeniu, należy użyć **/reference** kompilatora przełącznika i określ nazwę zestawu międzyoperacyjnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie składników modelu COM aplikacji .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 [Niezależność od języka i elementy niezależne od języka](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [Używanie typów COM w kodzie zarządzanym](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [Wskazówki: Osadzanie typów z zarządzanych zestawów](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [Importowanie biblioteki typów jako zestawu](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
