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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1eebca72b8c564e6d846eba69b6b59139754738e
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015979"
---
# <a name="develop-windows-forms-controls-at-design-time"></a><span data-ttu-id="d5d63-102">Opracowywanie formantów Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d5d63-102">Develop Windows Forms controls at design time</span></span>

<span data-ttu-id="d5d63-103">W przypadku autorów kontroli .NET Framework zapewnia mnóstwo technologii tworzenia kontroli.</span><span class="sxs-lookup"><span data-stu-id="d5d63-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="d5d63-104">Autorzy nie są już ograniczeni do projektowania kontrolek złożonych, które działają jako kolekcja istniejących kontrolek.</span><span class="sxs-lookup"><span data-stu-id="d5d63-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="d5d63-105">Za pomocą dziedziczenia można tworzyć własne kontrolki z istniejących wcześniej kontrolek złożonych lub wcześniej istniejących kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d5d63-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="d5d63-106">Możesz również projektować własne kontrolki implementujące niestandardowe malowanie.</span><span class="sxs-lookup"><span data-stu-id="d5d63-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="d5d63-107">Te opcje umożliwiają znaczną elastyczność projektowania i funkcjonalności interfejsu wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="d5d63-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="d5d63-108">Aby skorzystać z tych funkcji, należy zapoznać się z pojęciami programistycznymi opartymi na obiektach.</span><span class="sxs-lookup"><span data-stu-id="d5d63-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="d5d63-109">Nie jest konieczne dokładne zrozumienie dziedziczenia, ale może się okazać, że warto odnieść się do podstawowych informacji dotyczących [dziedziczenia (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="d5d63-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

<span data-ttu-id="d5d63-110">Jeśli chcesz utworzyć niestandardowe kontrolki do użycia w formularzach sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d5d63-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d5d63-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d5d63-111">In this section</span></span>

<span data-ttu-id="d5d63-112">[Przewodnik: Tworzenie kontrolki złożonej](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-112">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="d5d63-113">Pokazuje, jak utworzyć prosty formant złożony w C#.</span><span class="sxs-lookup"><span data-stu-id="d5d63-113">Shows how to create a simple composite control in C#.</span></span>

<span data-ttu-id="d5d63-114">[Przewodnik: Dziedziczenie z kontrolki Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-114">[Walkthrough: Inheriting from a Windows Forms Control](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="d5d63-115">Pokazuje, jak utworzyć prostą kontrolkę Windows Forms przy użyciu C#dziedziczenia w programie.</span><span class="sxs-lookup"><span data-stu-id="d5d63-115">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>

<span data-ttu-id="d5d63-116">[Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-116">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span></span>\
<span data-ttu-id="d5d63-117">Pokazuje, jak używać funkcji tagów inteligentnych w kontrolkach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d5d63-117">Shows how to use the smart tag feature on Windows Forms controls.</span></span>

<span data-ttu-id="d5d63-118">[Przewodnik: Serializacja kolekcji typów standardowych z za pomocą DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-118">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)</span></span>\
<span data-ttu-id="d5d63-119">Pokazuje, <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> jak używać atrybutu do serializacji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d5d63-119">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>

<span data-ttu-id="d5d63-120">[Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-120">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="d5d63-121">Pokazuje, jak debugować zachowanie formantu Windows Forms w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="d5d63-121">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>

<span data-ttu-id="d5d63-122">[Przewodnik: Tworzenie kontrolki Windows Forms, która wykorzystuje funkcje czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-122">[Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md)</span></span>\
<span data-ttu-id="d5d63-123">Pokazuje ścisłą integrację złożonego formantu ze środowiskiem projektowym.</span><span class="sxs-lookup"><span data-stu-id="d5d63-123">Shows how to tightly integrate a composite control into the design environment.</span></span>

<span data-ttu-id="d5d63-124">[Instrukcje: Kontrolki autora dla Windows Forms](how-to-author-controls-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-124">[How to: Author Controls for Windows Forms](how-to-author-controls-for-windows-forms.md)</span></span>\
<span data-ttu-id="d5d63-125">Zawiera omówienie zagadnień związanych z implementacją kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d5d63-125">Provides an overview of considerations for implementing a Windows Forms control.</span></span>

<span data-ttu-id="d5d63-126">[Instrukcje: Tworzenie złożonych kontrolek](how-to-author-composite-controls.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-126">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>\
<span data-ttu-id="d5d63-127">Pokazuje, jak utworzyć formant przez dziedziczenie z kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="d5d63-127">Shows how to create a control by inheriting from a composite control.</span></span>

<span data-ttu-id="d5d63-128">[Instrukcje: Dziedzicz z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-128">[How to: Inherit from the UserControl Class](how-to-inherit-from-the-usercontrol-class.md)</span></span>\
<span data-ttu-id="d5d63-129">Zawiera przegląd procedury tworzenia złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="d5d63-129">Provides an overview of the procedure for creating a composite control.</span></span>

<span data-ttu-id="d5d63-130">[Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-130">[How to: Inherit from Existing Windows Forms Controls](how-to-inherit-from-existing-windows-forms-controls.md)</span></span>\
<span data-ttu-id="d5d63-131">Pokazuje, jak utworzyć formant rozszerzony przez dziedziczenie z <xref:System.Windows.Forms.Button> klasy kontrolek.</span><span class="sxs-lookup"><span data-stu-id="d5d63-131">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>

<span data-ttu-id="d5d63-132">[Instrukcje: Dziedzicz z klasy kontrolki](how-to-inherit-from-the-control-class.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-132">[How to: Inherit from the Control Class](how-to-inherit-from-the-control-class.md)</span></span>\
<span data-ttu-id="d5d63-133">Zawiera omówienie tworzenia rozszerzonej kontroli.</span><span class="sxs-lookup"><span data-stu-id="d5d63-133">Provides an overview of creating an extended control.</span></span>

<span data-ttu-id="d5d63-134">[Instrukcje: Wyrównywanie kontrolki do krawędzi formularzy w czasie projektowania](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-134">[How to: Align a Control to the Edges of Forms at Design Time](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span></span>\
<span data-ttu-id="d5d63-135">Pokazuje, w jaki sposób <xref:System.Windows.Forms.Control.Dock%2A> używać właściwości, aby wyrównać formant do krawędzi formularza, który on zajmowan.</span><span class="sxs-lookup"><span data-stu-id="d5d63-135">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="d5d63-136">[Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-136">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>\
<span data-ttu-id="d5d63-137">Pokazuje procedurę instalowania kontrolki tak, aby była widoczna w oknie dialogowym **Dostosowywanie przybornika** .</span><span class="sxs-lookup"><span data-stu-id="d5d63-137">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>

<span data-ttu-id="d5d63-138">[Instrukcje: Udostępnianie mapy bitowej przybornika dla kontrolki](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-138">[How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span></span>\
<span data-ttu-id="d5d63-139">Pokazuje, <xref:System.Drawing.ToolboxBitmapAttribute> jak używać do wyświetlania ikony obok kontrolki niestandardowej w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="d5d63-139">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="d5d63-140">[Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-140">[How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span></span>\
<span data-ttu-id="d5d63-141">Pokazuje, jak używać obiektu **UserControl Test Container** do testowania zachowania złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="d5d63-141">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>

<span data-ttu-id="d5d63-142">[Błędy czasu projektowania w Projektant formularzy systemu Windows](design-time-errors-in-the-windows-forms-designer.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-142">[Design-Time Errors in the Windows Forms Designer](design-time-errors-in-the-windows-forms-designer.md)</span></span>\
<span data-ttu-id="d5d63-143">Wyjaśnia znaczenie i użycie Lista błędów czasu projektowania, które pojawiają się w Microsoft Visual Studio w przypadku niepowodzenia załadowania projektanta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d5d63-143">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>

<span data-ttu-id="d5d63-144">[Kontrola i Tworzenie składników rozwiązywania problemów](troubleshooting-control-and-component-authoring.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-144">[Troubleshooting Control and Component Authoring](troubleshooting-control-and-component-authoring.md)</span></span>\
<span data-ttu-id="d5d63-145">Pokazuje, jak diagnozować i rozwiązywać typowe problemy, które mogą wystąpić podczas tworzenia niestandardowego składnika lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d5d63-145">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>

## <a name="reference"></a><span data-ttu-id="d5d63-146">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d5d63-146">Reference</span></span>

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a><span data-ttu-id="d5d63-147">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d5d63-147">Related sections</span></span>

<span data-ttu-id="d5d63-148">[Tworzenie niestandardowych kontrolek Windows Forms przy użyciu .NET Framework](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-148">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="d5d63-149">W tym artykule omówiono sposób tworzenia własnych niestandardowych kontrolek przy użyciu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5d63-149">Discusses how to create your own custom controls with the .NET Framework.</span></span>

<span data-ttu-id="d5d63-150">[Niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-150">[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)</span></span>\
<span data-ttu-id="d5d63-151">Wprowadza środowisko uruchomieniowe języka wspólnego, które jest przeznaczone do uproszczenia tworzenia i używania składników.</span><span class="sxs-lookup"><span data-stu-id="d5d63-151">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="d5d63-152">Ważnym aspektem tego uproszczenia jest ulepszona współpraca między składnikami zapisanymi przy użyciu różnych języków programowania.</span><span class="sxs-lookup"><span data-stu-id="d5d63-152">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="d5d63-153">Common Language Specification (CLS) umożliwia tworzenie narzędzi i składników, które współpracują z wieloma językami programowania.</span><span class="sxs-lookup"><span data-stu-id="d5d63-153">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>

<span data-ttu-id="d5d63-154">[Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span><span class="sxs-lookup"><span data-stu-id="d5d63-154">[Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span></span>\
<span data-ttu-id="d5d63-155">Opisuje sposób włączania wyświetlania składnika lub kontrolki w oknie dialogowym **Dostosowywanie przybornika** .</span><span class="sxs-lookup"><span data-stu-id="d5d63-155">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
