---
title: "Opracowywanie złożonego formantu formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da180f888031aace892efc770184be53e9341047
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="df7cd-102">Opracowywanie złożonego formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="df7cd-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="df7cd-103">Można tworzyć złożone formantu formularzy systemu Windows, łącząc inne formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="df7cd-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="df7cd-104">Formanty złożone, które pochodzą z <xref:System.Web.UI.UserControl> są nazywane kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="df7cd-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="df7cd-105">Klasa podstawowa <xref:System.Windows.Forms.UserControl>, zapewnia klawiatury routingu dla formantów podrzędnych, w związku z tym zapewnienie, że formantów podrzędnych może odebrać fokus.</span><span class="sxs-lookup"><span data-stu-id="df7cd-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="df7cd-106">Na przykład kontrolki użytkownika zobacz <xref:System.Windows.Forms.UserControl> przykładowa w [porady: zastosowanie atrybutów w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="df7cd-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="df7cd-107">Projektant formularzy systemu Windows w [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] zapewnia obsługę projektowania sformatowanego tworzenie kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="df7cd-107">The Windows Forms designer in [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] provides rich design-time support for authoring user controls.</span></span>  
  
-   <span data-ttu-id="df7cd-108">[Porady: wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-108">[How to: Display a Control in the Choose Toolbox Items Dialog Box](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-109">[Porady: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-109">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-110">[Wskazówki: Dziedziczenie z systemu Windows formularzy formantu z Visual C#](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))</span><span class="sxs-lookup"><span data-stu-id="df7cd-110">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))</span></span>  
  
-   <span data-ttu-id="df7cd-111">[Porady: Podaj mapy bitowej przybornika dla formantu](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-111">[How to: Provide a Toolbox Bitmap for a Control](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-112">[Porady: dziedziczyć Windows istniejących formantów formularzy](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-112">[How to: Inherit from Existing Windows Forms Controls](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-113">[Wskazówki: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-113">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-114">[Porady: dziedziczenie z klasy formantów](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-114">[How to: Inherit from the Control Class](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-115">[Porady: testowanie zachowania UserControl w czasie wykonywania](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-115">[How to: Test the Run-Time Behavior of a UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-116">[Porady: wyrównywanie formantu z krawędziami formularzy w czasie projektowania](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-116">[How to: Align a Control to the Edges of Forms at Design Time](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-117">[Porady: dziedziczenie z klasy UserControl](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-117">[How to: Inherit from the UserControl Class](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-118">[Porady: formanty autoryzacji dla formularzy systemu Windows](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-118">[How to: Author Controls for Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-119">[Porady: autoryzowanie formantów złożonych](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-119">[How to: Author Composite Controls](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-120">[Wskazówki: Tworzenie formantu złożonego za pomocą Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-120">[Walkthrough: Authoring a Composite Control with Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-121">[Wskazówki: Tworzenie formantu złożonego za pomocą Visual C#](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))</span><span class="sxs-lookup"><span data-stu-id="df7cd-121">[Walkthrough: Authoring a Composite Control with Visual C#](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))</span></span>  
  
-   <span data-ttu-id="df7cd-122">[Wskazówki: Dziedziczenie z formantu formularzy systemu Windows za pomocą Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-122">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-123">[Porady: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-123">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="df7cd-124">[Porady: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="df7cd-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df7cd-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df7cd-125">See Also</span></span>  
 [<span data-ttu-id="df7cd-126">Porady: stosowanie atrybutów w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="df7cd-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="df7cd-127">Opracowywanie niestandardowych formularzy systemu Windows formantów za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="df7cd-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="df7cd-128">Różne typy formantów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="df7cd-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
