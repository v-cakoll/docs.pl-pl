---
title: Opracowywanie złożonego formantu formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 9ccbf3de3f5c65b99a06c29ffce4c96896d11fae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015954"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="d59c0-102">Opracowywanie złożonego formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d59c0-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="d59c0-103">Możesz opracować formant Windows Forms złożone przez połączenie innych kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d59c0-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="d59c0-104">Kontrolki złożone pochodne od <xref:System.Web.UI.UserControl> są nazywane kontrolkami użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d59c0-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="d59c0-105">Klasa bazowa, <xref:System.Windows.Forms.UserControl>, zapewnia Routing klawiatury dla formantów podrzędnych, dzięki czemu można uzyskać fokus formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="d59c0-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="d59c0-106">Aby zapoznać się z przykładem kontrolki użytkownika, <xref:System.Windows.Forms.UserControl> Zobacz przykład [w temacie How to: Zastosuj atrybuty w kontrolkach](how-to-apply-attributes-in-windows-forms-controls.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d59c0-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="d59c0-107">Projektant Windows Forms w programie Visual Studio zapewnia rozbudowaną obsługę tworzenia formantów użytkownika w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="d59c0-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="d59c0-108">Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="d59c0-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="d59c0-109">Przewodnik: Serializacja kolekcji typów standardowych z za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="d59c0-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="d59c0-110">Przewodnik: Dziedziczenie z kontrolki Windows Forms za pomocą wizualizacjiC#</span><span class="sxs-lookup"><span data-stu-id="d59c0-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="d59c0-111">Instrukcje: Udostępnianie mapy bitowej przybornika dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="d59c0-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="d59c0-112">Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d59c0-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="d59c0-113">Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d59c0-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="d59c0-114">Instrukcje: Dziedzicz z klasy kontrolki</span><span class="sxs-lookup"><span data-stu-id="d59c0-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="d59c0-115">Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="d59c0-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="d59c0-116">Instrukcje: Wyrównywanie kontrolki do krawędzi formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d59c0-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="d59c0-117">Instrukcje: Dziedzicz z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="d59c0-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="d59c0-118">Instrukcje: Kontrolki autora dla Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d59c0-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="d59c0-119">Instrukcje: Tworzenie złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="d59c0-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="d59c0-120">Przewodnik: Tworzenie formantu złożonego za pomocą wizualizacjiC#</span><span class="sxs-lookup"><span data-stu-id="d59c0-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="d59c0-121">Przewodnik: Tworzenie kontrolki Windows Forms, która wykorzystuje funkcje czasu projektowania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d59c0-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="d59c0-122">[Instrukcje: Utwórz formant Windows Forms, który korzysta z funkcji czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="d59c0-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="d59c0-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d59c0-123">See also</span></span>

- [<span data-ttu-id="d59c0-124">Instrukcje: Zastosuj atrybuty w kontrolkach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d59c0-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="d59c0-125">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d59c0-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="d59c0-126">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d59c0-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
