---
title: 'Instrukcje: Zmienianie rozmiarów formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 2da4b7483e92b02360bceb886d84a7f729b84dee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077228"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="14f59-102">Instrukcje: Zmienianie rozmiarów formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14f59-102">How to: Resize Windows Forms</span></span>
<span data-ttu-id="14f59-103">Rozmiar formularza Windows można określić na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="14f59-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="14f59-104">Można zmienić wysokość i szerokość formularza programowo, ustawiając nową wartość dla <xref:System.Windows.Forms.Form.Size%2A> właściwości lub dostosować <xref:System.Windows.Forms.Control.Height%2A> lub <xref:System.Windows.Forms.Control.Width%2A> właściwości indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="14f59-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="14f59-105">Jeśli używasz programu Visual Studio, możesz zmienić rozmiar przy użyciu programu Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="14f59-105">If you are using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="14f59-106">Zobacz też [jak: Zmiana rozmiaru formularzy Windows za pomocą projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="14f59-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>  
  
### <a name="to-resize-a-form-programmatically"></a><span data-ttu-id="14f59-107">Aby programowo zmienić rozmiar formularza</span><span class="sxs-lookup"><span data-stu-id="14f59-107">To resize a form programmatically</span></span>  
  
-   <span data-ttu-id="14f59-108">Określ rozmiar formularza w czasie wykonywania, ustawiając <xref:System.Windows.Forms.Form.Size%2A> właściwości formularza.</span><span class="sxs-lookup"><span data-stu-id="14f59-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>  
  
     <span data-ttu-id="14f59-109">Poniższy przykład kodu pokazuje rozmiar formularza, równa 100 x 100 pikseli.</span><span class="sxs-lookup"><span data-stu-id="14f59-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a><span data-ttu-id="14f59-110">Aby programowo zmienić wysokość i szerokość formularza</span><span class="sxs-lookup"><span data-stu-id="14f59-110">To change form width and height programmatically</span></span>  
  
-   <span data-ttu-id="14f59-111">Po <xref:System.Windows.Forms.Form.Size%2A> jest zdefiniowany, zmienić za pomocą formularza wysokość lub szerokość <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="14f59-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="14f59-112">Poniższy przykład kodu pokazuje szerokość formularza, wartość 300 pikseli od lewej krawędzi formularza, natomiast wysokość pozostają stałe.</span><span class="sxs-lookup"><span data-stu-id="14f59-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     <span data-ttu-id="14f59-113">—lub—</span><span class="sxs-lookup"><span data-stu-id="14f59-113">-or-</span></span>  
  
     <span data-ttu-id="14f59-114">Zmiana <xref:System.Drawing.Size.Width%2A> lub <xref:System.Drawing.Size.Height%2A> , ustawiając <xref:System.Windows.Forms.Form.Size%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="14f59-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>  
  
     <span data-ttu-id="14f59-115">Jednakże, jak pokazano w poniższym przykładzie kodu, to podejście jest bardziej skomplikowane niż ustawienie tylko <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="14f59-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a><span data-ttu-id="14f59-116">Aby zmienić rozmiar formularza krokami programowe</span><span class="sxs-lookup"><span data-stu-id="14f59-116">To change form size by increments programmatically</span></span>  
  
-   <span data-ttu-id="14f59-117">Aby zwiększyć rozmiar formularza, ustaw <xref:System.Drawing.Size.Width%2A> i <xref:System.Drawing.Size.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="14f59-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="14f59-118">Poniższy przykład kodu pokazuje szerokość formularza ustawiona na 200 pikseli szerszy niż bieżące ustawienie.</span><span class="sxs-lookup"><span data-stu-id="14f59-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>  
  
    ```vb  
    Form1.Width += 200  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="14f59-119">Zawsze używaj <xref:System.Drawing.Size.Height%2A> lub <xref:System.Drawing.Size.Width%2A> właściwości do zmiany wymiar formularza, chyba że ustawiasz szerokość i wysokość wymiarów w tym samym czasie, ustawiając <xref:System.Windows.Forms.Form.Size%2A> nową właściwość <xref:System.Drawing.Size> struktury.</span><span class="sxs-lookup"><span data-stu-id="14f59-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="14f59-120"><xref:System.Windows.Forms.Form.Size%2A> Właściwość zwraca <xref:System.Drawing.Size> struktury, która jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="14f59-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="14f59-121">Nowa wartość nie można przypisać do właściwości typu wartości.</span><span class="sxs-lookup"><span data-stu-id="14f59-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="14f59-122">W związku z tym nie zostanie skompilowany w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="14f59-122">Therefore, the following code example will not compile.</span></span>  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="14f59-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14f59-123">See also</span></span>

- [<span data-ttu-id="14f59-124">Wprowadzenie do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="14f59-124">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="14f59-125">Rozszerzanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14f59-125">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
