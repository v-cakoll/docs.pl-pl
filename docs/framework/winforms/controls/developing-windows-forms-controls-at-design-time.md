---
title: "Opracowywanie formantów formularzy systemu Windows w czasie projektowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4f9680bb64339f2f232793beb9c47a36c07aa4a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="79c74-102">Opracowywanie formantów formularzy systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="79c74-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="79c74-103">Dla autorów kontroli programu .NET Framework zapewnia szereg kontroli tworzenia technologii.</span><span class="sxs-lookup"><span data-stu-id="79c74-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="79c74-104">Autorzy nie są ograniczone do projektowania formanty złożone, które działają jako kolekcja istniejących formantów.</span><span class="sxs-lookup"><span data-stu-id="79c74-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="79c74-105">Poprzez dziedziczenie możesz utworzyć własne kontrolki z istniejących formantów złożonych lub istniejących formantów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="79c74-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="79c74-106">Można również projektować własne formantach, które implementują niestandardowe malowania.</span><span class="sxs-lookup"><span data-stu-id="79c74-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="79c74-107">Te opcje umożliwiają dużą elastyczność w projekcie i funkcjonalności interfejsu visual.</span><span class="sxs-lookup"><span data-stu-id="79c74-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="79c74-108">Aby móc korzystać z tych funkcji, należy zapoznać się z opartej na obiektach pojęcia dotyczące programowania.</span><span class="sxs-lookup"><span data-stu-id="79c74-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79c74-109">Nie jest konieczne dogłębnej wiedzy dziedziczenia, ale może być przydatne do odwoływania się do [podstawowe informacje o dziedziczeniu (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="79c74-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="79c74-110">Jeśli chcesz tworzyć własne kontrolki formularzy sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="79c74-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79c74-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="79c74-111">In This Section</span></span>  
 [<span data-ttu-id="79c74-112">Wskazówki: Tworzenie formantu złożonego za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="79c74-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="79c74-113">Przedstawia sposób tworzenia prostego formantu złożonego w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="79c74-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="79c74-114">Wskazówki: Tworzenie formantu złożonego za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="79c74-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="79c74-115">Przedstawia sposób tworzenia prostego formantu złożonego w języku C#.</span><span class="sxs-lookup"><span data-stu-id="79c74-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="79c74-116">Wskazówki: Dziedziczenie z formantu formularzy systemu Windows za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="79c74-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="79c74-117">Przedstawia sposób tworzenia prostego formantu formularzy systemu Windows za pomocą dziedziczenia w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="79c74-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="79c74-118">Wskazówki: Dziedziczenie z formantu formularzy systemu Windows w języku Visual C#</span><span class="sxs-lookup"><span data-stu-id="79c74-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="79c74-119">Przedstawia sposób tworzenia prostego formantu formularzy systemu Windows za pomocą dziedziczenia w języku C#.</span><span class="sxs-lookup"><span data-stu-id="79c74-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="79c74-120">Wskazówki: Przeprowadzanie typowych zadań z tagami inteligentnymi na Windows formantów formularzy</span><span class="sxs-lookup"><span data-stu-id="79c74-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="79c74-121">Pokazuje, jak korzystać z funkcji tagów inteligentnych na formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="79c74-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="79c74-122">Porady: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="79c74-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="79c74-123">Przedstawia sposób użycia <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atrybut do serializacji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="79c74-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="79c74-124">Wskazówki: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="79c74-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="79c74-125">Pokazuje, jak można debugować zachowanie czasu projektowania formantu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="79c74-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="79c74-126">Wskazówki: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79c74-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="79c74-127">Pokazuje, jak ścisła integracja złożonych kontrolek w środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="79c74-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="79c74-128">Porady: formanty autoryzacji dla formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="79c74-128">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="79c74-129">Zawiera omówienie zagadnienia dotyczące formantu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="79c74-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="79c74-130">Porady: autoryzowanie formantów złożonych</span><span class="sxs-lookup"><span data-stu-id="79c74-130">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 <span data-ttu-id="79c74-131">Przedstawia sposób tworzenia formantu przez dziedziczenie z formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="79c74-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="79c74-132">Porady: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="79c74-132">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="79c74-133">Zawiera omówienie procedury tworzenia złożonych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="79c74-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="79c74-134">Porady: dziedziczyć Windows istniejących formantów formularzy</span><span class="sxs-lookup"><span data-stu-id="79c74-134">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="79c74-135">Przedstawia sposób tworzenia przez dziedziczenie z formantu rozszerzonego <xref:System.Windows.Forms.Button> kontrolować klasy.</span><span class="sxs-lookup"><span data-stu-id="79c74-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="79c74-136">Porady: dziedziczenie z klasy formantów</span><span class="sxs-lookup"><span data-stu-id="79c74-136">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="79c74-137">Omówienie Tworzenie formantu rozszerzonego.</span><span class="sxs-lookup"><span data-stu-id="79c74-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="79c74-138">Porady: wyrównywanie formantu z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="79c74-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="79c74-139">Przedstawia sposób użycia <xref:System.Windows.Forms.Control.Dock%2A> wyrównywanie formantu z krawędzią formularza przypada dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="79c74-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="79c74-140">Porady: wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="79c74-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="79c74-141">Zawiera procedury dotyczące instalowania formantu, tak aby był wyświetlany w **Dostosowywanie przybornika** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="79c74-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="79c74-142">Porady: Podaj mapy bitowej przybornika dla formantu</span><span class="sxs-lookup"><span data-stu-id="79c74-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="79c74-143">Przedstawia sposób użycia <xref:System.Drawing.ToolboxBitmapAttribute> do wyświetlenia ikona obok formantu niestandardowego w **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="79c74-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="79c74-144">Porady: testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="79c74-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="79c74-145">Przedstawia sposób użycia **kontenera testu UserControl** do testowania zachowanie formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="79c74-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="79c74-146">Błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="79c74-146">Design-Time Errors in the Windows Forms Designer</span></span>](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="79c74-147">Wyjaśniono znaczenie i korzystanie z listy błędów czasu projektowania, który jest wyświetlany w programie Microsoft Visual Studio, gdy projektant formularzy systemu Windows nie udało się załadować.</span><span class="sxs-lookup"><span data-stu-id="79c74-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="79c74-148">Rozwiązywanie problemów z formantami oraz autoryzacją</span><span class="sxs-lookup"><span data-stu-id="79c74-148">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="79c74-149">Pokazuje, jak zdiagnozować i rozwiązać typowe problemy, które mogą wystąpić podczas tworzenia niestandardowego składnika lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="79c74-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="79c74-150">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="79c74-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="79c74-151">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="79c74-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="79c74-152">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="79c74-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="79c74-153">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="79c74-153">Related Sections</span></span>  
 [<span data-ttu-id="79c74-154">Opracowywanie niestandardowych formularzy systemu Windows formantów za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="79c74-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="79c74-155">W tym artykule omówiono sposób tworzenia Kontrolki niestandardowe z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79c74-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="79c74-156">Niezależność od języka i elementy niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="79c74-156">Language Independence and Language-Independent Components</span></span>](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="79c74-157">Wprowadza środowisko uruchomieniowe języka wspólnego, której celem jest uproszczenie tworzenia i używania składników.</span><span class="sxs-lookup"><span data-stu-id="79c74-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="79c74-158">Ważnym aspektem uproszczenie to jest rozszerzone możliwości współdziałania między składnikami napisane przy użyciu różnych języków programowania.</span><span class="sxs-lookup"><span data-stu-id="79c74-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="79c74-159">Wspólne specyfikacji języka (CLS) pozwala na tworzenie narzędzia i składniki, które współpracują z wielu języków programowania.</span><span class="sxs-lookup"><span data-stu-id="79c74-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="79c74-160">Wskazówki: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="79c74-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="79c74-161">Opisuje sposób włączania programu składnika lub kontrolki ma być wyświetlany w **Dostosowywanie przybornika** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="79c74-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
