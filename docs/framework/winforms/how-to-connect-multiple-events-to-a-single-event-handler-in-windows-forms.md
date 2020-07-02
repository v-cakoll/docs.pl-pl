---
title: 'Instrukcje: łączenie wielu zdarzeń z pojedynczym programem obsługi zdarzeń'
description: Dowiedz się, jak połączyć wiele zdarzeń z jednym programem obsługi zdarzeń w Windows Forms przy użyciu widoku zdarzeń okno Właściwości w języku C#.
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
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621889"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Instrukcje: Łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach Windows Forms
W projekcie aplikacji może być konieczne użycie jednego programu obsługi zdarzeń dla wielu zdarzeń lub wykonanie tej samej procedury przez wiele zdarzeń. Na przykład często zaawansowaną funkcją oszczędzania czasu jest to, że polecenie menu podnosi takie samo zdarzenie jak przycisk w formularzu, jeśli uwidacznia te same funkcje. Można to zrobić za pomocą widoku zdarzeń okno Właściwości w języku C# lub przy użyciu `Handles` słowa kluczowego oraz pól rozwijanych **Nazwa klasy** i **metoda** w edytorze kodu Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Aby połączyć wiele zdarzeń z jednym programem obsługi zdarzeń w Visual Basic  
  
1. Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.  
  
2. W polu listy rozwijanej **Nazwa klasy** wybierz jedną z formantów, które mają być obsługiwane przez procedurę obsługi zdarzeń.  
  
3. W polu listy rozwijanej **Nazwa metody** wybierz jedno z zdarzeń, które ma być obsługiwane przez program obsługi zdarzeń.  
  
4. Edytor kodu wstawia odpowiednią procedurę obsługi zdarzeń i ustawia punkt wstawiania w ramach metody. W poniższym przykładzie jest to <xref:System.Windows.Forms.Control.Click> zdarzenie dla <xref:System.Windows.Forms.Button> kontrolki.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. Dołącz inne zdarzenia, które chcesz obsłużyć do `Handles` klauzuli.  
  
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

- [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](creating-event-handlers-in-windows-forms.md)
- [Przegląd programów obsługi zdarzeń](event-handlers-overview-windows-forms.md)
