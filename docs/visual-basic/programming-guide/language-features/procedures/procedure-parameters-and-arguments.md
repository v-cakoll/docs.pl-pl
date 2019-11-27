---
title: Parametry i argumenty procedur
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 7dfbbcb39cf7bb05c8a62a7a252e425f287c9a09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352581"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Parametry i argumenty procedur (Visual Basic)
W większości przypadków procedura wymaga pewnych informacji na temat okoliczności, w których został wywołany. Procedura wykonująca powtarzalne lub udostępnione zadania używa różnych informacji dla każdego wywołania. Te informacje składają się ze zmiennych, stałych i wyrażeń, które są przekazywane do procedury po jej wywołaniu.  
  
 *Parametr* reprezentuje wartość, którą procedura oczekuje na dostarczenie podczas jego wywoływania. Deklaracja procedury definiuje jej parametry.  
  
 Można zdefiniować procedurę bez parametrów, jednego parametru lub więcej niż jeden. Część definicji procedury, która określa parametry jest nazywana *listą parametrów*.  
  
 *Argument* reprezentuje wartość dostarczaną do parametru procedury po wywołaniu procedury. Kod wywołujący dostarcza argumenty, gdy wywołuje procedurę. Część wywołania procedury, która określa argumenty jest nazywana *listą argumentów*.  
  
 Poniższa ilustracja przedstawia kod wywołujący procedurę `safeSquareRoot` z dwóch różnych miejsc. Pierwsze wywołanie przekazuje wartość zmiennej `x` (4,0) do `number`parametru, a wartość zwracana w `root` (2,0) jest przypisana do zmiennej `y`. Drugie wywołanie przekazuje wartość literału 9,0 do `number`i przypisuje wartość zwracaną (3,0) do zmiennej `z`.  
  
 ![Diagram, który pokazuje przekazywanie argumentu do parametru](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 Aby uzyskać więcej informacji, zobacz [różnice między parametrami i argumentami](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Typ danych parametru  
 Zdefiniowano typ danych dla parametru za pomocą klauzuli `As` w swojej deklaracji. Na przykład następująca funkcja akceptuje ciąg i liczbę całkowitą.  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 Jeśli przełącznik sprawdzania typu ([instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off,` klauzula `As` jest opcjonalna, z tą różnicą, że jeśli którykolwiek z nich używa tego parametru, wszystkie parametry muszą go używać. Jeśli sprawdzanie typu jest `On`, klauzula `As` jest wymagana dla wszystkich parametrów procedury.  
  
 Jeśli kod wywołujący oczekuje argumentu z typem danych innym niż odpowiedni parametr, taki jak `Byte` do parametru `String`, musi wykonać jedną z następujących czynności:  
  
- Dostarczaj tylko argumenty z typami danych, które rozszerzają się do typu danych parametru;  
  
- Ustaw `Option Strict Off`, aby zezwalać na niejawne konwersje zawężające; oraz  
  
- Użyj słowa kluczowego konwersji, aby jawnie skonwertować typ danych.  
  
### <a name="type-parameters"></a>Parametry typów  
 *Procedura ogólna* definiuje także jeden lub więcej *parametrów typu* oprócz zwykłych parametrów. Procedura ogólna pozwala wywołującemu kod przekazać różne typy danych przy każdym wywołaniu procedury, tak aby można było dostosować typy danych do wymagań poszczególnych wywołań. Zapoznaj [się z procedurami ogólnymi w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie parametru dla procedury](./how-to-define-a-parameter-for-a-procedure.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
