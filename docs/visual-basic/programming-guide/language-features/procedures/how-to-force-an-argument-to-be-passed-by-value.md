---
title: 'Porady: wymuszanie przekazywania argumentu przez wartość (Visual Basic)'
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
ms.openlocfilehash: adc58c34150030eb0fc82050576bfecc453e21ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Porady: wymuszanie przekazywania argumentu przez wartość (Visual Basic)
Deklaracja procedury określa mechanizm przekazywania. Jeśli parametr jest zadeklarowany jako [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic oczekuje, że odpowiedni argument jest przekazywany za pomocą odwołania. Dzięki temu procedury zmienić wartość elementu programistycznego bazowy argumentu w wywoływanym kodzie. Jeśli chcesz chronić odpowiedniego elementu na takie zmiany, można zastąpić `ByRef` mechanizm przekazywania w procedurze wywołać umieszczając Nazwa argumentu w nawiasach. Te nawiasy są oprócz nawiasów otaczającej listy argumentów w wywołaniu.  
  
 Nie można zastąpić kod wywołujący [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanizmu.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Aby wymusić argument przekazywany przez wartość  
  
-   Jeżeli zadeklarowano odpowiadającego mu parametru `ByVal` w procedurze, nie trzeba wykonać dodatkowe czynności. Visual Basic już oczekuje do przekazywania argumentu przez wartość.  
  
-   Jeżeli zadeklarowano odpowiadającego mu parametru `ByRef` w procedurze, ujmij argument w nawiasach w wywołaniu procedury.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zastępuje `ByRef` deklaracji parametru. W wywołaniu, która wymusza `ByVal`, należy zwrócić uwagę dwa poziomy nawiasów.  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Gdy `str` jest ujęta w dodatkowe nawiasy w liście argumentów `setNewString` procedury nie można zmienić jego wartości w wywoływanym kodzie i `MsgBox` wyświetla "nie można zamienić, jeśli przekazany ByVal". Gdy `str` nie jest ujęta w nawiasy dodatkowe procedury można zmienić, i `MsgBox` Wyświetla "Jest nową wartość dla argumentu inString".  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Jeśli zmienna przez odwołanie, należy użyć `ByRef` — słowo kluczowe, aby określić, ten mechanizm.  
  
 Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości. Jednak jest dobre rozwiązanie to dołączenie albo programowania [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe z każdym zadeklarowany parametr. Ułatwia to kodu do odczytu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli parametr deklaruje procedurę [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), prawidłowe wykonanie kodu może być zależna od możliwość zmiany odpowiedniego elementu kodu wywołującego. Jeśli kod wywołujący zastępuje ten mechanizm wywoływania umieszczając argument w nawiasach, lub jeśli przekazaniem niemodyfikowalnymi argument procedury nie można zmienić elementu źródłowego. Może to spowodować nieoczekiwane wyniki w wywoływanym kodzie.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Istnieje potencjalne ryzyko z umożliwieniem procedury zmienić wartość argumentu w wywoływanym kodzie podstawowy. Upewnij się, że oczekiwane tę wartość można zmienić, i jest gotowy do Sprawdź poprawność, przed jego użyciem.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
