---
title: Komentarze w kodzie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: fafc80cc4847e9ec05f19fc7f3d31d2d5b11197a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661155"
---
# <a name="comments-in-code-visual-basic"></a>Komentarze w kodzie (Visual Basic)
Czytając przykłady kodu, często napotykasz symbol komentarza (`'`). Ten symbol informuje kompilator języka Visual Basic, aby zignorować tekst następujący, lub *komentarz*. Komentarze to krótkie notatki wyjaśniające, dodane do kodu, aby ułatwić życie innym osobom, które go czytają.  
  
 Dobrą praktyką programowania jest rozpoczynanie wszystkich procedur od krótkiego komentarza, który opisuje charakterystykę funkcjonalną procedury (co dana procedura robi). Korzysta z tego i sam programista, i wszyscy inni, którzy czytają kod. Szczegóły dotyczące implementacji (jak procedura coś robi) należy oddzielić od komentarzy opisujących charakterystyki funkcjonalne. Gdy w opisie dołączasz szczegóły dotyczące implementacji, pamiętaj, aby je zaktualizować, gdy aktualizujesz funkcję.  
  
 Komentarze mogą następować po instrukcji w tym samym wierszu lub zajmować cały wiersz. Poniższy kod ilustruje obie wersje.  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 Jeśli komentarz wymaga więcej niż jednego wiersza, należy użyć symbolu komentarza w każdym wierszu, jak pokazuje poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## <a name="commenting-guidelines"></a>Wytyczne komentowania  
 Poniższa tabela zawiera ogólne wytyczne na temat tego, jakie rodzaje komentarzy mogą poprzedzać sekcję kodu. Są to propozycje; Visual Basic nie wymusza zasad dodawania komentarzy. Pisz to, co się najlepiej sprawdza, zarówno dla ciebie, jak i dla każdego, kto czyta twój kod.  
  
|||  
|---|---|  
|Typ komentarza|Opis komentarza|  
|Cel|Opisuje, co procedura robi (a nie jak to robi)|  
|Założenia|Wymienia każdą zewnętrzną zmienną, element sterujący, otwarty plik lub inny element, do którego procedura uzyskuje dostęp|  
|Efekty|Wymienia każdą zewnętrzną zmienną, element sterowania lub plik i efekt, jaki wywołuje (tylko jeśli nie jest on oczywisty)|  
|Dane wejściowe|Określa cel argumentu|  
|Zwraca|Wyjaśnia wartości zwrócone przez procedurę|  
  
 Należy pamiętać o następujących kwestiach:  
  
-   Każda ważna deklaracja zmiennej powinna być poprzedzona komentarzem opisującym użycie deklarowanej zmiennej.  
  
-   Zmienne, elementy sterujące i procedury powinno się nazywać na tyle jasno, żeby komentowanie było konieczne tylko w przypadku szczegółów złożonych implementacji.  
  
-   Komentarze nie mogą występować w tym samym wierszu, jeśli jest on kontynuowany w następnym.  
  
 Można dodawać lub usuwać symbole komentarza dla bloku kodu, zaznaczając jeden lub więcej wierszy kodu i wybierając **komentarz** (![Obiekt VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton ")) i **Odkomentuj** (![Obiekt VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) przyciski na **edycji**  paska narzędzi.  
  
> [!NOTE]
>  Można również dodawać komentarze do kodu, poprzedzając tekst między znakami dwóch `REM` — słowo kluczowe. Jednak `'` symboli i **komentarz**/**Odkomentuj** przyciski są łatwiejsze w użyciu i wymagają mniej miejsca i pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentowanie kodu przy użyciu komentarzy XML](https://msdn.microsoft.com/magazine/dd722812.aspx)  
 [Instrukcje: tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)  
 [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [REM, instrukcja](../../../visual-basic/language-reference/statements/rem-statement.md)
