---
title: 'Instrukcje: Drukowanie grafiki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 2435b3bc14747a00d2a0fc03a9ebd21ae43c5369
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740643"
---
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="aaef3-102">Porady: drukowanie grafiki w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="aaef3-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="aaef3-103">Często chcesz wydrukować grafikę w aplikacji opartej na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="aaef3-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="aaef3-104">Klasa <xref:System.Drawing.Graphics> zapewnia metody rysowania obiektów na urządzeniu, takie jak ekran lub drukarka.</span><span class="sxs-lookup"><span data-stu-id="aaef3-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="aaef3-105">Aby wydrukować grafikę</span><span class="sxs-lookup"><span data-stu-id="aaef3-105">To print graphics</span></span>  
  
1. <span data-ttu-id="aaef3-106">Dodaj składnik <xref:System.Drawing.Printing.PrintDocument> do formularza.</span><span class="sxs-lookup"><span data-stu-id="aaef3-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="aaef3-107">W obsłudze zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage> Użyj właściwości <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> klasy <xref:System.Drawing.Printing.PrintPageEventArgs>, aby poinstruować drukarkę, jakiego rodzaju grafika ma drukować.</span><span class="sxs-lookup"><span data-stu-id="aaef3-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="aaef3-108">Poniższy przykład kodu pokazuje procedurę obsługi zdarzeń użytą do utworzenia niebieską elipsę w obrębie prostokąta ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="aaef3-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="aaef3-109">Prostokąt ma następującą lokalizację i wymiary: od 100 do 150 z szerokością 250 i wysokością 250.</span><span class="sxs-lookup"><span data-stu-id="aaef3-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     <span data-ttu-id="aaef3-110">(Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aaef3-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="aaef3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aaef3-111">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="aaef3-112">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aaef3-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
