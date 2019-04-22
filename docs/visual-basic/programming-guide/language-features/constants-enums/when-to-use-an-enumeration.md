---
title: Kiedy stosować wyliczanie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ff2d8c324aee8bbccef050c020e5392368b05b1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825108"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kiedy stosować wyliczanie (Visual Basic)
Wyliczenia oferują prosty sposób pracy z zestawami pokrewnych stałych. Moduł wyliczenia lub `Enum`, to Symboliczna nazwa zestawu wartości. Wyliczenia są traktowane jako typy danych i umożliwia im tworzenie zestawów stałych do użycia z zmienne i ich właściwości.  
  
## <a name="when-to-use-an-enumeration"></a>Kiedy stosować wyliczanie  
 Zawsze, gdy procedura akceptuje ograniczony zestaw zmiennych, należy wziąć pod uwagę przy użyciu funkcji wyliczania. Wyliczenia powodują przejrzyste i bardziej czytelny kod, szczególnie w przypadku, gdy używane są znaczące nazwy.  
  
 Korzyści wynikające ze stosowania wyliczeń:  
  
-   Zmniejsza błędy spowodowane Transponowanie lub błędne liczby.  
  
-   Można łatwo zmienić wartości w przyszłości.  
  
-   Sprawia, że kod łatwiejsza do odczytania, co oznacza, że jest mniej prawdopodobne, że błędy będą pełzanie tę sytuację.  
  
-   Zapewnia zgodność z nowszymi wersjami. Z wyliczeniami kod jest mniej prawdopodobne zakończyć się niepowodzeniem, jeśli w przyszłości ktoś zmienia wartości odpowiadające nazwy elementów członkowskich.  
  
## <a name="naming-enumerations"></a>Nazwy wyliczeń  
 Używa konwencji nazewnictwa dla elementów członkowskich wyliczenia. Gdy Visual Basic napotyka nazwa składowej wyliczenia, może zgłoszony wyjątek, jeśli inne biblioteki typów w przywoływanych zawierać taką samą nazwę. Użyj unikatowy prefiks, który identyfikuje wartości z aplikacji lub składnika.  
  
 Przy odwoływaniu się do elementu członkowskiego wyliczenia, musisz kwalifikowania nazwy elementu członkowskiego o nazwie wyliczenie, czyli użyj `Imports` instrukcji. Aby uzyskać więcej informacji, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Wstępnie zdefiniowane wyliczenia  
 Visual Basic zawiera szereg wstępnie zdefiniowanych wyliczenia, takich jak `FirstDayOfWeek` i `MsgBoxResult`, aby ułatwić swój kod. Aby uzyskać listę tych zobacz [stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum, instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
