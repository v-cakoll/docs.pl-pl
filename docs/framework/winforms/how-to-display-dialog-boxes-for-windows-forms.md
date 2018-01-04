---
title: "Porady: wyświetlanie okien dialogowych formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46e4d019bbd586c0ed46794f55c65da7bcc657f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Porady: wyświetlanie okien dialogowych formularzy systemu Windows
Okno dialogowe jest wyświetlane w taki sam sposób jak inne formy są wyświetlane w aplikacji. Formularz początkowy jest ładowana automatycznie po uruchomieniu aplikacji. Aby drugi formularz lub okno dialogowe, które są wyświetlane w aplikacji, należy napisać kod ładowania i wyświetl ją. Podobnie formularza lub okna dialogowego pole znikają, kod zapisu, aby zwolnić lub je ukryć.  
  
### <a name="to-display-a-dialog-box"></a>Aby wyświetlić okno dialogowe  
  
1.  Przejdź do programu obsługi zdarzeń, z którą chcesz otworzyć okno dialogowe. Może się to zdarzyć, gdy polecenia menu jest zaznaczona, gdy zostanie kliknięty przycisk lub inne zdarzenia.  
  
2.  W obsłudze zdarzeń Dodaj kod, aby otworzyć okno dialogowe. W tym przykładzie zdarzenie kliknięcia przycisku umożliwia wyświetlenie okna dialogowego:  
  
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
