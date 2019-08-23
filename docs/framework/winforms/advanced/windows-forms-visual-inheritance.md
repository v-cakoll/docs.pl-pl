---
title: Formularze systemu Windows — dziedziczenie Visual
ms.date: 03/30/2017
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
ms.openlocfilehash: 11a90615938da9e7dda5e05c55546918ccde137d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957104"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="e1cba-102">Formularze systemu Windows — dziedziczenie Visual</span><span class="sxs-lookup"><span data-stu-id="e1cba-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="e1cba-103">Czasami możesz zdecydować, że projekt wywołuje formularz podobny do tego, który został utworzony w poprzednim projekcie.</span><span class="sxs-lookup"><span data-stu-id="e1cba-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="e1cba-104">Można też utworzyć podstawową formę z ustawieniami, takimi jak znak wodny lub określony układ kontroli, który będzie następnie używany ponownie w projekcie, z każdą iteracją zawierającą modyfikacje oryginalnego szablonu formularza.</span><span class="sxs-lookup"><span data-stu-id="e1cba-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="e1cba-105">Dziedziczenie formularzy umożliwia tworzenie formularza podstawowego, a następnie dziedziczenie i dokonywanie modyfikacji oraz zachowanie wszelkich potrzebnych oryginalnych ustawień.</span><span class="sxs-lookup"><span data-stu-id="e1cba-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="e1cba-106">Można tworzyć formularze klasy pochodnej programowo lub za pomocą selektora dziedziczenia wizualnego.</span><span class="sxs-lookup"><span data-stu-id="e1cba-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1cba-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e1cba-107">In This Section</span></span>  
 [<span data-ttu-id="e1cba-108">Instrukcje: Dziedzicz Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1cba-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="e1cba-109">Zawiera wskazówki dotyczące tworzenia dziedziczonych formularzy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e1cba-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="e1cba-110">Instrukcje: Dziedzicz formularze przy użyciu okna dialogowego selektora dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="e1cba-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="e1cba-111">Zawiera wskazówki dotyczące tworzenia dziedziczonych formularzy przy użyciu selektora dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e1cba-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="e1cba-112">Efekty modyfikowania wyglądu formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="e1cba-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="e1cba-113">Daje wskazówki dotyczące zmiany kontrolek formularza podstawowego i ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="e1cba-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="e1cba-114">Przewodnik: Demonstrowanie dziedziczenia wizualnego</span><span class="sxs-lookup"><span data-stu-id="e1cba-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="e1cba-115">Opisuje sposób tworzenia podstawowego formularza systemu Windows i kompilowania go w bibliotece klas.</span><span class="sxs-lookup"><span data-stu-id="e1cba-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="e1cba-116">Ta biblioteka klas zostanie zaimportowana do innego projektu i zostanie utworzony nowy formularz, który dziedziczy po formularzu podstawowym.</span><span class="sxs-lookup"><span data-stu-id="e1cba-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="e1cba-117">Instrukcje: Używanie modyfikatorów i właściwości GenerateMember</span><span class="sxs-lookup"><span data-stu-id="e1cba-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="e1cba-118">Daje wskazówki dotyczące używania `GenerateMember` właściwości i `Modifiers` , które są istotne, gdy Projektant formularzy systemu Windows generuje zmienną członkowską dla składnika.</span><span class="sxs-lookup"><span data-stu-id="e1cba-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e1cba-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e1cba-119">Related Sections</span></span>  
 [<span data-ttu-id="e1cba-120">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1cba-120">Inheritance basics (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="e1cba-121">Opisuje sposób definiowania klas Visual Basic, które stanowią podstawę dla innych klas.</span><span class="sxs-lookup"><span data-stu-id="e1cba-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="e1cba-122">class</span><span class="sxs-lookup"><span data-stu-id="e1cba-122">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="e1cba-123">Opisuje C# podejście klas, w których dozwolone jest pojedyncze dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="e1cba-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="e1cba-124">Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1cba-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="e1cba-125">Wyświetla listę typowych problemów występujących w przypadku programów obsługi zdarzeń w składnikach dziedziczonych</span><span class="sxs-lookup"><span data-stu-id="e1cba-125">Lists common issues that arise with event handlers in inherited components</span></span>
