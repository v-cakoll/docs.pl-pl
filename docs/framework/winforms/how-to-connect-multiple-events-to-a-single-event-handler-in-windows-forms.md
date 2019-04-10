---
title: 'Instrukcje: Łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: eec6a754b885cd169e5542221caefb3233c4c8af
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300726"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Instrukcje: Łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach Windows Forms
W projekcie aplikacji może okazać się niezbędne do obsługi pojedynczego zdarzenia na użytek wielu zdarzeń lub ma wiele zdarzeń, wykonaj tę samą procedurę. Na przykład często jest zaawansowane oszczędność czasu do polecenia podnieść te same zdarzenia, jak przycisk w formularzu, jeśli eksponowanie taką samą funkcjonalność. Można to zrobić, korzystając z widoku zdarzenia w oknie właściwości w C# lub za pomocą `Handles` — słowo kluczowe i **Nazwa klasy** i **nazwę metody** list rozwijanych w edytorze kodu języka Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Aby połączyć wiele zdarzeń do obsługi pojedynczego zdarzenia w języku Visual Basic  
  
1. Kliknij prawym przyciskiem myszy formularz, a następnie wybierz **Wyświetl kod**.  
  
2. Z **Nazwa klasy** listy rozwijanej, wybierz jeden z elementów sterujących, które chcesz mieć obsługi program obsługi zdarzeń.  
  
3. Z **nazwę metody** listy rozwijanej, wybierz jedną z zdarzenia, które chcesz, aby program obsługi zdarzeń do obsługi.  
  
4. Edytor kodu wstawia obsługi odpowiednie zdarzenia i umieszcza kursor w metodzie. W poniższym przykładzie jest <xref:System.Windows.Forms.Control.Click> zdarzenie <xref:System.Windows.Forms.Button> kontroli.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. Dołącz innych zdarzeń chcesz użyte do `Handles` klauzuli.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. Dodaj odpowiedni kod do obsługi zdarzeń.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Aby połączyć wiele zdarzeń do obsługi pojedynczego zdarzenia w języku C\#
  
1. Wybierz kontrolkę, do którego chcesz się połączyć program obsługi zdarzeń.  
  
2. W oknie dialogowym właściwości kliknij **zdarzenia** przycisku (![przycisk zdarzeń](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3. Kliknij nazwę zdarzenia, które mają być obsługiwane.  
  
4. W sekcji wartość obok nazwy zdarzeń kliknij przycisk listy rozwijanej, aby wyświetlić listę istniejących programów obsługi zdarzeń, które pasuje do podpisu metody, zdarzenia, które mają być obsługiwane.  
  
5. Wybierz odpowiednie zdarzenie obsługi z listy.  
  
     Kod zostanie dodany do formularza, aby powiązać zdarzenia istniejącego programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](creating-event-handlers-in-windows-forms.md)
- [Przegląd programów obsługi zdarzeń](event-handlers-overview-windows-forms.md)
