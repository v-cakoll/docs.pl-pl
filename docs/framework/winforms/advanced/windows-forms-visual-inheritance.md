---
title: "Formularze systemu Windows — dziedziczenie Visual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 177b3034e9afc71a8ecc899364cc4911ef42a1a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="25f47-102">Formularze systemu Windows — dziedziczenie Visual</span><span class="sxs-lookup"><span data-stu-id="25f47-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="25f47-103">Czasami może zdecydować, że projekt odwołuje się do formularza podobny do utworzonego w poprzednim projekcie.</span><span class="sxs-lookup"><span data-stu-id="25f47-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="25f47-104">Możesz też utworzyć podstawowy formularz z ustawienia, takie jak znak wodny lub niektórych układ formantu, który zostanie następnie ponownie użyć w projekcie, a każda iteracja zawierającą zmiany w oryginalnym szablonie formularza.</span><span class="sxs-lookup"><span data-stu-id="25f47-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="25f47-105">Dziedziczenie formularzy umożliwia tworzenie formularza podstawowego, a następnie dziedziczyć po nim i wprowadź zmiany, zachowując niezależnie od oryginalnego ustawienia potrzebne.</span><span class="sxs-lookup"><span data-stu-id="25f47-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="25f47-106">Można utworzyć formularze klas pochodnych programowo lub przy użyciu selektora dziedziczenia Visual.</span><span class="sxs-lookup"><span data-stu-id="25f47-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25f47-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="25f47-107">In This Section</span></span>  
 [<span data-ttu-id="25f47-108">Instrukcje: dziedziczenie formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25f47-108">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 <span data-ttu-id="25f47-109">Zawiera wskazówki dotyczące tworzenia odziedziczone formularze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="25f47-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="25f47-110">Instrukcje: dziedziczenie formularzy korzystających z okna dialogowego selektora dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="25f47-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="25f47-111">Zawiera wskazówki dotyczące tworzenia formularzy dziedziczone z selektora dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="25f47-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="25f47-112">Efekty modyfikowania wyglądu formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="25f47-112">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="25f47-113">Zawiera wskazówki dotyczące zmieniania kontrolek formularza podstawowego i ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="25f47-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="25f47-114">Przewodnik: demonstrowanie dziedziczenia wizualizacji</span><span class="sxs-lookup"><span data-stu-id="25f47-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="25f47-115">Opisuje sposób tworzenia podstawowej formularza systemu Windows i skompiluj go do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="25f47-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="25f47-116">Zostanie zaimportować tę bibliotekę klas do innego projektu, a następnie utwórz nowy formularz, który dziedziczy z formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="25f47-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="25f47-117">Instrukcje: stosowanie modyfikatorów i właściwości GenerateMember</span><span class="sxs-lookup"><span data-stu-id="25f47-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="25f47-118">Zawiera wskazówki dotyczące korzystania z `GenerateMember` i `Modifiers` właściwości, które mają zastosowanie, gdy projektant formularzy systemu Windows generuje zmienną członkowską dla składnika.</span><span class="sxs-lookup"><span data-stu-id="25f47-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="25f47-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="25f47-119">Related Sections</span></span>  
 [<span data-ttu-id="25f47-120">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25f47-120">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="25f47-121">Opisuje sposób definiowania klas języka Visual Basic, które stanowią podstawę dla innych klas.</span><span class="sxs-lookup"><span data-stu-id="25f47-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="25f47-122">class</span><span class="sxs-lookup"><span data-stu-id="25f47-122">class</span></span>](~/docs/csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="25f47-123">Opisuje metody C# klas, w których jest dozwolona pojedyncze dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="25f47-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="25f47-124">Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25f47-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="25f47-125">Wyświetla listę typowych problemów, które wynikają z obsługi zdarzeń w składników odziedziczonych</span><span class="sxs-lookup"><span data-stu-id="25f47-125">Lists common issues that arise with event handlers in inherited components</span></span>
