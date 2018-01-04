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
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="6c1c1-102">Porady: wyświetlanie okien dialogowych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6c1c1-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="6c1c1-103">Okno dialogowe jest wyświetlane w taki sam sposób jak inne formy są wyświetlane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6c1c1-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="6c1c1-104">Formularz początkowy jest ładowana automatycznie po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6c1c1-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="6c1c1-105">Aby drugi formularz lub okno dialogowe, które są wyświetlane w aplikacji, należy napisać kod ładowania i wyświetl ją.</span><span class="sxs-lookup"><span data-stu-id="6c1c1-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="6c1c1-106">Podobnie formularza lub okna dialogowego pole znikają, kod zapisu, aby zwolnić lub je ukryć.</span><span class="sxs-lookup"><span data-stu-id="6c1c1-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="6c1c1-107">Aby wyświetlić okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="6c1c1-107">To display a dialog box</span></span>  
  
1.  <span data-ttu-id="6c1c1-108">Przejdź do programu obsługi zdarzeń, z którą chcesz otworzyć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6c1c1-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="6c1c1-109">Może się to zdarzyć, gdy polecenia menu jest zaznaczona, gdy zostanie kliknięty przycisk lub inne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6c1c1-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2.  <span data-ttu-id="6c1c1-110">W obsłudze zdarzeń Dodaj kod, aby otworzyć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6c1c1-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="6c1c1-111">W tym przykładzie zdarzenie kliknięcia przycisku umożliwia wyświetlenie okna dialogowego:</span><span class="sxs-lookup"><span data-stu-id="6c1c1-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
