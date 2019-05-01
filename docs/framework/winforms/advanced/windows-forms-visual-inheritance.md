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
ms.openlocfilehash: e94cdc38b97f95cfe8a8504733298525c25667df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011869"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="80e6a-102">Formularze systemu Windows — dziedziczenie Visual</span><span class="sxs-lookup"><span data-stu-id="80e6a-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="80e6a-103">Od czasu do czasu może zdecydować, że projekt wymaga formularz podobny do jednego, utworzony w poprzednim projektu.</span><span class="sxs-lookup"><span data-stu-id="80e6a-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="80e6a-104">Możesz też utworzyć podstawowy formularz przy użyciu ustawień, takich jak znak wodny lub niektórych układu kontrolki, która będzie następnie używana ponownie w ramach projektu, z każdą iteracją, zawierający modyfikacji oryginalnego szablonu formularza.</span><span class="sxs-lookup"><span data-stu-id="80e6a-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="80e6a-105">Dziedziczenie formularzy pozwala na tworzenie formularza podstawowego, a następnie dziedziczyć po nim i wprowadź zmiany przy jednoczesnym zachowaniu niezależnie od oryginalnego ustawienia, należy.</span><span class="sxs-lookup"><span data-stu-id="80e6a-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="80e6a-106">Klasa pochodna formularzy można utworzyć programowo lub za pomocą selektora dziedziczenia Visual.</span><span class="sxs-lookup"><span data-stu-id="80e6a-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80e6a-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="80e6a-107">In This Section</span></span>  
 [<span data-ttu-id="80e6a-108">Instrukcje: Dziedziczenie formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="80e6a-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="80e6a-109">Zawiera wskazówki dotyczące tworzenia odziedziczone formularze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="80e6a-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="80e6a-110">Instrukcje: Dziedziczenie formularzy przy użyciu okna dialogowego selektora dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="80e6a-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="80e6a-111">Zawiera wskazówki dotyczące tworzenia odziedziczone formularze za pomocą selektora dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="80e6a-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="80e6a-112">Efekty modyfikowania wyglądu formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="80e6a-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="80e6a-113">Zawiera wskazówki dotyczące zmieniania kontrolki formularza podstawowego i ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="80e6a-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="80e6a-114">Przewodnik: Demonstrowanie dziedziczenia wizualizacji</span><span class="sxs-lookup"><span data-stu-id="80e6a-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="80e6a-115">W tym artykule opisano sposób tworzenia formularza Windows podstawowego i skompiluj go do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="80e6a-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="80e6a-116">Będzie zaimportować tej biblioteki klas do innego projektu, a następnie utworzyć nowy formularz, który dziedziczy z formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="80e6a-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="80e6a-117">Instrukcje: Stosowanie modyfikatorów i właściwości "generatemember"</span><span class="sxs-lookup"><span data-stu-id="80e6a-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="80e6a-118">Zawiera wskazówki dotyczące używania `GenerateMember` i `Modifiers` właściwości, które są istotne, generując zmienną składową dla składnika Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="80e6a-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="80e6a-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="80e6a-119">Related Sections</span></span>  
 [<span data-ttu-id="80e6a-120">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80e6a-120">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="80e6a-121">W tym artykule opisano sposób definiowania klas języka Visual Basic, które stanowią podstawę dla innych klas.</span><span class="sxs-lookup"><span data-stu-id="80e6a-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="80e6a-122">class</span><span class="sxs-lookup"><span data-stu-id="80e6a-122">class</span></span>](~/docs/csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="80e6a-123">W tym artykule opisano C# podejście klas, w których pojedyncze dziedziczenie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="80e6a-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="80e6a-124">Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80e6a-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="80e6a-125">Zawiera listę typowych problemów, które wynikają z programami obsługi zdarzeń w składnikach dziedziczone</span><span class="sxs-lookup"><span data-stu-id="80e6a-125">Lists common issues that arise with event handlers in inherited components</span></span>
