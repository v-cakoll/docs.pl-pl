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
ms.openlocfilehash: bdaa0351e288b85a3e35818c0f53ef4d772932e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151316"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)
Gdy wywołujesz `Sub` lub `Function` procedury, można przekazać argumenty *według pozycji* — w kolejności, w jakiej są wyświetlane w definicji procedury — lub przekazać je *według nazwy*, bez uwzględniając pozycji.  
  
 Podczas przekazywania argumentu przez nazwę, należy określić argument deklarowana przez nazwę, a następnie dwukropek i znak równości (`:=`), a następnie wartość argumentu. Możesz podać Argumenty nazwane w dowolnej kolejności.  
  
 Na przykład następująca `Sub` procedury przyjmuje trzy argumenty:  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 Po wywołaniu tej procedury, można podać argumentów według pozycji według nazwy lub przy użyciu kombinacji obu.  
  
## <a name="passing-arguments-by-position"></a>Przekazywanie argumentów według pozycji  
 Możesz wywołać `Display` metody z argumentami przekazywane według pozycji i rozdzielone przecinkami, jak pokazano w poniższym przykładzie:  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 Jeżeli pominięto opcjonalny argument na liście argumentów pozycyjnych muszą przechowywać jej miejscu za pomocą przecinka. Poniższy przykład wywołuje `Display` metody bez `age` argumentu:  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>Przekazywanie argumentów według nazwy  
 Ewentualnie możesz wywołać `Display` argumenty przekazywane według nazwy, również rozdzielone przecinkami, jak pokazano w poniższym przykładzie:  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 Przekazywanie argumentów według nazwy w ten sposób jest szczególnie przydatne w przypadku, gdy wywołujesz procedurę, która ma więcej niż jeden opcjonalny argument. Jeśli podasz argumentów według nazwy, ma oznaczają brakujące argumenty pozycyjne przy użyciu następujących po sobie przecinków. Przekazywanie argumentów według nazwy również ułatwia do śledzenia argumentów, które kończy się sukcesem i pomijanie te, które.  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Mieszanie argumentów według pozycji i według nazwy  

Można podać argumentów według pozycji i według nazwy w wywołaniu samą procedurą, jak pokazano w poniższym przykładzie:  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 W powyższym przykładzie nie dodatkowy przecinek jest niezbędne do przechowywania miejsca pominięty `age` argumentu, ponieważ `birth` jest przekazywany przez nazwę.  
  
W wersji programu Visual Basic przed 15.5 podczas podawania argumenty przez kombinację pozycji i nazwy, argumentów pozycyjnych muszą wszystkich umieszczone jako pierwsze. Gdy podasz argument według nazwy, wszelkie pozostałe argumenty muszą wszystkie być przekazywane według nazwy.  Na przykład, następujące wywołanie do `Display` metoda wyświetla błąd kompilatora [BC30241: Oczekiwano argumentu nazwanego](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

Począwszy od wersji 15.5 programu Visual Basic, argumenty pozycyjne wykonać argumenty nazwane jeśli końcowa argumenty pozycyjne są w poprawnej pozycji. Jeśli skompilowany w wersji 15.5 programu Visual Basic, poprzednie wywołanie `Display` metoda pomyślnie wykonuje kompilację i już nie generuje błąd kompilatora [BC30241](../../../misc/bc30241.md).  

Ta możliwość mieszanie i dopasowywanie argumentów nazwanych i pozycyjnych w dowolnej kolejności jest szczególnie przydatne, jeśli chcesz użyć nazwanego argumentu, aby zwiększyć czytelność kodu. Na przykład następująca `Person` konstruktora klasy wymaga dwóch argumentów typu `Person`, które mogą być `Nothing`. 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

Za pomocą mieszanego argumentów nazwanych i pozycyjnych, które ułatwia celem kod, usuń zaznaczenie, gdy wartość `father` i `mother` argumenty są `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

Aby skorzystać z argumentów pozycyjnych z argumentami nazwanego, należy dodać następujący element do projektu języka Visual Basic (\*.vbproj) pliku:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Aby uzyskać więcej informacji, zobacz [ustawienie wersji języka Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Ograniczenia dotyczące podanie argumentów według nazwy  

Nie można przekazywać argumentów według nazwy, aby uniknąć wpisywania wymaganych argumentów. Można pominąć opcjonalne argumenty.  
  
Tablica parametrów nie można przekazać według nazwy. Jest to spowodowane po wywołaniu procedury, podaj nieskończona liczba rozdzielonych przecinkami argumenty tablicą parametrów, a kompilator nie można skojarzyć więcej niż jeden argument nazwą jednego.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Jak: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Parametry opcjonalne](./optional-parameters.md)  
 [Tablice parametrów](./parameter-arrays.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
