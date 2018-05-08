---
title: Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49e313b2d5aa8302ea4b99e643e09f7b43659785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)
Podczas wywoływania `Sub` lub `Function` procedury, można przekazywać argumenty *według położenia* — w kolejności, w jakiej występują w definicji procedury — lub można przekazać *według nazwy*, bez w odniesieniu do pozycji.  
  
 Jeśli argument według nazw, określ argument deklarowana przez nazwę dwukropek i znak równości (`:=`), a następnie wartość argumentu. Możesz podać Argumenty nazwane w dowolnej kolejności.  
  
 Na przykład następująca `Sub` procedury przyjmuje trzy argumenty:  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 Podczas wywoływania tej procedury, można podać argumentów według pozycji, według nazwy lub za pomocą ich kombinacjami.  
  
## <a name="passing-arguments-by-position"></a>Przekazywanie argumentów według pozycji  
 Możesz wywołać `Display` metody z argumentami przekazywane według pozycji i rozdzielonych przecinkami, jak pokazano w poniższym przykładzie:  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 W przypadku pominięcia opcjonalny argument w postaci listy argument pozycyjny, musi posiadać zamiast niej użyć przecinka. Następujące przykładowe wywołania `Display` metody bez `age` argumentu:  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>Przekazywanie argumentów według nazwy  
 Alternatywnie możesz wywołać `Display` argumentów przekazywane według nazw, również rozdzielonych przecinkami, jak pokazano w poniższym przykładzie:  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 Przekazywanie argumentów według nazwy w ten sposób jest szczególnie przydatna podczas wywoływania procedury, która ma więcej niż jeden argument opcjonalny. Należy podać argumenty według nazwy, nie trzeba używać przecinków kolejnych oznaczający brak argumenty pozycyjne. Przekazywanie argumentów według nazwy również ułatwia do śledzenia argumenty, które są przekazywane i które pominięcie.  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Mieszanie argumentów według pozycji i według nazwy  

Można podać argumenty zarówno według pozycji i według nazwy w wywołaniu procedury pojedynczego, jak pokazano w poniższym przykładzie:  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 W powyższym przykładzie nie dodatkowy przecinek jest niezbędne do przechowywania miejsca pominięcia `age` argumentu, ponieważ `birth` jest przekazywana przez nazwę.  
  
W wersjach programu Visual Basic przed 15,5 cala gdy podać argumenty mieszaniną pozycji i nazwy, argumenty pozycyjne musi wszystkie znajdować na pierwszym. Po podasz argument według nazwy, wszystkie pozostałe argumenty muszą wszystkie być przekazywane przez nazwę.  Na przykład następujące wywołanie do `Display` metoda wyświetla błąd kompilatora [BC30241: nazwany argument, oczekiwano](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

Począwszy od programu Visual Basic 15,5 cala argumenty pozycyjne można wykonać nazwanych argumentów Jeśli końcowy argumenty pozycyjne są w poprawnej pozycji. Jeśli skompilowany w obszarze 15,5 cala Visual Basic, poprzedniego wywołania `Display` metoda kompiluje pomyślnie i już nie generuje błąd kompilatora [BC30241](../../../misc/bc30241.md).  

Ta możliwość mieszać i dopasowywać argumentów nazwanych i pozycyjnych w dowolnej kolejności jest szczególnie przydatne, jeśli chcesz użyć nazwanego argumentu, aby zwiększyć czytelność kodu. Na przykład następująca `Person` Konstruktor klasy wymaga dwóch argumentów typu `Person`, które mogą być `Nothing`. 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

Przy użyciu mieszanych argumentów nazwanych i pozycyjnych ułatwia celem kod wyczyścić, gdy wartość `father` i `mother` argumentów jest `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

Aby wykonać argumenty pozycyjne z argumentami nazwanymi, należy dodać następujący element do projekt programu Visual Basic (\*.vbproj) plików:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a>Ograniczenia dotyczące określenie argumentów według nazwy  

Nie można przekazywać argumentów przez nazwę, aby uniknąć wprowadzenia wymaganych argumentów. Można pominąć tylko argumenty opcjonalne.  
  
Tablica parametrów nie można przekazać według nazwy. To dlatego po wywołaniu procedury, podaj nieokreśloną liczbę rozdzielone przecinkami argumenty dla tablicy parametrów, a kompilator nie można skojarzyć więcej niż jeden argument pod jedną nazwą.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Parametry opcjonalne](./optional-parameters.md)  
 [Tablice parametrów](./parameter-arrays.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
