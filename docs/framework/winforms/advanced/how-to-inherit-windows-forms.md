---
title: Dziedziczenie formularza
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: cc3a4cc75fd13e8f193a6920ed5b4a9bc8fd5d74
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743323"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="14535-102">Porady: dziedziczenie formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="14535-102">How to: Inherit Windows Forms</span></span>

<span data-ttu-id="14535-103">Tworzenie nowych Windows Forms przez dziedziczenie z formularzy podstawowych jest wygodnym sposobem duplikowania najlepszych starań bez przechodzenia przez proces całkowitego odtwarzania formularza za każdym razem, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="14535-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>

<span data-ttu-id="14535-104">Aby uzyskać więcej informacji na temat dziedziczenia formularzy w czasie projektowania przy użyciu okna dialogowego **selektora dziedziczenia** oraz wizualnego rozróżniania poziomów zabezpieczeń dziedziczonych kontrolek, zobacz [How to: inherit Forms przy użyciu selektora dziedziczenia](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="14535-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>

> [!NOTE]
> <span data-ttu-id="14535-105">Aby można było dziedziczyć z formularza, plik lub przestrzeń nazw zawierające ten formularz muszą być wbudowane w plik wykonywalny lub DLL.</span><span class="sxs-lookup"><span data-stu-id="14535-105">In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="14535-106">Aby skompilować projekt, wybierz opcję **Kompiluj** z menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="14535-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="14535-107">Ponadto odwołanie do przestrzeni nazw należy dodać do klasy dziedziczonej w formularzu.</span><span class="sxs-lookup"><span data-stu-id="14535-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span>

## <a name="inherit-a-form-programmatically"></a><span data-ttu-id="14535-108">Programowe dziedziczenie formularza</span><span class="sxs-lookup"><span data-stu-id="14535-108">Inherit a form programmatically</span></span>

1. <span data-ttu-id="14535-109">W klasie Dodaj odwołanie do przestrzeni nazw zawierającej formularz, z którego chcesz dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="14535-109">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>

2. <span data-ttu-id="14535-110">W definicji klasy Dodaj odwołanie do formularza, aby dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="14535-110">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="14535-111">Odwołanie powinno zawierać przestrzeń nazw, która zawiera formularz, po którym następuje kropka, a następnie nazwę podstawowego formularza.</span><span class="sxs-lookup"><span data-stu-id="14535-111">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 <span data-ttu-id="14535-112">Podczas dziedziczenia formularzy należy pamiętać, że problemy mogą wystąpić w odniesieniu do programów obsługi zdarzeń, które są wywoływane dwa razy, ponieważ każde zdarzenie jest obsługiwane przez klasę bazową i dziedziczoną klasy.</span><span class="sxs-lookup"><span data-stu-id="14535-112">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="14535-113">Aby uzyskać więcej informacji na temat tego, jak uniknąć tego problemu, zobacz [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="14535-113">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14535-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14535-114">See also</span></span>

- [<span data-ttu-id="14535-115">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="14535-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="14535-116">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="14535-116">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="14535-117">using</span><span class="sxs-lookup"><span data-stu-id="14535-117">using</span></span>](../../../csharp/language-reference/keywords/using.md)
- [<span data-ttu-id="14535-118">Efekty modyfikowania wyglądu formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="14535-118">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)
- [<span data-ttu-id="14535-119">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="14535-119">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
