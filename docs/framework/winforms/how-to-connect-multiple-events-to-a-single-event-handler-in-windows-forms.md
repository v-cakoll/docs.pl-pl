---
title: 'Instrukcje: łączenie wielu zdarzeń z pojedynczym programem obsługi zdarzeń'
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
ms.openlocfilehash: 0591291522ab1da04fef90bf1c0a73cf33ba0518
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739608"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Porady: łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach systemu Windows
W projekcie aplikacji może być konieczne użycie jednego programu obsługi zdarzeń dla wielu zdarzeń lub wykonanie tej samej procedury przez wiele zdarzeń. Na przykład często zaawansowaną funkcją oszczędzania czasu jest to, że polecenie menu podnosi takie samo zdarzenie jak przycisk w formularzu, jeśli uwidacznia te same funkcje. Można to zrobić za pomocą widoku zdarzeń okno Właściwości w C# lub przy użyciu słowa kluczowego `Handles` i pola listy rozwijanej **Nazwa klasy** i **Metoda** w edytorze kodu Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Aby połączyć wiele zdarzeń z jednym programem obsługi zdarzeń w Visual Basic  
  
1. Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.  
  
2. W polu listy rozwijanej **Nazwa klasy** wybierz jedną z formantów, które mają być obsługiwane przez procedurę obsługi zdarzeń.  
  
3. W polu listy rozwijanej **Nazwa metody** wybierz jedno z zdarzeń, które ma być obsługiwane przez program obsługi zdarzeń.  
  
4. Edytor kodu wstawia odpowiednią procedurę obsługi zdarzeń i ustawia punkt wstawiania w ramach metody. W poniższym przykładzie jest to zdarzenie <xref:System.Windows.Forms.Control.Click> dla kontrolki <xref:System.Windows.Forms.Button>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. Dołącz inne zdarzenia, które mają być obsługiwane w klauzuli `Handles`.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. Dodaj odpowiedni kod do programu obsługi zdarzeń.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Aby połączyć wiele zdarzeń z jednym programem obsługi zdarzeń w języku C\#
  
1. Wybierz kontrolkę, z którą chcesz połączyć procedurę obsługi zdarzeń.  
  
2. W okno Właściwości kliknij przycisk **zdarzenia** (![przycisk zdarzenia](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3. Kliknij nazwę zdarzenia, które chcesz obsłużyć.  
  
4. W sekcji wartość obok nazwy zdarzenia kliknij przycisk listy rozwijanej, aby wyświetlić listę istniejących programów obsługi zdarzeń, które pasują do sygnatury metody dla zdarzenia, które chcesz obsłużyć.  
  
5. Wybierz odpowiednią procedurę obsługi zdarzeń z listy.  
  
     Kod zostanie dodany do formularza w celu powiązania zdarzenia z istniejącym programem obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Przegląd procedur obsługi zdarzeń](event-handlers-overview-windows-forms.md)
