---
title: Parameter — Tablice (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: e059f471f78262320f1968c12192de710876aef4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966583"
---
# <a name="parameter-arrays-visual-basic"></a>Parameter — Tablice (Visual Basic)
Zwykle nie można wywołać procedury z więcej argumentów niż określa deklaracja procedury. Jeśli potrzebujesz nieokreśloną liczbę argumentów, można zadeklarować *tablicy parametrów*, co pozwala procedurę, aby zaakceptować tablicy wartości parametru. Nie trzeba znać liczbę elementów w tablicy parametrów podczas definiowania procedury. Rozmiar tablicy jest określana indywidualnie przy każdym wywołaniu procedury.  
  
## <a name="declaring-a-paramarray"></a>Deklarowanie ParamArray  
 Możesz użyć [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) — słowo kluczowe do oznaczania tablicy parametrów na liście parametrów. Mają zastosowanie następujące zasady:  
  
-   Procedurę można zdefiniować tylko jedna Tablica parametrów i musi być ostatnim parametrem w definicji procedury.  
  
-   Tablica parametrów musi być przekazywany przez wartość. Jest dobrą praktyką, aby jawnie dołączyć znak programowania [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) — słowo kluczowe w definicji procedury.  
  
-   Tablica parametrów jest automatycznie opcjonalne. Jego wartość domyślna to puste Jednowymiarowa tablica typu elementu tablicy parametrów.  
  
-   Wszystkie parametry z poprzednich tablicy parametrów musi być wymagane. Tablica parametrów musi być tylko opcjonalny parametr.  
  
## <a name="calling-a-paramarray"></a>Wywoływanie ParamArray  
 Po wywołaniu procedury, która definiuje tablicy parametrów, należy podać argument w jednym z następujących sposobów:  
  
-   Nothing — oznacza to, możesz pominąć [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argumentu. W tym przypadku pusta tablica jest przekazywany do procedury. Można również przekazać [nic](../../../../visual-basic/language-reference/nothing.md) — słowo kluczowe, w tym samym celu.  
  
-   Lista dowolną liczbę argumentów, oddzielonych przecinkami. Typ danych każdego argumentu musi być niejawnie konwertowane na `ParamArray` typ elementu.  
  
-   Tablica z tego samego typu elementu jako typ elementu tablicy parametrów.  
  
 We wszystkich przypadkach kodu w ramach procedury traktuje tablicy parametrów jako tablicę jednowymiarową za pomocą elementów tego samego typu danych, co `ParamArray` typu danych.  
  
> [!IMPORTANT]
>  Zawsze, gdy użytkownik poradzić sobie z tablicy, które mogą być duże przez czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrznych wydajności aplikacji. Jeśli zdecydujesz się zaakceptować tablicy parametrów, należy sprawdzić rozmiar tablicy, która przekazany kod wywołujący. Wykonaj kroki odpowiednie, jeśli jest zbyt duży dla aplikacji. Aby uzyskać więcej informacji, zobacz [tablic](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje i wywołuje funkcję `calcSum`. `ParamArray` Modyfikator parametru `args` włącza funkcję zaakceptować zmienną liczbę argumentów.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 Poniższy przykład definiuje procedurę z tablicą parametrów i wyświetla wartości wszystkie elementy tablicy przekazane do tablicy parametrów.  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
