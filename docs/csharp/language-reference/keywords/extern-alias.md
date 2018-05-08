---
title: extern alias (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: a2803d09ee64af854cad352f6a158fb84bb6d410
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [Słowa kluczowe przestrzeni nazw](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [::, operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [/ Reference (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
