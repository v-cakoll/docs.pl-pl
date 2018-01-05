---
title: 'Porady: dziedziczenie formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f190fb101a3ff666d194d854c9ce152657ebf85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="e8288-102">Porady: dziedziczenie formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e8288-102">How to: Inherit Windows Forms</span></span>
<span data-ttu-id="e8288-103">Tworzenie nowych formularzy systemu Windows przez dziedziczenie z formularzy podstawowy jest to wygodna metoda mają zostać zduplikowane starań bez pośrednictwa całkowicie odtworzenie formularza za każdym razem, gdy wymagają tego procesu.</span><span class="sxs-lookup"><span data-stu-id="e8288-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>  
  
 <span data-ttu-id="e8288-104">Aby uzyskać więcej informacji na temat dziedziczenie formularzy przy użyciu czasu projektowania **selektora dziedziczenia** okno dialogowe i jak wizualnie rozróżnienia poziomów zabezpieczeń dziedziczone formantów, zobacz [porady: dziedziczenie formularzy przy użyciu Okno dialogowe selektora dziedziczenia](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="e8288-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>  
  
 <span data-ttu-id="e8288-105">**Uwaga** aby dziedziczyć z formularza, pliku lub przestrzeni nazw zawierającej formularza musi skompilowano do pliku wykonywalnego lub DLL.</span><span class="sxs-lookup"><span data-stu-id="e8288-105">**Note** In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="e8288-106">Aby utworzyć projekt, wybierz **kompilacji** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="e8288-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="e8288-107">Ponadto odwołanie do przestrzeni nazw musi można dodać do klasy dziedziczy formularza.</span><span class="sxs-lookup"><span data-stu-id="e8288-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span> <span data-ttu-id="e8288-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="e8288-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e8288-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="e8288-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e8288-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e8288-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-inherit-a-form-programmatically"></a><span data-ttu-id="e8288-111">Aby programowo dziedziczą formularza</span><span class="sxs-lookup"><span data-stu-id="e8288-111">To inherit a form programmatically</span></span>  
  
1.  <span data-ttu-id="e8288-112">W klasie Dodaj odwołanie do przestrzeni nazw zawierający formularz, który chcesz dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="e8288-112">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>  
  
2.  <span data-ttu-id="e8288-113">W definicji klasy Dodaj odwołanie do formularza, aby dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="e8288-113">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="e8288-114">Odwołania powinny zawierać nazw, zawierający formularz, a następnie okres, a następnie nazwę samego formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="e8288-114">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 <span data-ttu-id="e8288-115">Przy dziedziczenie formularzy, należy pamiętać o tym, jakie problemy mogą się pojawić w odniesieniu do obsługi zdarzeń wywoływana dwukrotnie, ponieważ każde zdarzenie jest obsługiwane przez klasę podstawową i dziedziczonej klasie.</span><span class="sxs-lookup"><span data-stu-id="e8288-115">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="e8288-116">Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [Rozwiązywanie problemów z dziedziczone programów obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="e8288-116">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8288-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8288-117">See Also</span></span>  
 [<span data-ttu-id="e8288-118">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e8288-118">Inherits Statement</span></span>](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="e8288-119">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="e8288-119">Imports Statement (.NET Namespace and Type)</span></span>](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="e8288-120">using</span><span class="sxs-lookup"><span data-stu-id="e8288-120">using</span></span>](~/docs/csharp/language-reference/keywords/using.md)  
 [<span data-ttu-id="e8288-121">Efekty modyfikowania wyglądu formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="e8288-121">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [<span data-ttu-id="e8288-122">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="e8288-122">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
