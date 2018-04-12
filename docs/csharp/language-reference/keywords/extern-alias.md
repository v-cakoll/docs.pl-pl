---
title: extern alias (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e995586c08659853538726a12679770cd1ada37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="extern-alias-c-reference"></a>extern alias (odwołanie w C#)
Może być konieczne dwie wersje zestawy takich samych nazwach w pełni kwalifikowanego typu odwołania. Może być konieczne na przykład użyć dwóch lub więcej wersji zestawu w tej samej aplikacji. Za pomocą aliasu zewnętrznego zestawu, przestrzeni nazw z każdego zestawu można ich opakować wewnątrz przestrzeni nazw poziomu głównego o nazwie aliasu, co umożliwia ich do użycia w tym samym pliku.  
  
> [!NOTE]
>  [Extern](../../../csharp/language-reference/keywords/extern.md) — słowo kluczowe jest również używany jako modyfikator metody, deklarowanie metody zapisane za pomocą kodu niezarządzanego.  
  
 Aby odwołać się do dwóch zestawów pod tą samą nazwą w pełni kwalifikowanego typu aliasu musi być określona w wierszu polecenia, w następujący sposób:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Spowoduje to utworzenie aliasów zewnętrznych `GridV1` i `GridV2`. Aby korzystać z tych aliasy w programie, odwoływać je za pomocą `extern` — słowo kluczowe. Na przykład:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Każdy extern alias deklaracji wprowadzono dodatkowe nazw poziomu głównego, który równoleżnikami (ale nie znajduje się w obrębie) globalnej przestrzeni nazw. W związku z tym typów z każdego zestawu może być określone bez niejednoznaczności przy użyciu ich w pełni kwalifikowanej nazwy, umieszczone w odpowiednich alias przestrzeni nazw.  
  
 W poprzednim przykładzie `GridV1::Grid` byłoby formantu siatki z `grid.dll`, i `GridV2::Grid` byłoby formantu siatki z `grid20.dll`.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe Namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [:: — Operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [/ Reference (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
