---
title: Opracowywanie złożonego formantu formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: bfbb9091d40652bdd1ae277f3a77feefbccbf080
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196466"
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="43115-102">Opracowywanie złożonego formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="43115-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="43115-103">Możesz tworzyć złożonego formantu Windows Forms, łącząc innych kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="43115-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="43115-104">Formanty złożone, które wynikają z <xref:System.Web.UI.UserControl> noszą nazwę kontrolek użytkownika.</span><span class="sxs-lookup"><span data-stu-id="43115-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="43115-105">Klasa bazowa <xref:System.Windows.Forms.UserControl>, zapewnia klawiatury routingu dla formantów podrzędnych, dlatego zapewnienie, że formanty podrzędne może odebrać fokus.</span><span class="sxs-lookup"><span data-stu-id="43115-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="43115-106">Na przykład kontrolki użytkownika zobacz <xref:System.Windows.Forms.UserControl> próbki w [jak: Stosowanie atrybutów w kontrolkach formularzy Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="43115-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="43115-107">Projektanta Windows Forms w programie Visual Studio zapewnia zaawansowane obsługi w czasie projektowania na potrzeby tworzenia kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="43115-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>  
  
-   [<span data-ttu-id="43115-108">Instrukcje: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="43115-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
-   [<span data-ttu-id="43115-109">Przewodnik: serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="43115-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [<span data-ttu-id="43115-110">Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows formantu z Visual C#</span><span class="sxs-lookup"><span data-stu-id="43115-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="43115-111">Instrukcje: dostarczanie mapy bitowej przybornika dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="43115-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
-   [<span data-ttu-id="43115-112">Instrukcje: dziedziczenie z istniejących kontrolek formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="43115-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
  
-   [<span data-ttu-id="43115-113">Przewodnik: debugowanie niestandardowych kontrolek formularzy systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="43115-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
-   [<span data-ttu-id="43115-114">Instrukcje: dziedziczenie z klasy kontrolek</span><span class="sxs-lookup"><span data-stu-id="43115-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
  
-   [<span data-ttu-id="43115-115">Instrukcje: testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="43115-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [<span data-ttu-id="43115-116">Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="43115-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
-   [<span data-ttu-id="43115-117">Instrukcje: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="43115-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
  
-   [<span data-ttu-id="43115-118">Instrukcje: kontrolki autoryzacji dla formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="43115-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
  
-   [<span data-ttu-id="43115-119">Instrukcje: autoryzowanie kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="43115-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
  
-   [<span data-ttu-id="43115-120">Przewodnik: tworzenie kontrolki złożonej za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43115-120">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="43115-121">Przewodnik: tworzenie kontrolki złożonej za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="43115-121">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="43115-122">Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43115-122">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="43115-123">Przewodnik: tworzenie kontrolki formularzy systemu Windows wykorzystującego funkcje czasu projektowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43115-123">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
  
-   [<span data-ttu-id="43115-124">Instrukcje: Tworzenie formantu formularzy Windows wykorzystującego funkcje czasu projektowania</span><span class="sxs-lookup"><span data-stu-id="43115-124">How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a><span data-ttu-id="43115-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43115-125">See also</span></span>

- [<span data-ttu-id="43115-126">Instrukcje: stosowanie atrybutów w kontrolkach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="43115-126">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="43115-127">Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43115-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="43115-128">Różne typy formantów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="43115-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
