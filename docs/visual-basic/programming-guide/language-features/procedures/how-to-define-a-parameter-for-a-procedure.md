---
title: 'Instrukcje: Definiowanie parametru dla procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 55925b0f007b1be2f5d46ffc0854601f483b2e2d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333837"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Instrukcje: Definiowanie parametru dla procedury (Visual Basic)
A *parametru* umożliwia kod wywołujący, aby przekazać wartości do procedury, gdy wywoływanych przez nią. Możesz zadeklarować każdego parametru dla procedury taki sam sposób, jak zadeklarować zmienną, określając jej nazwę i typ danych. Możesz również określić mechanizm przekazywania, i czy parametr jest opcjonalny.  
  
 Aby uzyskać więcej informacji, zobacz [parametry i argumenty procedur](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Aby zdefiniować parametr procedury  
  
1. W deklaracji procedury Dodaj nazwę parametru do listy parametrów procedury, oddzielając od innych parametrów przecinkami.  
  
2. Zdecyduj, typ danych parametru.  
  
3. Postępuj zgodnie z nazwą parametru `As` klauzuli, aby określić typ danych.  
  
4. Zdecyduj, mechanizm przekazywania, dla parametru. Zwykle należy podać parametr według wartości, chyba że chcesz procedury, aby można było zmienić jego wartość w wywoływanym kodzie.  
  
5. Poprzedź nazwę parametru za pomocą [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) Aby określić mechanizm przekazywania. Aby uzyskać więcej informacji, zobacz [różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6. Jeśli parametr jest opcjonalny, poprzedź mechanizm przekazywania za pomocą [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) i postępuj zgodnie z typem danych parametru znakiem równości (`=`) i wartość domyślną.  
  
     W poniższym przykładzie zdefiniowano konturu `Sub` procedury z trzech parametrów. Pierwsze dwa są wymagane, a trzeci jest opcjonalne. Deklaracji parametrów są rozdzielone na liście parametrów przecinkami.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     Pierwszy parametr akceptuje `customer` obiektu i `updateCustomer` bezpośrednio zaktualizować zmienną do `c` ponieważ argument jest przekazywany [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Procedury nie można zmienić wartości dwa ostatnie argumenty, ponieważ są one przekazywane [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Jeśli kod wywołujący nie dostarcza wartość `level` parametru, Visual Basic ustawia ją na wartość domyślna 0.  
  
     Jeśli kontrola typów w przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off`, `As` klauzula jest opcjonalny podczas definiowania parametru. Jednakże jeśli korzysta z żadnych jeden parametr `As` klauzuli wszystkich z nich należy użyć go. Jeśli typ sprawdzania przełącznika `On`, `As` klauzula jest wymagana dla każdej definicji parametru.  
  
     Określanie typów danych dla wszystkich elementów programowania jest znany jako *silne wpisywanie*. Po ustawieniu `Option Strict On`, Visual Basic wymusza silne wpisywanie. Jest to zdecydowanie zalecane, z następujących powodów:  
  
    -   Umożliwia obsługę funkcji IntelliSense dla zmiennych i parametrów. Dzięki temu można zobaczyć ich właściwości i inne elementy członkowskie podczas wpisywania w kodzie.  
  
    -   Umożliwia kompilatorowi wykonywanie sprawdzania typu. Dzięki temu catch, instrukcje, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienia. Przechwytuje także wywołania metod, na obiektach, które nie obsługują je.  
  
    -   Powoduje ona szybsze wykonywanie Twojego kodu. Co dzieje się, jeśli nie określisz typ danych dla elementu programistycznego, kompilator Visual Basic przypisuje mu `Object` typu. Skompilowany kod może być konieczne konwersji do i z powrotem między `Object` a innymi typami danych, które powoduje zmniejszenie wydajności.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Instrukcje: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)
