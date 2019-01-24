---
title: Parametry i argumenty procedur (Visual Basic)
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
ms.openlocfilehash: 42f85ed98f399c96f89879129b085f25ab117096
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731741"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Parametry i argumenty procedur (Visual Basic)
W większości przypadków procedura potrzebuje pewnych informacji o sytuacjach, w których została wywołana. Procedura, która wykonuje zadania powtórzonych lub udostępnione używa różne informacje dla każdego wywołania. Ten zawiera zmienne, stałe i wyrażeń, które przekazujesz do procedury, gdy wywołujesz ją.  
  
 A *parametr* reprezentuje wartość, która oczekuje procedury, trzeba będzie podać podczas jego wywoływania. Deklaracja procedury definiuje jego parametrów.  
  
 Można zdefiniować procedurę z bez parametrów, jeden parametr lub więcej niż jeden. Nazywa się częścią definicji procedury, która określa parametry *listy parametrów*.  
  
 *Argument* reprezentuje wartość, należy podać parametr procedury po wywołaniu procedury. Kod wywołujący dostarcza argumentów, gdy wywołuje procedurę. Część po wywołaniu procedury, która określa argumenty nosi nazwę *listy argumentów*.  
  
 Na poniższej ilustracji przedstawiono kodu wywołującego procedurę `safeSquareRoot` w dwóch różnych miejscach. Pierwsze wywołanie przekazuje wartość zmiennej `x` (4.0) do parametru `number`i wartość zwracana w `root` (2.0) jest przypisany do zmiennej `y`. Drugie wywołanie przekazuje wartość literału 9.0 do `number`, a następnie przypisuje wartość zwracaną (3.0) do zmiennej `z`.  
  
 ![Przekazywanie argumentów do parametrów graficzny diagram](./media/parametersargue.gif "ParametersArgue")  
Przekazywanie argumentu do parametru  
  
 Aby uzyskać więcej informacji, zobacz [różnice pomiędzy parametrami i argumentami](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Typ danych parametru  
 Zdefiniuj typ danych parametru za pomocą `As` klauzuli w jego deklaracji. Na przykład następująca funkcja akceptuje string i integer.  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 Jeśli kontrola typów w przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off,` `As` klauzula jest opcjonalne, z tą różnicą, że wszelkie jeden parametr używa go, wszystkie parametry muszą używać. W przypadku sprawdzania typu `On`, `As` klauzula jest wymagana dla wszystkich parametrów procedury.  
  
 Jeśli kod wywołujący oczekuje, że takie jak podać argument o typie danych innym niż odpowiadającego mu parametru `Byte` do `String` parametru, wykonaj jedną z następujących czynności:  
  
-   Podaj tylko argumenty z typami danych, które mogą zostać poszerzone do do typu parametru.  
  
-   Ustaw `Option Strict Off` umożliwia niejawne konwersje zawężające; lub  
  
-   Użyj słowa kluczowego konwersji można jawnie przekonwertować na typ danych.  
  
### <a name="type-parameters"></a>Parametry typów  
 A *ogólna procedura* definiuje także co najmniej jeden *parametry typu* oprócz normalnych parametry. Ogólna procedura pozwala kod wywołujący, aby przekazać zawsze wywołuje procedurę, dzięki czemu można dostosować, typy danych do wymagań poszczególnych wywołań różnych typów danych. Zobacz [procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: Definiowanie parametru dla procedury](./how-to-define-a-parameter-for-a-procedure.md)
- [Instrukcje: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
