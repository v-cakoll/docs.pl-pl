---
title: Kiedy stosować wyliczanie (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ab152687f4f9e4ba6bd032ae7c1352f65af715f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kiedy stosować wyliczanie (Visual Basic)
Wyliczenia oferują prosty sposób pracy z zestawów powiązanych stałe. Jako wyliczenia lub `Enum`, jest nazwa symboliczna dla zestawu wartości. Wyliczenia są traktowane jako typy danych i można je utworzyć zestawy stałych do użycia z zmiennych i właściwości.  
  
## <a name="when-to-use-an-enumeration"></a>Kiedy stosować wyliczanie  
 Zawsze, gdy procedura akceptuje ograniczony zestaw zmiennych, należy wziąć pod uwagę przy użyciu wyliczania. Wyliczenia upewnij się jaśniejszy i czytelność kodu, szczególnie w przypadku, gdy są używane łatwy do rozpoznania nazwy.  
  
 Korzyści wynikające ze stosowania wyliczenia obejmują:  
  
-   Zmniejsza liczbę błędów spowodowanych przez Transponowanie lub błędne liczby.  
  
-   Można łatwo zmienić wartości w przyszłości.  
  
-   Powoduje, że kod czytelności, co oznacza, że jest mniej prawdopodobne, że błędy będą pełzanie do niego.  
  
-   Zapewnia zgodność z nowszymi wersjami. Z wyliczenia kod jest mniej prawdopodobne się niepowodzeniem, jeśli w przyszłości użytkownik wprowadza zmiany wartości odpowiadających nazwy elementów członkowskich.  
  
## <a name="naming-enumerations"></a>Wyliczenia nazw  
 Elementy członkowskie wyliczenia używać konwencji nazewnictwa. Gdy Visual Basic napotka nazwę elementu członkowskiego wyliczenia, wyjątek może zostać zgłoszony, jeśli inne biblioteki typu występującego w odwołaniu nie ma takiej samej nazwie. Użyj unikatowy prefiks, który identyfikuje wartości z aplikacją lub składnikiem albo.  
  
 Podczas odwoływania się do elementu członkowskiego wyliczenia, musisz nazwy elementu członkowskiego o nazwie wyliczenia, czyli użyj `Imports` instrukcji. Aby uzyskać więcej informacji, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Wstępnie zdefiniowane wyliczenia  
 Visual Basic zapewnia szereg wstępnie zdefiniowanych wyliczenia `FirstDayOfWeek` i `MsgBoxResult`, aby ułatwić kodu. Lista tych [stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Porady: iterowanie za pomocą wyliczania w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Enum, instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
