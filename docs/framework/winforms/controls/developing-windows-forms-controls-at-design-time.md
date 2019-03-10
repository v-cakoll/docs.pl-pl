---
title: Opracowywanie formantów formularzy systemu Windows w czasie projektowania
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
ms.openlocfilehash: 641a6c1c99169c6836c33b3e84b2ae02aba298d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707719"
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="c7650-102">Opracowywanie formantów formularzy systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c7650-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="c7650-103">Dla autorów kontroli programu .NET Framework zapewnia wiele technologii do tworzenia kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c7650-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="c7650-104">Autorzy nie są już ograniczony do projektowania formanty złożone, które działają jako kolekcję istniejących kontrolek.</span><span class="sxs-lookup"><span data-stu-id="c7650-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="c7650-105">Poprzez dziedziczenie można utworzyć własne kontrolki z istniejących kontrolek złożonych lub istniejących kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c7650-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="c7650-106">Istnieje również możliwość projektowania własnych kontrolek, które implementują niestandardowe malowania.</span><span class="sxs-lookup"><span data-stu-id="c7650-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="c7650-107">Te opcje umożliwiają dużą elastyczność w projekcie i funkcjonalność interfejsu wizualnego.</span><span class="sxs-lookup"><span data-stu-id="c7650-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="c7650-108">Aby móc korzystać z tych funkcji, należy zapoznać się z koncepcjami opartej na obiektach.</span><span class="sxs-lookup"><span data-stu-id="c7650-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7650-109">Nie jest konieczne dogłębną wiedzę na temat dziedziczenia, ale może okazać się przydatne do odwoływania się do [podstawowe informacje o dziedziczeniu (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c7650-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="c7650-110">Jeśli chcesz utworzyć niestandardowe formanty do użycia w formularzach sieci Web, zobacz artykuł [tworzenie niestandardowe formanty serwera ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c7650-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7650-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c7650-111">In This Section</span></span>  
 [<span data-ttu-id="c7650-112">Przewodnik: Tworzenie formantu złożonego za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7650-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="c7650-113">Przedstawia sposób tworzenia prostego formantu złożonego w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c7650-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="c7650-114">Przewodnik: Tworzenie formantu złożonego za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="c7650-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="c7650-115">Przedstawia sposób tworzenia prostego formantu złożonego w języku C#.</span><span class="sxs-lookup"><span data-stu-id="c7650-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="c7650-116">Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7650-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="c7650-117">Przedstawia sposób tworzenia prostego formantu Windows Forms za pomocą dziedziczenia w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c7650-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="c7650-118">Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="c7650-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="c7650-119">Przedstawia sposób tworzenia prostego formantu Windows Forms za pomocą dziedziczenia w języku C#.</span><span class="sxs-lookup"><span data-stu-id="c7650-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="c7650-120">Przewodnik: Wykonywania typowych zadań przy użyciu inteligentnych tagów w Windows Forms, formanty</span><span class="sxs-lookup"><span data-stu-id="c7650-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="c7650-121">Pokazuje, jak korzystać z funkcji tagu inteligentnego kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c7650-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="c7650-122">Przewodnik: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="c7650-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="c7650-123">Ilustruje sposób używania <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atrybutu do serializacji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c7650-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="c7650-124">Przewodnik: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c7650-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="c7650-125">Pokazuje, jak można debugować zachowania formantu Windows Forms w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="c7650-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="c7650-126">Przewodnik: Tworzenie kontrolki formularzy Windows wykorzystującego funkcje czasu projektowania w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7650-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="c7650-127">Pokazuje, jak ściśle zintegrowane formantu złożonego w środowisku projektowym.</span><span class="sxs-lookup"><span data-stu-id="c7650-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="c7650-128">Instrukcje: Tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7650-128">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="c7650-129">Zawiera omówienie zagadnienia dotyczące implementacji formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c7650-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="c7650-130">Instrukcje: Formanty złożone autora</span><span class="sxs-lookup"><span data-stu-id="c7650-130">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
 <span data-ttu-id="c7650-131">Pokazuje, jak utworzyć formant przez dziedziczenie z kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="c7650-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="c7650-132">Instrukcje: Dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="c7650-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="c7650-133">Zawiera omówienie procedury tworzenia kontrolek złożonych.</span><span class="sxs-lookup"><span data-stu-id="c7650-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="c7650-134">Instrukcje: Dziedzicz Windows istniejących formantów formularzy</span><span class="sxs-lookup"><span data-stu-id="c7650-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="c7650-135">Pokazuje, jak tworzenie formantu rozszerzonego przez dziedziczenie z <xref:System.Windows.Forms.Button> kontrolować klasy.</span><span class="sxs-lookup"><span data-stu-id="c7650-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="c7650-136">Instrukcje: Dziedziczenie z klasy formantów</span><span class="sxs-lookup"><span data-stu-id="c7650-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="c7650-137">Omówienie Tworzenie formantu rozszerzonego.</span><span class="sxs-lookup"><span data-stu-id="c7650-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="c7650-138">Instrukcje: Wyrównywanie formantu z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c7650-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="c7650-139">Ilustruje sposób używania <xref:System.Windows.Forms.Control.Dock%2A> właściwość wyrównywanie formantu do krawędzi formularza zajmuje.</span><span class="sxs-lookup"><span data-stu-id="c7650-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="c7650-140">Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="c7650-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="c7650-141">Zawiera procedury dotyczące instalowania formantu, aby była ona wyświetlana w **Dostosowywanie przybornika** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c7650-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="c7650-142">Instrukcje: Dostarczanie mapy bitowej przybornika dla formantu</span><span class="sxs-lookup"><span data-stu-id="c7650-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="c7650-143">Ilustruje sposób używania <xref:System.Drawing.ToolboxBitmapAttribute> Aby wyświetlić ikonę obok niestandardową kontrolkę w **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="c7650-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="c7650-144">Instrukcje: Testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="c7650-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="c7650-145">Ilustruje sposób używania **UserControl — kontener testu** się testowanie zachowania formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="c7650-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="c7650-146">Błędy czasu projektowania w narzędziu Projektant dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7650-146">Design-Time Errors in the Windows Forms Designer</span></span>](design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="c7650-147">Wyjaśnia znaczenie i użyj listy błędów projektowania, który pojawia się w programie Microsoft Visual Studio, gdy nie może załadować projektanta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c7650-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="c7650-148">Rozwiązywanie problemów związanych z kontrolkami oraz tworzeniem składników</span><span class="sxs-lookup"><span data-stu-id="c7650-148">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="c7650-149">Pokazuje, jak diagnozować i rozwiązywać typowe problemy, które mogą wystąpić podczas tworzenia niestandardowego składnika lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c7650-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c7650-150">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c7650-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="c7650-151">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="c7650-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="c7650-152">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="c7650-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7650-153">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c7650-153">Related Sections</span></span>  
 [<span data-ttu-id="c7650-154">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c7650-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="c7650-155">W tym artykule omówiono sposób tworzenia Kontrolki niestandardowe za pomocą programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c7650-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="c7650-156">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="c7650-156">Language Independence and Language-Independent Components</span></span>](../../../standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="c7650-157">Wprowadza wykonywalnych języka wspólnego upraszcza tworzenie i używanie składników.</span><span class="sxs-lookup"><span data-stu-id="c7650-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="c7650-158">Ważnym aspektem uproszczenie to jest rozszerzone możliwości współdziałania między składnikami napisanymi przy użyciu różnych języków programowania.</span><span class="sxs-lookup"><span data-stu-id="c7650-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="c7650-159">Common Language Specification (CLS) umożliwia tworzenie, narzędzia i składniki, które działają z wielu języków programowania.</span><span class="sxs-lookup"><span data-stu-id="c7650-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="c7650-160">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="c7650-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="c7650-161">Opisuje sposób włączania usługi składnika lub kontrolki, które mają być wyświetlane w **Dostosowywanie przybornika** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c7650-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
