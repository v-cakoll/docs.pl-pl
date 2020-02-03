---
title: Opracowywanie kontrolki złożonej
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: d80564c71dad57ce9145fbedd45a1396df1ddfec
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746030"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="3bcd7-102">Opracowywanie złożonego formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3bcd7-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="3bcd7-103">Możesz opracować formant Windows Forms złożone przez połączenie innych kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3bcd7-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="3bcd7-104">Kontrolki złożone, które pochodzą z <xref:System.Web.UI.UserControl> są nazywane kontrolkami użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3bcd7-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="3bcd7-105">Klasa bazowa, <xref:System.Windows.Forms.UserControl>, zapewnia Routing klawiatury dla formantów podrzędnych, dzięki czemu można uzyskać fokus formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3bcd7-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="3bcd7-106">Aby zapoznać się z przykładem kontrolki użytkownika, zobacz przykład <xref:System.Windows.Forms.UserControl> w [instrukcje: stosowanie atrybutów w kontrolkach Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3bcd7-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="3bcd7-107">Projektant Windows Forms w programie Visual Studio zapewnia rozbudowaną obsługę tworzenia formantów użytkownika w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="3bcd7-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="3bcd7-108">Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="3bcd7-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="3bcd7-109">Przewodnik: serializowanie kolekcji standardowych typów za pomocą elementu DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="3bcd7-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="3bcd7-110">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="3bcd7-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="3bcd7-111">Instrukcje: dostarczanie mapy bitowej przybornika dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="3bcd7-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="3bcd7-112">Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3bcd7-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="3bcd7-113">Przewodnik: debugowanie niestandardowych kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="3bcd7-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="3bcd7-114">Instrukcje: dziedziczenie z klasy kontrolek</span><span class="sxs-lookup"><span data-stu-id="3bcd7-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="3bcd7-115">Instrukcje: testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="3bcd7-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="3bcd7-116">Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="3bcd7-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="3bcd7-117">Instrukcje: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="3bcd7-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="3bcd7-118">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3bcd7-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="3bcd7-119">Instrukcje: tworzenie kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="3bcd7-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="3bcd7-120">Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="3bcd7-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="3bcd7-121">Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3bcd7-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="3bcd7-122">[Instrukcje: Tworzenie formantu Windows Forms, który korzysta z funkcji czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="3bcd7-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="3bcd7-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bcd7-123">See also</span></span>

- [<span data-ttu-id="3bcd7-124">Instrukcje: stosowanie atrybutów w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3bcd7-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="3bcd7-125">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3bcd7-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="3bcd7-126">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="3bcd7-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
