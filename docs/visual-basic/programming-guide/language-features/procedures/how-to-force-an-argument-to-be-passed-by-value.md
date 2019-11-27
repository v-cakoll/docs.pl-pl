---
title: 'Porady: wymuszanie przekazywania argumentu przez wartość'
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
ms.openlocfilehash: 8261d126f988bdcf05b4a2af3106b38717e46bc8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344518"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Porady: wymuszanie przekazywania argumentu przez wartość (Visual Basic)
Deklaracja procedury określa mechanizm przekazywania. Jeśli parametr jest zadeklarowany jako [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic oczekuje na przekazanie odpowiadającego argumentu przez odwołanie. Pozwala to na zmianę wartości elementu programowania bazowego argumentu w wywoływanym kodzie. Jeśli chcesz chronić podstawowy element przed takimi zmianami, możesz zastąpić mechanizm `ByRef` przekazywaniem w wywołaniu procedury, umieszczając nazwę argumentu w nawiasach. Nawiasy te są uzupełnieniem nawiasu otaczającego listę argumentów w wywołaniu.  
  
 Kod wywołujący nie może przesłonić mechanizmu [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) .  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Aby wymusić przekazywanie argumentu przez wartość  
  
- Jeśli odpowiedni parametr jest zadeklarowany `ByVal` w procedurze, nie trzeba podejmować żadnych dodatkowych kroków. Visual Basic już oczekuje na przekazanie argumentu przez wartość.  
  
- Jeśli odpowiedni parametr jest zadeklarowany `ByRef` w procedurze, należy ująć argument w nawiasy w wywołaniu procedury.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zastępuje deklarację parametru `ByRef`. W wywołaniu, które wymusza `ByVal`, należy pamiętać o dwóch poziomach nawiasów.  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 Gdy `str` jest ujęta w dodatkowe nawiasy na liście argumentów, procedura `setNewString` nie może zmienić jej wartości w kodzie wywołującym, a `MsgBox` wyświetla "nie można zastąpić w przypadku pomyślnego ByVal". Gdy `str` nie jest ujęta w dodatkowe nawiasy, procedura może go zmienić, a `MsgBox` wyświetla "jest to nowa wartość argumentu unstring".  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Gdy przekazujesz zmienną według odwołania, musisz użyć słowa kluczowego `ByRef`, aby określić ten mechanizm.  
  
 Wartością domyślną w Visual Basic jest przekazanie argumentów według wartości. Jednak dobrym sposobem programowania jest dołączenie albo słowa kluczowego [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) z każdym zadeklarowanym parametrem. Ułatwia to odczytywanie kodu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli procedura deklaruje parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), poprawne wykonanie kodu może zależeć od możliwości zmiany podstawowego elementu w kodzie wywołującym. Jeśli wywoływany kod zastępuje ten mechanizm wywołujący przez załączanie argumentu w nawiasach lub jeśli przeszedł niemodyfikowalny argument, procedura nie może zmienić elementu bazowego. Może to spowodować nieoczekiwane wyniki w wywoływanym kodzie.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze istnieje potencjalne ryzyko w umożliwieniu procedury zmiany wartości bazowej argumentu w wywoływanym kodzie. Upewnij się, że ta wartość jest zmieniana, i przygotuj się do sprawdzenia jej pod kątem poprawności przed jej użyciem.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
