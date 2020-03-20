---
title: 'Jak: Wyświetlanie okien dialogowych'
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
ms.openlocfilehash: 3625080c7c322e297a9de92e4f95a40c0caf3e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181976"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Porady: wyświetlanie okien dialogowych formularzy systemu Windows
Okno dialogowe jest wyświetlane w taki sam sposób, jak w aplikacji jest wyświetlany inny formularz. Formularz startowy ładuje się automatycznie po uruchomieniu aplikacji. Aby drugi formularz lub okno dialogowe były wyświetlane w aplikacji, napisz kod, aby go załadować i wyświetlić. Podobnie, aby formularz lub okno dialogowe zniknęło, napisz kod, aby go zwolnić lub ukryć.  
  
### <a name="to-display-a-dialog-box"></a>Aby wyświetlić okno dialogowe  
  
1. Przejdź do programu obsługi zdarzeń, za pomocą którego chcesz otworzyć okno dialogowe. Może się to zdarzyć, gdy zostanie wybrane polecenie menu, po kliknięciu przycisku lub gdy wystąpi inne zdarzenie.  
  
2. W programie obsługi zdarzeń dodaj kod, aby otworzyć okno dialogowe. W tym przykładzie zdarzenie kliknięcia przycisku jest używane do pokazywanie okna dialogowego:  
  
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
