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
ms.openlocfilehash: 64a0b8d0d0d9f0cc2bc2a841b999af58f29b4f75
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718054"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows
W tym temacie wyjaśniono znaczenie i użycie listy błędów podczas projektowania, który pojawia się w programie Microsoft Visual Studio, gdy Windows Forms Designer nie można załadować. Jeśli zostanie wyświetlona lista ten błąd, należy nie ich interpretacji jako błąd w projektancie, ale także jako pomoc do poprawiania błędów w kodzie.  
  
 Podstawową wiedzę na temat tej listy błędów są pomocne podczas debugowania aplikacji, zapewniając szczegółowe informacje na temat błędów i sugerowanie możliwych rozwiązań.  
  
## <a name="the-design-time-error-list-interface"></a>Interfejs listę błędów podczas projektowania  
 W przypadku niepowodzenia można załadować projektanta formularzy Windows w Projektancie pojawi się lista błędów. Błędy są podzielone na kategorie. Na przykład jeśli cztery wystąpienia niezadeklarowany zmiennych, te są grupowane w tej samej kategorii błędów. Każda kategoria błędu zawiera krótki opis, który znajduje się podsumowanie błędu.  
  
 Można rozwinąć lub zwinąć do kategorii błędów, klikając nagłówek kategorii błędów lub przez kliknięcie przycisku cudzysłów ostrokątny rozwijania/zwijania. Po rozwinięciu do kategorii błędów, zostanie wyświetlony następujący dodatkowej pomocy:  
  
-   Wystąpienia tego błędu.  
  
-   Pomoc dotycząca tego błędu.  
  
-   Posty na forum dotyczące tego błędu.  
  
### <a name="instances-of-this-error"></a>Wystąpienia tego błędu  
 Dodatkową pomoc, listę wszystkich wystąpień błąd w bieżącym projekcie. Wiele błędów obejmują dokładną lokalizację, w następującym formacie: *[Nazwa projektu]* *[nazwa formularza]* wiersza:*[numer wiersza]* kolumny:*— kolumny numer*. **Przejdź do kodu** link umożliwia przejście do lokalizacji w kodzie, w którym występuje błąd.  
  
 Jeśli stos wywołań jest skojarzony z powodu błędu, możesz kliknąć **Pokaż stos wywołań** łącze, które bardziej rozszerza błędu, aby wyświetlić stos wywołań. Badanie stosu może dostarczyć cennych informacji debugowania. Na przykład można śledzić funkcje, które zostały wywołane przed wystąpieniem błędu. Stos wywołań jest możliwy, tak, aby skopiować i zapisać go.  
  
> [!NOTE]
>  W języku Visual Basic na liście błędów podczas projektowania nie są wyświetlane więcej niż jeden błąd, ale mogą być wyświetlane wiele wystąpień tego samego błędu. W programie Visual C++ błędy nie mają przejdź do kodu łączy/linii numer łącza.  
  
### <a name="help-with-this-error"></a>Pomoc dotycząca tego błędu  
 Jeśli błąd zawiera łącze do skojarzonego tematu pomocy MSDN, dodatkowej pomocy zawiera łącze do tematu Pomocy. Po kliknięciu łącza, skojarzonego tematu Pomocy pojawia się w programie Visual Studio.  
  
### <a name="forum-posts-about-this-error"></a>Posty na forum dotyczące tego błędu  
 Dodatkową pomoc zawiera łącze do wpisy na forum MSDN dotyczące błędu. Fora są przeszukiwane w oparciu o ciąg komunikatu o błędzie. Możesz też spróbować przeszukiwanie forów następujące:  
  
-   [Forum projektanta programu Windows Forms](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Windows Forms forów](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a>Ignoruj i Kontynuuj  
 Można zignorować warunek błędu i kontynuowania ładowania projektanta. Wybranie tej akcji może spowodować nieoczekiwane zachowanie. Na przykład formanty nie może występować na powierzchni projektowej.  
  
## <a name="see-also"></a>Zobacz także
- [Rozwiązywanie problemów podczas projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
- [Rozwiązywanie problemów związanych z kontrolkami oraz tworzeniem składników](troubleshooting-control-and-component-authoring.md)
- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Windows Forms komunikaty o błędach projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))
