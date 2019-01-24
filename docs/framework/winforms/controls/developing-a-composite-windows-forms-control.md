---
title: Opracowywanie złożonego formantu formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 82d76c1656ff14c6d1c9bbbb1c79ec3a30708a90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635718"
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="3f00e-102">Opracowywanie złożonego formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3f00e-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="3f00e-103">Możesz tworzyć złożonego formantu Windows Forms, łącząc innych kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3f00e-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="3f00e-104">Formanty złożone, które wynikają z <xref:System.Web.UI.UserControl> noszą nazwę kontrolek użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3f00e-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="3f00e-105">Klasa bazowa <xref:System.Windows.Forms.UserControl>, zapewnia klawiatury routingu dla formantów podrzędnych, dlatego zapewnienie, że formanty podrzędne może odebrać fokus.</span><span class="sxs-lookup"><span data-stu-id="3f00e-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="3f00e-106">Na przykład kontrolki użytkownika zobacz <xref:System.Windows.Forms.UserControl> próbki w [jak: Stosowanie atrybutów w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3f00e-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="3f00e-107">Projektanta Windows Forms w programie Visual Studio zapewnia zaawansowane obsługi w czasie projektowania na potrzeby tworzenia kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3f00e-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>  
  
-   <span data-ttu-id="3f00e-108">[Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-108">[How to: Display a Control in the Choose Toolbox Items Dialog Box](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   [<span data-ttu-id="3f00e-109">Przewodnik: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="3f00e-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   <span data-ttu-id="3f00e-110">[Przewodnik: Dziedziczenie z Windows Forms kontrolki z wizualizacją C# ](https://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span><span class="sxs-lookup"><span data-stu-id="3f00e-110">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](https://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span></span>  
  
-   <span data-ttu-id="3f00e-111">[Instrukcje: Dostarczanie mapy bitowej przybornika dla formantu](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-111">[How to: Provide a Toolbox Bitmap for a Control](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-112">[Instrukcje: Dziedzicz Windows istniejących formantów formularzy](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-112">[How to: Inherit from Existing Windows Forms Controls](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-113">[Przewodnik: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-113">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-114">[Instrukcje: Dziedziczenie z klasy formantów](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-114">[How to: Inherit from the Control Class](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   [<span data-ttu-id="3f00e-115">Instrukcje: Testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="3f00e-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   <span data-ttu-id="3f00e-116">[Instrukcje: Wyrównywanie formantu z krawędziami formularzy w czasie projektowania](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-116">[How to: Align a Control to the Edges of Forms at Design Time](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-117">[Instrukcje: Dziedziczenie z klasy UserControl](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-117">[How to: Inherit from the UserControl Class](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-118">[Instrukcje: Tworzenie kontrolek dla formularzy Windows Forms](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-118">[How to: Author Controls for Windows Forms](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-119">[Instrukcje: Formanty złożone autora](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-119">[How to: Author Composite Controls](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-120">[Przewodnik: Tworzenie formantu złożonego za pomocą Visual Basic](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-120">[Walkthrough: Authoring a Composite Control with Visual Basic](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-121">[Przewodnik: Tworzenie kontrolki złożonej z wizualizacją C# ](https://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span><span class="sxs-lookup"><span data-stu-id="3f00e-121">[Walkthrough: Authoring a Composite Control with Visual C#](https://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span></span>  
  
-   <span data-ttu-id="3f00e-122">[Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual Basic](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-122">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-123">[Instrukcje: Tworzenie formantu formularzy Windows wykorzystującego funkcje czasu projektowania](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-123">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3f00e-124">[Instrukcje: Tworzenie formantu formularzy Windows wykorzystującego funkcje czasu projektowania](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="3f00e-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f00e-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f00e-125">See also</span></span>
- [<span data-ttu-id="3f00e-126">Instrukcje: Stosowanie atrybutów w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f00e-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="3f00e-127">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3f00e-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="3f00e-128">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="3f00e-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
