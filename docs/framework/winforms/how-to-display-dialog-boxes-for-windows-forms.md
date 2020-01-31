---
title: 'Instrukcje: wyświetlanie okien dialogowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
ms.openlocfilehash: dd04a06eaa0dd7583ef2f72edb4cffa99aaaa60c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739465"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Porady: wyświetlanie okien dialogowych formularzy systemu Windows
Wyświetla się okno dialogowe w taki sam sposób, jak w przypadku innych formularzy w aplikacji. Formularz startowy jest ładowany automatycznie podczas uruchamiania aplikacji. Aby w aplikacji pojawił się drugi formularz lub okno dialogowe, napisz kod w celu załadowania i wyświetlenia go. Podobnie, aby formularz lub okno dialogowe znikły, napisz kod w celu zwolnienia lub ukrycia go.  
  
### <a name="to-display-a-dialog-box"></a>Aby wyświetlić okno dialogowe  
  
1. Przejdź do programu obsługi zdarzeń, za pomocą którego chcesz otworzyć okno dialogowe. Może się tak zdarzyć, gdy wybrane zostanie polecenie menu, gdy zostanie kliknięty przycisk lub gdy wystąpi jakiekolwiek inne zdarzenie.  
  
2. W programie obsługi zdarzeń Dodaj kod, aby otworzyć okno dialogowe. W tym przykładzie zdarzenie kliknięcia przycisku służy do wyświetlania okna dialogowego:  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:   
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```
