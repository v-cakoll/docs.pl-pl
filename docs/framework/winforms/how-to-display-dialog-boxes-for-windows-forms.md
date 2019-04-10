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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311087"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="31f58-102">Instrukcje: Wyświetlanie okien dialogowych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="31f58-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="31f58-103">Okno dialogowe jest wyświetlane w taki sam sposób, jak wyświetlać jakąkolwiek inną formę w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31f58-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="31f58-104">Formularz początkowy ładuje się automatycznie, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="31f58-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="31f58-105">Aby wprowadzić drugi formularz lub okno dialogowe, które są wyświetlane w aplikacji, należy napisać kod, ładowania i wyświetlania ich.</span><span class="sxs-lookup"><span data-stu-id="31f58-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="31f58-106">Podobnie aby formularza lub okna dialogowego pole znikną, napisz kod, aby zwolnić lub je ukryć.</span><span class="sxs-lookup"><span data-stu-id="31f58-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="31f58-107">Aby wyświetlić okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="31f58-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="31f58-108">Przejdź do narzędzia obsługi zdarzeń, z którą chcesz otworzyć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="31f58-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="31f58-109">Można to zrobić, po wybraniu polecenia menu, po kliknięciu przycisku lub inne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="31f58-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="31f58-110">W procedurze obsługi zdarzeń Dodaj kod, aby otworzyć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="31f58-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="31f58-111">W tym przykładzie zdarzenie kliknięcia przycisku służy do wyświetlenia w oknie dialogowym:</span><span class="sxs-lookup"><span data-stu-id="31f58-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
