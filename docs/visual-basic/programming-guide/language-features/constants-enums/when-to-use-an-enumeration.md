---
title: Kiedy stosować wyliczanie
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 5daae8d487ddfe079a54e305e59e32e8ded8f65e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353959"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kiedy stosować wyliczanie (Visual Basic)
Wyliczenia oferują łatwy sposób pracy z zestawami powiązanych stałych. Wyliczenie lub `Enum`, jest nazwą symboliczną zestawu wartości. Wyliczenia są traktowane jako typy danych i można ich używać do tworzenia zestawów stałych do użycia ze zmiennymi i właściwościami.  
  
## <a name="when-to-use-an-enumeration"></a>Kiedy stosować wyliczanie  
 Za każdym razem, gdy procedura akceptuje ograniczony zestaw zmiennych, należy rozważyć użycie wyliczenia. Wyliczenia mają na celu wyraźniejszy i bardziej czytelny kod, szczególnie w przypadku używania znaczących nazw.  
  
 Zalety korzystania z wyliczeń obejmują:  
  
- Zmniejsza liczbę błędów spowodowanych przez transpozycję lub błędne wpisanie numerów.  
  
- Ułatwia zmianę wartości w przyszłości.  
  
- Sprawia, że kod jest łatwiejszy do odczytania, co oznacza, że błędy będą w nim wypadane.  
  
- Zapewnia zgodność dalej. W przypadku wyliczeń kod jest mniej prawdopodobnie niepowodzeniem, jeśli w przyszłości ktoś zmieni wartości odpowiadające nazwom członków.  
  
## <a name="naming-enumerations"></a>Wyliczanie nazw  
 Użyj konwencji nazewnictwa dla elementów członkowskich wyliczenia. Gdy Visual Basic napotka nazwę elementu członkowskiego wyliczenia, wyjątek może być zgłaszany, jeśli inne przywoływane biblioteki typów zawierają tę samą nazwę. Użyj unikatowego prefiksu, który identyfikuje wartości z aplikacji lub składnika.  
  
 W przypadku odwoływania się do elementu członkowskiego wyliczenia należy zakwalifikować nazwę elementu członkowskiego o nazwie wyliczenia lub użyć instrukcji `Imports`. Aby uzyskać więcej informacji, zobacz [wyliczenia i kwalifikowanie nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Wstępnie zdefiniowane wyliczenia  
 Visual Basic udostępnia wiele wstępnie zdefiniowanych wyliczeń, takich jak `FirstDayOfWeek` i `MsgBoxResult`, aby ułatwić wykonywanie kodu. Aby zapoznać się z listą tych elementów [, zobacz stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: deklarowanie wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrukcje: Iterowanie przez Wyliczenie w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum, instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
