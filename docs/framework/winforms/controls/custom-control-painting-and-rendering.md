---
title: Malowanie i renderowanie formantu niestandardowego
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 355a5842348aa4395d1841d0343080ddef634456
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="7c1a0-102">Malowanie i renderowanie formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="7c1a0-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="7c1a0-103">Niestandardowe rysowania formantów jest jednym z wielu skomplikowanym łatwej w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="7c1a0-104">Podczas tworzenia niestandardowego formantu, istnieje wiele opcji dotyczących graficznego wygląd formantu.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="7c1a0-105">Jeśli tworzony kontrolkę, która dziedziczy `Control`, należy podać kod, który umożliwia formantu do renderowania jej graficzną reprezentację.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="7c1a0-106">Jeśli tworzysz kontrolkę użytkownika przez dziedziczenie z `UserControl`, lub są dziedziczone z jednego z formanty formularzy systemu Windows może zastąpić standardowe graficzną reprezentację i podaj kod grafiki.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="7c1a0-107">Jeśli chcesz podać niestandardowe renderowanie formantów składowych `UserControl` tworzenia, opcje będą ograniczone, ale nadal mogli szeroką gamę możliwości graficznego dla formantów i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c1a0-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7c1a0-108">In This Section</span></span>  
 [<span data-ttu-id="7c1a0-109">Renderowanie kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c1a0-109">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 <span data-ttu-id="7c1a0-110">Pokazano, jak program logikę, która wyświetla formant.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="7c1a0-111">Kontrolki rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="7c1a0-111">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 <span data-ttu-id="7c1a0-112">Zestawienie etapy pisania i zastępowanie kodu renderowania dla formantu.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="7c1a0-113">Kontrolki składników</span><span class="sxs-lookup"><span data-stu-id="7c1a0-113">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 <span data-ttu-id="7c1a0-114">Opisuje sposób implementowania kodu niestandardowe renderowanie formantów składowych formularzy i kontrolek użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="7c1a0-115">Instrukcje: ukrywanie kontrolki w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="7c1a0-115">How to: Make Your Control Invisible at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="7c1a0-116">Przedstawia sposób użycia <xref:System.Windows.Forms.Control.Visible%2A> właściwości, aby ukryć i pokazać formantu.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="7c1a0-117">Instrukcje: ustawienie przezroczystego tła kontrolki</span><span class="sxs-lookup"><span data-stu-id="7c1a0-117">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="7c1a0-118">Przedstawia sposób użycia <xref:System.Windows.Forms.Control.SetStyle%2A> metodę w celu utworzenia kolor tła nieprzezroczyste, przezroczysty lub częściowo przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="7c1a0-119">Renderowanie kontrolek przy użyciu stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="7c1a0-119">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="7c1a0-120">Przedstawia sposób renderowania formantów przy użyciu stylów wizualnych w systemach operacyjnych, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7c1a0-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7c1a0-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="7c1a0-122">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="7c1a0-123">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="7c1a0-124">Zawiera opis tej metody.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7c1a0-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7c1a0-125">Related Sections</span></span>  
 [<span data-ttu-id="7c1a0-126">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="7c1a0-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="7c1a0-127">Wprowadza [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje graficzne z programu Visual Studio perspektywy i udostępnia łącza do dodatkowych informacji.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-127">Introduces [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="7c1a0-128">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="7c1a0-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="7c1a0-129">W tym artykule opisano typy formantów niestandardowych, które można tworzyć.</span><span class="sxs-lookup"><span data-stu-id="7c1a0-129">Describes the kinds of custom controls you can author.</span></span>
