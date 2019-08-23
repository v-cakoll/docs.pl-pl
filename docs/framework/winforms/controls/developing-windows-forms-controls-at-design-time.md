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
ms.openlocfilehash: 11c3d9d6e7faa4741365316339d38f9fda69d059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965709"
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="be342-102">Opracowywanie formantów formularzy systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="be342-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="be342-103">W przypadku autorów kontroli .NET Framework zapewnia mnóstwo technologii tworzenia kontroli.</span><span class="sxs-lookup"><span data-stu-id="be342-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="be342-104">Autorzy nie są już ograniczeni do projektowania kontrolek złożonych, które działają jako kolekcja istniejących kontrolek.</span><span class="sxs-lookup"><span data-stu-id="be342-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="be342-105">Za pomocą dziedziczenia można tworzyć własne kontrolki z istniejących wcześniej kontrolek złożonych lub wcześniej istniejących kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="be342-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="be342-106">Możesz również projektować własne kontrolki implementujące niestandardowe malowanie.</span><span class="sxs-lookup"><span data-stu-id="be342-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="be342-107">Te opcje umożliwiają znaczną elastyczność projektowania i funkcjonalności interfejsu wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="be342-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="be342-108">Aby skorzystać z tych funkcji, należy zapoznać się z pojęciami programistycznymi opartymi na obiektach.</span><span class="sxs-lookup"><span data-stu-id="be342-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be342-109">Nie jest konieczne dokładne zrozumienie dziedziczenia, ale może się okazać, że warto odnieść się do podstawowych informacji dotyczących [dziedziczenia (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="be342-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="be342-110">Jeśli chcesz utworzyć niestandardowe kontrolki do użycia w formularzach sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="be342-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be342-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="be342-111">In This Section</span></span>  
 [<span data-ttu-id="be342-112">Przewodnik: Tworzenie złożonego formantu z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be342-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="be342-113">Pokazuje, jak utworzyć prosty formant złożony w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="be342-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="be342-114">Przewodnik: Tworzenie formantu złożonego za pomocą wizualizacjiC#</span><span class="sxs-lookup"><span data-stu-id="be342-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="be342-115">Pokazuje, jak utworzyć prosty formant złożony w C#.</span><span class="sxs-lookup"><span data-stu-id="be342-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="be342-116">Przewodnik: Dziedziczenie z kontrolki Windows Forms z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be342-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="be342-117">Pokazuje, jak utworzyć prostą kontrolkę Windows Forms przy użyciu dziedziczenia w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="be342-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="be342-118">Przewodnik: Dziedziczenie z kontrolki Windows Forms za pomocą wizualizacjiC#</span><span class="sxs-lookup"><span data-stu-id="be342-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="be342-119">Pokazuje, jak utworzyć prostą kontrolkę Windows Forms przy użyciu C#dziedziczenia w programie.</span><span class="sxs-lookup"><span data-stu-id="be342-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="be342-120">Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be342-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="be342-121">Pokazuje, jak używać funkcji tagów inteligentnych w kontrolkach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="be342-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="be342-122">Przewodnik: Serializacja kolekcji typów standardowych z za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="be342-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="be342-123">Pokazuje, <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> jak używać atrybutu do serializacji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="be342-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="be342-124">Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="be342-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="be342-125">Pokazuje, jak debugować zachowanie formantu Windows Forms w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="be342-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="be342-126">Przewodnik: Tworzenie kontrolki Windows Forms, która wykorzystuje funkcje czasu projektowania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be342-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="be342-127">Pokazuje ścisłą integrację złożonego formantu ze środowiskiem projektowym.</span><span class="sxs-lookup"><span data-stu-id="be342-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="be342-128">Instrukcje: Kontrolki autora dla Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be342-128">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="be342-129">Zawiera omówienie zagadnień związanych z implementacją kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="be342-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="be342-130">Instrukcje: Tworzenie złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="be342-130">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
 <span data-ttu-id="be342-131">Pokazuje, jak utworzyć formant przez dziedziczenie z kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="be342-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="be342-132">Instrukcje: Dziedzicz z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="be342-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="be342-133">Zawiera przegląd procedury tworzenia złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="be342-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="be342-134">Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be342-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="be342-135">Pokazuje, jak utworzyć formant rozszerzony przez dziedziczenie z <xref:System.Windows.Forms.Button> klasy kontrolek.</span><span class="sxs-lookup"><span data-stu-id="be342-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="be342-136">Instrukcje: Dziedzicz z klasy kontrolki</span><span class="sxs-lookup"><span data-stu-id="be342-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="be342-137">Zawiera omówienie tworzenia rozszerzonej kontroli.</span><span class="sxs-lookup"><span data-stu-id="be342-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="be342-138">Instrukcje: Wyrównywanie kontrolki do krawędzi formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="be342-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="be342-139">Pokazuje, w jaki sposób <xref:System.Windows.Forms.Control.Dock%2A> używać właściwości, aby wyrównać formant do krawędzi formularza, który on zajmowan.</span><span class="sxs-lookup"><span data-stu-id="be342-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="be342-140">Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="be342-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="be342-141">Pokazuje procedurę instalowania kontrolki tak, aby była widoczna w oknie dialogowym **Dostosowywanie przybornika** .</span><span class="sxs-lookup"><span data-stu-id="be342-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="be342-142">Instrukcje: Udostępnianie mapy bitowej przybornika dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="be342-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="be342-143">Pokazuje, <xref:System.Drawing.ToolboxBitmapAttribute> jak używać do wyświetlania ikony obok kontrolki niestandardowej w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="be342-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="be342-144">Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="be342-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="be342-145">Pokazuje, jak używać obiektu **UserControl Test Container** do testowania zachowania złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="be342-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="be342-146">Błędy czasu projektowania w narzędziu Projektant dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be342-146">Design-Time Errors in the Windows Forms Designer</span></span>](design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="be342-147">Wyjaśnia znaczenie i użycie Lista błędów czasu projektowania, które pojawiają się w Microsoft Visual Studio w przypadku niepowodzenia załadowania projektanta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="be342-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="be342-148">Rozwiązywanie problemów związanych z kontrolkami oraz tworzeniem składników</span><span class="sxs-lookup"><span data-stu-id="be342-148">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="be342-149">Pokazuje, jak diagnozować i rozwiązywać typowe problemy, które mogą wystąpić podczas tworzenia niestandardowego składnika lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be342-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="be342-150">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="be342-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="be342-151">Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="be342-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="be342-152">Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="be342-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="be342-153">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="be342-153">Related Sections</span></span>  
 [<span data-ttu-id="be342-154">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="be342-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="be342-155">W tym artykule omówiono sposób tworzenia własnych niestandardowych kontrolek przy użyciu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be342-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="be342-156">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="be342-156">Language Independence and Language-Independent Components</span></span>](../../../standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="be342-157">Wprowadza środowisko uruchomieniowe języka wspólnego, które jest przeznaczone do uproszczenia tworzenia i używania składników.</span><span class="sxs-lookup"><span data-stu-id="be342-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="be342-158">Ważnym aspektem tego uproszczenia jest ulepszona współpraca między składnikami zapisanymi przy użyciu różnych języków programowania.</span><span class="sxs-lookup"><span data-stu-id="be342-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="be342-159">Common Language Specification (CLS) umożliwia tworzenie narzędzi i składników, które współpracują z wieloma językami programowania.</span><span class="sxs-lookup"><span data-stu-id="be342-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="be342-160">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="be342-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="be342-161">Opisuje sposób włączania wyświetlania składnika lub kontrolki w oknie dialogowym **Dostosowywanie przybornika** .</span><span class="sxs-lookup"><span data-stu-id="be342-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
