---
title: 'Porady: dziedziczenie formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 275ae52a36ed9766e2569bd6c8ecdea78ea56e0b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43537149"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="84324-102">Porady: dziedziczenie formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="84324-102">How to: Inherit Windows Forms</span></span>
<span data-ttu-id="84324-103">Tworzenie nowych formularzy Windows przez dziedziczenie z formularzy podstawowy jest wygodny sposób zduplikowane starań bez przechodzenia przez proces całkowicie ponownego tworzenia formularza, za każdym razem, gdy jej potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="84324-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>  
  
 <span data-ttu-id="84324-104">Aby uzyskać więcej informacji na temat dziedziczenie formularzy przy użyciu czasu projektowania **selektor dziedziczenia** okno dialogowe i jak wizualnie rozróżnienie między poziomy zabezpieczeń dziedziczone formantów, zobacz [porady: dziedziczenie formularzy przy użyciu Selektor dziedziczenia — okno dialogowe](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="84324-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>  
  
 <span data-ttu-id="84324-105">**Uwaga** celu dziedziczą z formularza, pliku lub przestrzeni nazw, zawierające ten formularz musi zostały skompilowane do pliku wykonywalnego lub biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="84324-105">**Note** In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="84324-106">Aby skompilować projekt, wybierz opcję **kompilacji** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="84324-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="84324-107">Ponadto należy można dodać odwołania do przestrzeni nazw do klasy dziedziczące formularza.</span><span class="sxs-lookup"><span data-stu-id="84324-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span> <span data-ttu-id="84324-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="84324-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="84324-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="84324-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="84324-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="84324-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-inherit-a-form-programmatically"></a><span data-ttu-id="84324-111">Programowe dziedziczyć formularza</span><span class="sxs-lookup"><span data-stu-id="84324-111">To inherit a form programmatically</span></span>  
  
1.  <span data-ttu-id="84324-112">W klasie Dodaj odwołanie do przestrzeni nazw zawierający formularz, który chcesz dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="84324-112">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>  
  
2.  <span data-ttu-id="84324-113">W definicji klasy Dodaj odwołanie do formularza, aby dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="84324-113">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="84324-114">Odwołania powinny zawierać przestrzeń nazw zawierająca formularz, następuje kropka, a następnie nazwa podstawowa samego formularza.</span><span class="sxs-lookup"><span data-stu-id="84324-114">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 <span data-ttu-id="84324-115">Gdy dziedziczenie formularzy, należy pamiętać o tym, jakie problemy mogą się pojawić w odniesieniu do programów obsługi zdarzeń, wywoływana dwa razy, ponieważ każde zdarzenie jest obsługiwane zarówno przez klasę bazową i odziedziczoną klasę.</span><span class="sxs-lookup"><span data-stu-id="84324-115">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="84324-116">Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [Rozwiązywanie problemów z dziedziczone procedury obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="84324-116">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84324-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84324-117">See Also</span></span>  
 [<span data-ttu-id="84324-118">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="84324-118">Inherits Statement</span></span>](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="84324-119">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="84324-119">Imports Statement (.NET Namespace and Type)</span></span>](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="84324-120">using</span><span class="sxs-lookup"><span data-stu-id="84324-120">using</span></span>](~/docs/csharp/language-reference/keywords/using.md)  
 [<span data-ttu-id="84324-121">Efekty modyfikowania wyglądu formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="84324-121">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [<span data-ttu-id="84324-122">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="84324-122">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
