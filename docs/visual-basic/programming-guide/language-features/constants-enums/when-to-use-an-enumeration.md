---
title: Kiedy stosować wyliczanie
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ba69249e16b8c0ee06d57d06d192874a283b295e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403540"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kiedy stosować wyliczanie (Visual Basic)
Wyliczenia oferują łatwy sposób pracy z zestawami powiązanych stałych. Wyliczenie lub `Enum` , jest nazwą symboliczną dla zestawu wartości. Wyliczenia są traktowane jako typy danych i można ich używać do tworzenia zestawów stałych do użycia ze zmiennymi i właściwościami.  
  
## <a name="when-to-use-an-enumeration"></a>Kiedy stosować wyliczanie  
 Za każdym razem, gdy procedura akceptuje ograniczony zestaw zmiennych, należy rozważyć użycie wyliczenia. Wyliczenia mają na celu wyraźniejszy i bardziej czytelny kod, szczególnie w przypadku używania znaczących nazw.  
  
 Zalety korzystania z wyliczeń obejmują:  
  
- Zmniejsza liczbę błędów spowodowanych przez transpozycję lub błędne wpisanie numerów.  
  
- Ułatwia zmianę wartości w przyszłości.  
  
- Sprawia, że kod jest łatwiejszy do odczytania, co oznacza, że błędy będą w nim wypadane.  
  
- Zapewnia zgodność dalej. W przypadku wyliczeń kod jest mniej prawdopodobnie niepowodzeniem, jeśli w przyszłości ktoś zmieni wartości odpowiadające nazwom członków.  
  
## <a name="naming-enumerations"></a>Wyliczanie nazw  
 Użyj konwencji nazewnictwa dla elementów członkowskich wyliczenia. Gdy Visual Basic napotka nazwę elementu członkowskiego wyliczenia, wyjątek może być zgłaszany, jeśli inne przywoływane biblioteki typów zawierają tę samą nazwę. Użyj unikatowego prefiksu, który identyfikuje wartości z aplikacji lub składnika.  
  
 W przypadku odwoływania się do elementu członkowskiego wyliczenia należy zakwalifikować nazwę elementu członkowskiego z nazwą wyliczenia lub użyć `Imports` instrukcji. Aby uzyskać więcej informacji, zobacz [wyliczenia i kwalifikowanie nazw](enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Wstępnie zdefiniowane wyliczenia  
 Visual Basic udostępnia wiele wstępnie zdefiniowanych wyliczeń, takich jak `FirstDayOfWeek` i `MsgBoxResult` , w celu ułatwienia działania kodu. Aby zapoznać się z listą tych elementów [, zobacz stałe i wyliczenia](../../../language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: deklarowanie wyliczenia](how-to-declare-enumerations.md)
- [Porady: odwoływanie się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md)
- [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)
- [Porady: iterowanie za pomocą wyliczania w Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum, instrukcja](../../../language-reference/statements/enum-statement.md)
- [Stałe i wyliczenia](../../../language-reference/constants-and-enumerations.md)
