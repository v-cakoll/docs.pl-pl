---
title: 'Porady: drukowanie grafiki w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 8281e1e0a3d350c3b81e26bbe59c098536ef064e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521501"
---
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="f71f1-102">Porady: drukowanie grafiki w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f71f1-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="f71f1-103">Często mają drukowanie grafiki w aplikacji opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="f71f1-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="f71f1-104"><xref:System.Drawing.Graphics> Klasa zawiera metody służące do rysowania obiektów na urządzeniu, na przykład ekranu lub drukarki.</span><span class="sxs-lookup"><span data-stu-id="f71f1-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="f71f1-105">Drukowanie grafiki</span><span class="sxs-lookup"><span data-stu-id="f71f1-105">To print graphics</span></span>  
  
1.  <span data-ttu-id="f71f1-106">Dodaj <xref:System.Drawing.Printing.PrintDocument> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="f71f1-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="f71f1-107">W <xref:System.Drawing.Printing.PrintDocument.PrintPage> program obsługi zdarzeń, użyj <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy nakazać drukarki na jakiego rodzaju grafiki do drukowania.</span><span class="sxs-lookup"><span data-stu-id="f71f1-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="f71f1-108">Poniższy przykład kodu pokazuje pozwala utworzyć niebieski elipsy w prostokąt ograniczający program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f71f1-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="f71f1-109">Prostokąt ma następujące wymiary i lokalizacji: począwszy od 100, 150 250 szerokości i wysokości 250.</span><span class="sxs-lookup"><span data-stu-id="f71f1-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
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
  
     <span data-ttu-id="f71f1-110">(Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f71f1-110">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f71f1-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f71f1-111">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [<span data-ttu-id="f71f1-112">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f71f1-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
