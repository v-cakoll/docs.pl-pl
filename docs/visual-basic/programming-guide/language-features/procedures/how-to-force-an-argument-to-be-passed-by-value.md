---
title: 'Instrukcje: Wymuszanie argumentu być przekazywany przez wartość (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 497ae11b858b7d164ba3b5607ff2109254a154de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842048"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Instrukcje: Wymuszanie argumentu być przekazywany przez wartość (Visual Basic)
Deklaracja procedury określa mechanizm przekazywania. Jeśli parametr jest zadeklarowana [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic oczekuje przekazywania odpowiadający argument odwołania. Dzięki temu procedurę, aby zmienić wartość elementu programistycznego, bazowy argumentu w wywoływanym kodzie. Jeśli chcesz chronić element podstawowy względem takie zmiany, można zastąpić `ByRef` wywołać mechanizm przekazywania w procedurze, umieszczając nazwę argumentu w nawiasach. Te nawiasy w niniejszym dokumencie stanowią nawiasów otaczający listę argumentów w wywołaniu.  
  
 Nie można przesłonić, kod wywołujący [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanizm.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Aby wymusić argument jest przekazywany przez wartość  
  
-   Jeżeli zadeklarowano odpowiadającego mu parametru `ByVal` w procedurze jest konieczne wykonanie żadnych dodatkowych czynności. Visual Basic już oczekuje do przekazywania argumentu przez wartość.  
  
-   Jeżeli zadeklarowano odpowiadającego mu parametru `ByRef` w procedurze, należy ująć argument w nawiasach w wywołaniu procedury.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zastępuje `ByRef` deklaracji parametru. W wywołaniu, która wymusza `ByVal`, należy pamiętać, dwa poziomy nawiasów.  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 Gdy `str` jest ujęty w nawiasy dodatkowe w liście argumentów `setNewString` procedury nie można zmienić jego wartość w wywoływanym kodzie i `MsgBox` Wyświetla, "nie można zastąpić, jeśli przekazany ByVal". Gdy `str` nie jest ujęty w nawiasy dodatkowe procedury można go zmienić, i `MsgBox` Wyświetla "Jest nową wartość dla argumentu inString".  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Jeśli zmienna jest przekazywane przez odwołanie, musisz użyć `ByRef` — słowo kluczowe, aby określić, ten mechanizm.  
  
 Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości. Jednak dobrą praktyką, aby uwzględnić albo programowania jest [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe z każdym zadeklarowany parametr. Dzięki temu można łatwiej odczytać kodu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli procedura deklaruje parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), poprawna wykonania kodu może zależeć od możliwości zmienić element podstawowy w wywoływanym kodzie. Jeśli kod wywołujący zastępuje ten mechanizm wywołania, umieszczając argument w nawiasach lub przekazuje argument niemodyfikowalnymi, procedury nie można zmienić elementu bazowego. Może to dawać nieoczekiwane wyniki w wywoływanym kodzie.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Z zezwoleniem na procedury zmienić wartość argumentu w wywoływanym kodzie bazowego zawsze to potencjalne zagrożenie. Upewnij się, że oczekiwane tę wartość można zmienić i przygotowywane do sprawdzania poprawności, przed jego użyciem.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Instrukcje: Zmień wartość argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: Chronienie argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
