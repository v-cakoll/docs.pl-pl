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
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="81e66-102">Porady: wyświetlanie okien dialogowych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="81e66-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="81e66-103">Okno dialogowe jest wyświetlane w taki sam sposób, jak w aplikacji jest wyświetlany inny formularz.</span><span class="sxs-lookup"><span data-stu-id="81e66-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="81e66-104">Formularz startowy ładuje się automatycznie po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="81e66-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="81e66-105">Aby drugi formularz lub okno dialogowe były wyświetlane w aplikacji, napisz kod, aby go załadować i wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="81e66-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="81e66-106">Podobnie, aby formularz lub okno dialogowe zniknęło, napisz kod, aby go zwolnić lub ukryć.</span><span class="sxs-lookup"><span data-stu-id="81e66-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="81e66-107">Aby wyświetlić okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="81e66-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="81e66-108">Przejdź do programu obsługi zdarzeń, za pomocą którego chcesz otworzyć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="81e66-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="81e66-109">Może się to zdarzyć, gdy zostanie wybrane polecenie menu, po kliknięciu przycisku lub gdy wystąpi inne zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="81e66-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="81e66-110">W programie obsługi zdarzeń dodaj kod, aby otworzyć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="81e66-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="81e66-111">W tym przykładzie zdarzenie kliknięcia przycisku jest używane do pokazywanie okna dialogowego:</span><span class="sxs-lookup"><span data-stu-id="81e66-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
