---
title: 'Porady: definiowanie parametru dla procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 411959a7be92ea49a59558b508e992bfba8eff95
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344884"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Porady: definiowanie parametru dla procedury (Visual Basic)
*Parametr* pozwala wywołującemu kod przekazać wartość do procedury, gdy wywołuje ją. Należy zadeklarować każdy parametr dla procedury w taki sam sposób, w jaki deklarujesz zmienną, określając jej nazwę i typ danych. Określany jest również mechanizm przekazywania oraz określa, czy parametr jest opcjonalny.  
  
 Aby uzyskać więcej informacji, zobacz [parametry procedury i argumenty](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Aby zdefiniować parametr procedury  
  
1. W deklaracji procedury Dodaj nazwę parametru do listy parametrów procedury, oddzielając ją od innych parametrów przecinkami.  
  
2. Wybierz typ danych parametru.  
  
3. Aby określić typ danych, postępuj zgodnie z nazwą parametru z klauzulą `As`.  
  
4. Zdecyduj, który mechanizm przekazywania ma być dla parametru. Zwykle przekazujesz parametr według wartości, chyba że chcesz, aby procedura mogła zmienić jej wartość w kodzie wywołującym.  
  
5. Poprzedź nazwę parametru poleceniem [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) , aby określić mechanizm przekazywania. Aby uzyskać więcej informacji, zobacz [różnice między przekazywaniem argumentu według wartości i przez odwołanie](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6. Jeśli parametr jest opcjonalny, należy poprzedzić mechanizm przekazywania [opcjonalnym](../../../../visual-basic/language-reference/modifiers/optional.md) i postępować według typu danych parametru z znakiem równości (`=`) i wartością domyślną.  
  
     W poniższym przykładzie zdefiniowano kontur procedury `Sub` z trzema parametrami. Pierwsze dwa są wymagane, a trzeci jest opcjonalny. Deklaracje parametrów są oddzielane do listy parametrów przecinkami.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     Pierwszy parametr akceptuje obiekt `customer`, a `updateCustomer` może bezpośrednio zaktualizować zmienną przekazaną do `c`, ponieważ argument jest przenoszona jako [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Procedura nie może zmienić wartości dwóch ostatnich argumentów, ponieważ są one przenoszone przez [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Jeśli wywołujący kod nie poda wartości dla parametru `level`, Visual Basic ustawi ją na wartość domyślną 0.  
  
     Jeśli przełącznik sprawdzania typu ([instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off`, klauzula `As` jest opcjonalna przy definiowaniu parametru. Jeśli jednak którykolwiek z parametrów używa klauzuli `As`, wszystkie muszą z nich korzystać. Jeśli przełącznik sprawdzania typu jest `On`, klauzula `As` jest wymagana dla każdej definicji parametru.  
  
     Określanie typów danych dla wszystkich elementów programistycznych jest znane jako *silne wpisywanie*. Po ustawieniu `Option Strict On`, Visual Basic wymusza silne wpisywanie. Jest to zdecydowanie zalecane z następujących powodów:  
  
    - Umożliwia obsługę technologii IntelliSense dla zmiennych i parametrów. Dzięki temu można zobaczyć swoje właściwości i innych członków podczas wpisywania kodu w kodzie.  
  
    - Umożliwia kompilatorowi wykonywanie kontroli typu. Ułatwia to wychwycenie instrukcji, które mogą zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienie. Przechwytuje również wywołania metod na obiektach, które ich nie obsługują.  
  
    - Skutkuje to przyspieszeniem wykonywania kodu. Jedną z przyczyn tego problemu jest to, że jeśli nie określisz typu danych dla elementu programistycznego, kompilator Visual Basic przypisze `Object` typ. Skompilowany kod może wymagać konwersji z powrotem między `Object` i innymi typami danych, co zmniejsza wydajność.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)
