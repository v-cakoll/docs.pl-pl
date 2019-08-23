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
ms.openlocfilehash: 428af7e4396fde8ac29046d73adda95dbe2182f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910469"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="70dff-102">Instrukcje: dostarczanie mapy bitowej przybornika dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="70dff-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="70dff-103">Jeśli chcesz mieć specjalną ikonę kontrolki w przyborniku, możesz określićkonkretny obraz przy użyciu <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="70dff-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="70dff-104">Ta klasa jest *atrybutem*, specjalnym rodzajem klasy, którą można dołączyć do innych klas.</span><span class="sxs-lookup"><span data-stu-id="70dff-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="70dff-105">Aby uzyskać więcej informacji na temat atrybutów, zobacz [Omówienie atrybutów (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) dla Visual Basic lub [atrybutówC#()](../../../csharp/programming-guide/concepts/attributes/index.md) dla. C#</span><span class="sxs-lookup"><span data-stu-id="70dff-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>  
  
 <span data-ttu-id="70dff-106">Przy użyciu <xref:System.Drawing.ToolboxBitmapAttribute>, można określić ciąg, który wskazuje ścieżkę i nazwę pliku dla mapy bitowej 16 x 16 pikseli.</span><span class="sxs-lookup"><span data-stu-id="70dff-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="70dff-107">Ta mapa bitowa pojawia się obok formantu po dodaniu do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="70dff-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="70dff-108">Można również określić <xref:System.Type>, w którym przypadku zostanie załadowana Mapa bitowa skojarzona z tym typem.</span><span class="sxs-lookup"><span data-stu-id="70dff-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="70dff-109">Jeśli określono zarówno <xref:System.Type> ciąg a, jak i, formant wyszukuje zasób obrazu o nazwie określonej przez parametr ciągu w zestawie zawierający typ określony <xref:System.Type> przez parametr.</span><span class="sxs-lookup"><span data-stu-id="70dff-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="70dff-110">Aby określić mapę bitową przybornika dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="70dff-110">To specify a Toolbox bitmap for your control</span></span>  
  
1. <span data-ttu-id="70dff-111">Dodaj do deklaracji klasy kontrolki `Class` przed słowem kluczowym dla języka Visual Basic i powyżej deklaracji klasy dla wizualizacji C# <xref:System.Drawing.ToolboxBitmapAttribute></span><span class="sxs-lookup"><span data-stu-id="70dff-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
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
  
2. <span data-ttu-id="70dff-112">Ponownie skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="70dff-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="70dff-113">Mapa bitowa nie jest wyświetlana w przyborniku dla automatycznie generowanych kontrolek i składników.</span><span class="sxs-lookup"><span data-stu-id="70dff-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="70dff-114">Aby wyświetlić mapę bitową, Załaduj ponownie formant przy użyciu okna dialogowego **Wybierz elementy przybornika** .</span><span class="sxs-lookup"><span data-stu-id="70dff-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="70dff-115">Aby uzyskać więcej informacji, [zobacz Przewodnik: Automatyczne wypełnianie przybornika składnikami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)niestandardowymi.</span><span class="sxs-lookup"><span data-stu-id="70dff-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70dff-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70dff-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="70dff-117">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="70dff-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="70dff-118">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="70dff-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="70dff-119">Omówienie atrybutów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70dff-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="70dff-120">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="70dff-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
