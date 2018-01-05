---
title: 'Porady: dostarczanie mapy bitowej przybornika dla formantu'
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
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 947ac4f8783b388135cf9e8147bb48eda93cfa08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="1b432-102">Porady: dostarczanie mapy bitowej przybornika dla formantu</span><span class="sxs-lookup"><span data-stu-id="1b432-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="1b432-103">Jeśli chcesz mieć specjalne ikon dla formantu są wyświetlane w **przybornika**, określonego obrazu można określić za pomocą <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1b432-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="1b432-104">Ta klasa jest *atrybutu*, specjalny rodzaj klasy można dołączyć do innych klas.</span><span class="sxs-lookup"><span data-stu-id="1b432-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="1b432-105">Aby uzyskać więcej informacji na temat atrybutów, zobacz [NOT IN kompilacji: Omówienie atrybutów w języku Visual Basic](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f) dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] i [atrybuty](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) dla [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b432-105">For more information about attributes, see [NOT IN BUILD: Attributes Overview in Visual Basic](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f) for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] and [Attributes](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) for [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span>  
  
 <span data-ttu-id="1b432-106">Przy użyciu <xref:System.Drawing.ToolboxBitmapAttribute>, można określić ciąg, który określa ścieżkę i nazwę pliku mapy bitowej pikseli 16 na 16.</span><span class="sxs-lookup"><span data-stu-id="1b432-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="1b432-107">Ta mapa bitowa pojawia się obok formantu podczas dodawania do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="1b432-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="1b432-108">Można również określić <xref:System.Type>, w którym to przypadku mapy bitowej skojarzony z danym typem jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="1b432-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="1b432-109">Jeśli możesz określić ich obu <xref:System.Type> i ciąg, formantu wyszukuje zasób obrazu o nazwie określonej przez parametr ciągu w zestaw zawierający typ określony przez <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="1b432-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="1b432-110">Aby określić mapy bitowej przybornika dla formantu</span><span class="sxs-lookup"><span data-stu-id="1b432-110">To specify a Toolbox bitmap for your control</span></span>  
  
1.  <span data-ttu-id="1b432-111">Dodaj <xref:System.Drawing.ToolboxBitmapAttribute> deklaracji klasy z formantu przed `Class` — słowo kluczowe dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]i powyżej deklaracji klasy [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b432-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], and above the class declaration for [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span>  
  
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
  
2.  <span data-ttu-id="1b432-112">Skompiluj ponownie projekt.</span><span class="sxs-lookup"><span data-stu-id="1b432-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1b432-113">Nie ma mapy bitowej przybornika dla formantów wygenerowany automatycznie i składniki.</span><span class="sxs-lookup"><span data-stu-id="1b432-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="1b432-114">Aby wyświetlić mapę bitową, należy ponownie załadować formantu przy użyciu **wybierz elementy przybornika** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1b432-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="1b432-115">Aby uzyskać więcej informacji, zobacz [wskazówki: automatyczne zapełnianie przybornika składnikami niestandardowe](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="1b432-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b432-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b432-116">See Also</span></span>  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [<span data-ttu-id="1b432-117">Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="1b432-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="1b432-118">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="1b432-118">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="1b432-119">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b432-119">Attributes (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="1b432-120">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b432-120">Attributes</span></span>](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
