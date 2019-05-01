---
title: 'Instrukcje: dostarczanie mapy bitowej przybornika dla kontrolki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 7c26e00acd4278ced53ad29c748ac076e0215a23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913214"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="b7baa-102">Instrukcje: dostarczanie mapy bitowej przybornika dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="b7baa-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="b7baa-103">Jeśli chcesz mieć specjalną ikonę kontrolki są wyświetlane w **przybornika**, należy określić określonego obrazu, za pomocą <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b7baa-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="b7baa-104">Ta klasa jest *atrybutu*, specjalny rodzaj klasy, można dołączyć do innych klas.</span><span class="sxs-lookup"><span data-stu-id="b7baa-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="b7baa-105">Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty Przegląd (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) dla języka Visual Basic lub [atrybuty (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) dla języka C#.</span><span class="sxs-lookup"><span data-stu-id="b7baa-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>  
  
 <span data-ttu-id="b7baa-106">Za pomocą <xref:System.Drawing.ToolboxBitmapAttribute>, można określić ciąg, który określa ścieżkę i nazwę pliku mapy bitowej 16 na 16 pikseli.</span><span class="sxs-lookup"><span data-stu-id="b7baa-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="b7baa-107">Ta mapa bitowa pojawi się obok kontrolki podczas dodawania do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="b7baa-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="b7baa-108">Można również określić <xref:System.Type>, w którym to przypadku mapy bitowej skojarzony z danym typem jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="b7baa-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="b7baa-109">Jeśli określisz zarówno <xref:System.Type> i ciąg, formant wyszukuje zasób obrazu o nazwie określonej przez parametr ciągu w zestawie z typem określonym przez <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="b7baa-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="b7baa-110">Aby określić mapy bitowej przybornika dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="b7baa-110">To specify a Toolbox bitmap for your control</span></span>  
  
1. <span data-ttu-id="b7baa-111">Dodaj <xref:System.Drawing.ToolboxBitmapAttribute> do deklaracji klasy kontrolki przed `Class` — słowo kluczowe w języku visual Basic oraz nad deklaracją klasy dla języka Visual C#.</span><span class="sxs-lookup"><span data-stu-id="b7baa-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2. <span data-ttu-id="b7baa-112">Skompiluj ponownie projekt.</span><span class="sxs-lookup"><span data-stu-id="b7baa-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7baa-113">Nie ma mapy bitowej przybornika dla kontrolki wygenerowany automatycznie i składników.</span><span class="sxs-lookup"><span data-stu-id="b7baa-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="b7baa-114">Aby wyświetlić mapę bitową, należy ponownie załadować formantu za pomocą **wybierz elementy przybornika** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b7baa-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="b7baa-115">Aby uzyskać więcej informacji, zobacz [instruktażu: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="b7baa-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7baa-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7baa-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="b7baa-117">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="b7baa-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="b7baa-118">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="b7baa-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="b7baa-119">Omówienie atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7baa-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="b7baa-120">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="b7baa-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
