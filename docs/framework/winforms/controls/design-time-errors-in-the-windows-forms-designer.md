---
title: Błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: 00296b51563a5f973b8e5d64c55867568ff0324e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527790"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows
W tym temacie opisano, co oznacza i użyj listy błędów czasu projektowania, który jest wyświetlany w programie Microsoft Visual Studio, gdy projektant formularzy systemu Windows nie udało się załadować. Jeśli zostanie wyświetlona lista ten błąd, użytkownik powinien nie go zinterpretować jako błąd w projektancie, ale jako pomoc do poprawiania błędów w kodzie.  
  
 Podstawową wiedzę na temat tej listy błędów pomoże Ci debugowania aplikacji, zapewniając szczegółowe informacje o błędach i sugerowanie możliwych rozwiązań.  
  
## <a name="the-design-time-error-list-interface"></a>Interfejs listy błędów w czasie projektowania  
 Jeśli projektant formularzy systemu Windows nie może załadować, w Projektancie pojawi się lista błędów. Błędy są podzielone na kategorie. Na przykład jeśli cztery wystąpienia niezadeklarowany zmiennych, te zostaną zgrupowane w tej samej kategorii błąd. Każda kategoria błędu zawiera krótki opis podsumowujący błędu.  
  
 Można rozwinąć lub zwinąć kategorię błędu, albo klikając nagłówek kategorii błąd lub klikając ikonę strzałki Rozwiń/Zwiń. Po rozwinięciu kategorię błędu, wyświetlane są następujące dodatkowe pomocy:  
  
-   Wystąpienia tego błędu.  
  
-   Pomoc dotyczącą tego błędu.  
  
-   Posty na forum dotyczące tego błędu.  
  
### <a name="instances-of-this-error"></a>Wystąpienia tego błędu  
 Dodatkowej pomocy, wyświetlić listę wszystkich wystąpień błędu w bieżącym projekcie. Wiele błędów obejmują dokładna lokalizacja w następującym formacie: *[Nazwa projektu]* *[nazwa formularza]* wiersza:*[numer]* kolumny:*[numer kolumny]*. **Przejdź do kodu** łącze prowadzi do lokalizacji w kodzie, w którym występuje błąd.  
  
 Jeśli stos wywołań jest skojarzony z powodu błędu, możesz kliknąć **Pokaż stos wywołań** łącza, które dodatkowo rozszerza błędu można wyświetlić stosu wywołań. Badanie stosu zapewniają cenne informacje debugowania. Na przykład można śledzić funkcje, które zostały wywołane przed wystąpieniem błędu. Stos wywołań jest możliwy, dzięki czemu można skopiować i zapisać go.  
  
> [!NOTE]
>  W języku Visual Basic listy błędów czasu projektowania nie są wyświetlane więcej niż jeden błąd, ale mogą wyświetlać wiele wystąpień tego samego błędu. W programie Visual C++ błędy nie mają przejdź do kodu numer łącza łącza/linii.  
  
### <a name="help-with-this-error"></a>Pomoc dotyczącą tego błędu  
 Jeśli błąd zawiera łącze do skojarzonego tematu pomocy MSDN, uzyskać dodatkową pomoc zawiera łącze do tematu Pomocy. Po kliknięciu łącza skojarzonego tematu Pomocy pojawia się w programie Visual Studio.  
  
### <a name="forum-posts-about-this-error"></a>Posty na forum dotyczące tego błędu  
 Uzyskać dodatkową pomoc zawiera łącze do wpisów forum MSDN dotyczące błędu. Fora przeszukiwane są oparte na ciąg komunikatu o błędzie. Można też spróbować wyszukiwanie fora następujące:  
  
-   [Forum projektanta formularzy systemu Windows](http://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Fora formularzy systemu Windows](http://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a>Ignoruj i Kontynuuj  
 Można zignorować błąd i kontynuować ładowania projektanta. Wybranie tej akcji może spowodować nieoczekiwane zachowanie. Na przykład formanty nie może występować na powierzchni projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z Programowanie w czasie projektowania](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Rozwiązywanie problemów związanych z kontrolkami oraz tworzeniem składników](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Komunikaty projektanta formularzy systemu Windows](http://msdn.microsoft.com/library/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
