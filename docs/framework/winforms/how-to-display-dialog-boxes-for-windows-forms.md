---
title: 'Instrukcje: Wyświetlanie okien dialogowych formularzy Windows Forms'
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
ms.openlocfilehash: b99f2273dae88faf86448da6e1d2986a83803abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802586"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Instrukcje: Wyświetlanie okien dialogowych formularzy Windows Forms
Okno dialogowe jest wyświetlane w taki sam sposób, jak wyświetlać jakąkolwiek inną formę w aplikacji. Formularz początkowy ładuje się automatycznie, gdy aplikacja jest uruchomiona. Aby wprowadzić drugi formularz lub okno dialogowe, które są wyświetlane w aplikacji, należy napisać kod, ładowania i wyświetlania ich. Podobnie aby formularza lub okna dialogowego pole znikną, napisz kod, aby zwolnić lub je ukryć.  
  
### <a name="to-display-a-dialog-box"></a>Aby wyświetlić okno dialogowe  
  
1. Przejdź do narzędzia obsługi zdarzeń, z którą chcesz otworzyć okno dialogowe. Można to zrobić, po wybraniu polecenia menu, po kliknięciu przycisku lub inne zdarzenia.  
  
2. W procedurze obsługi zdarzeń Dodaj kod, aby otworzyć okno dialogowe. W tym przykładzie zdarzenie kliknięcia przycisku służy do wyświetlenia w oknie dialogowym:  
  
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
