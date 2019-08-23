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
ms.openlocfilehash: 3635d52532789133a345d9a9228efae869c8c223
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945617"
---
# <a name="comments-in-code-visual-basic"></a>Komentarze w kodzie (Visual Basic)
Podczas odczytywania przykładów kodu często występuje symbol komentarza (`'`). Ten symbol nakazuje kompilatorowi Visual Basic ignorowanie tekstu po nim lub *komentarz*. Komentarze to krótkie notatki wyjaśniające, dodane do kodu, aby ułatwić życie innym osobom, które go czytają.  
  
 Dobrą praktyką programowania jest rozpoczynanie wszystkich procedur od krótkiego komentarza, który opisuje charakterystykę funkcjonalną procedury (co dana procedura robi). Korzysta z tego i sam programista, i wszyscy inni, którzy czytają kod. Szczegóły dotyczące implementacji (jak procedura coś robi) należy oddzielić od komentarzy opisujących charakterystyki funkcjonalne. Gdy w opisie dołączasz szczegóły dotyczące implementacji, pamiętaj, aby je zaktualizować, gdy aktualizujesz funkcję.  
  
 Komentarze mogą następować po instrukcji w tym samym wierszu lub zajmować cały wiersz. Poniższy kod ilustruje obie wersje.  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 Jeśli komentarz wymaga więcej niż jednego wiersza, należy użyć symbolu komentarza w każdym wierszu, jak pokazuje poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a>Wytyczne komentowania  
 Poniższa tabela zawiera ogólne wytyczne na temat tego, jakie rodzaje komentarzy mogą poprzedzać sekcję kodu. Są to sugestie: Visual Basic nie wymusza reguł dodawania komentarzy. Pisz to, co się najlepiej sprawdza, zarówno dla ciebie, jak i dla każdego, kto czyta twój kod.  
  
|||  
|---|---|  
|Typ komentarza|Opis komentarza|  
|Cel|Opisuje, co procedura robi (a nie jak to robi)|  
|Założenia|Wymienia każdą zewnętrzną zmienną, element sterujący, otwarty plik lub inny element, do którego procedura uzyskuje dostęp|  
|Efekty|Wymienia każdą zewnętrzną zmienną, element sterowania lub plik i efekt, jaki wywołuje (tylko jeśli nie jest on oczywisty)|  
|Dane wejściowe|Określa cel argumentu|  
|Zwraca|Wyjaśnia wartości zwrócone przez procedurę|  
  
 Należy pamiętać o następujących kwestiach:  
  
- Każda ważna deklaracja zmiennej powinna być poprzedzona komentarzem opisującym użycie deklarowanej zmiennej.  
  
- Zmienne, elementy sterujące i procedury powinno się nazywać na tyle jasno, żeby komentowanie było konieczne tylko w przypadku szczegółów złożonych implementacji.  
  
- Komentarze nie mogą występować w tym samym wierszu, jeśli jest on kontynuowany w następnym.  
  
 Możesz dodawać lub usuwać symbole komentarzy dla bloku kodu, wybierając jeden lub więcej wierszy kodu i wybierając **komentarz** ![(przycisk Visual Basic komentarz](./media/comments-in-code/visual-basic-comment-button.gif)w Visual Studio) i Usuń **komentarz** (![Wizualizacja Przycisk usuwania komentarza podstawowego w programie Visual Studio. ) przyciski na pasku narzędzi **Edycja.** ](./media/comments-in-code/visual-basic-uncomment-button.gif)  
  
> [!NOTE]
> Możesz również dodać komentarze do kodu, poprzedzając tekst `REM` słowem kluczowym. Jednak symbole i **Komentarze komentarzy**/są łatwiejsze do użycia i wymagają mniej miejsca i pamięci. `'`  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe intuicji — dokumentowanie kodu z komentarzami XML](https://msdn.microsoft.com/magazine/dd722812.aspx)
- [Instrukcje: Utwórz dokumentację XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
- [Konwencje dotyczące struktury programów i kodu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [REM, instrukcja](../../../visual-basic/language-reference/statements/rem-statement.md)
