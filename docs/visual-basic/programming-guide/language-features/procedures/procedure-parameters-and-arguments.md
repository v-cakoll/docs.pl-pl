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
ms.openlocfilehash: b0ab186945b456d7fb4dde3f52724b08a99e2827
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Parametry i argumenty procedur (Visual Basic)
W większości przypadków procedury potrzebuje pewnych informacji o okoliczności, w których została wywołana. Procedury, która wykonuje zadania wielokrotnego lub udostępnionego używa różne informacje dla każdego wywołania. Te informacje składa się z zmienne, stałe i wyrażeń, które przekazujesz do procedury po jej wywołaniu.  
  
 A *parametr* reprezentuje wartość, która procedura oczekuje podania po jej wywołaniu. Deklaracja procedury definiuje jego parametrów.  
  
 Można zdefiniować procedury z żadnych parametrów, jeden parametr lub więcej niż jeden. Nazywa się częścią definicji procedury, która określa parametry *listy parametrów*.  
  
 *Argument* reprezentuje należy podać wartość parametru procedury po wywołaniu procedury. Kod wywołujący zawiera argumenty, gdy wywołuje procedurę. Część wywołaniu procedury, która określa argumenty jest nazywany *listy argumentów*.  
  
 Na poniższej ilustracji przedstawiono wywołującego procedurę `safeSquareRoot` w dwóch różnych miejscach. Pierwsze wywołanie przekazuje wartość zmiennej `x` (4.0) do parametru `number`, a wartość zwracana w `root` (2.0) jest przypisany do zmiennej `y`. Drugie wywołanie przekazuje wartość literału 9.0 do `number`i przypisuje wartość zwrotna (3.0) do zmiennej `z`.  
  
 ![Przekazywanie argumentów do parametru graficzny diagram](./media/parametersargue.gif "ParametersArgue")  
Przekazywanie argumentów do parametru  
  
 Aby uzyskać więcej informacji, zobacz [różnice pomiędzy parametrami i argumentami](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Typ danych parametru  
 Definiowanie typu danych dla parametru za pomocą `As` klauzuli w jego deklaracji. Na przykład następująca funkcja akceptuje string i integer.  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 Jeśli sprawdzanie typu przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off,` `As` klauzuli jest opcjonalny, z wyjątkiem tego, że wszystkie jeden parametr używa go, wszystkie parametry muszą używać. Jeśli sprawdzanie, czy typ jest `On`, `As` klauzula jest wymagana dla wszystkich parametrów procedury.  
  
 Jeśli kod wywołujący oczekuje, że takie jak podać argument o typie danych innym niż odpowiadającego mu parametru `Byte` do `String` parametru, wykonaj jedną z następujących czynności:  
  
-   Podaj tylko argumenty typów danych, które poszerzyć na typ danych parametru;  
  
-   Ustaw `Option Strict Off` umożliwiają niejawnej konwersji zawężającej; lub  
  
-   Użyj słowa kluczowego konwersji, aby jawnie przekonwertować na typ danych.  
  
### <a name="type-parameters"></a>Parametry typów  
 A *ogólnego procedury* definiuje także co najmniej jeden *parametry typu* oprócz jego normalnej parametrów. Procedury ogólne umożliwia kod wywołujący do przekazania różne typy danych zawsze wywołuje procedurę, więc można dostosować typy danych do każdego wywołania poszczególnych wymagań. Zobacz [procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Sub, procedury](./sub-procedures.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Instrukcje: definiowanie parametru dla procedury](./how-to-define-a-parameter-for-a-procedure.md)  
 [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
