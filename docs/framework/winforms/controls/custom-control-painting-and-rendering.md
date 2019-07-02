---
title: Malowanie i renderowanie formantu niestandardowego
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 14abac5678bfffa3cdb61307fd3cb54681c82a99
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506086"
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="bfee1-102">Malowanie i renderowanie formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="bfee1-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="bfee1-103">Malowanie niestandardowych formantów jest jednym z wielu zadań skomplikowane, łatwe w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfee1-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="bfee1-104">Podczas tworzenia niestandardowego formantu, masz wiele opcji dotyczących kontroli nad wyglądem graficznego.</span><span class="sxs-lookup"><span data-stu-id="bfee1-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="bfee1-105">Jeśli tworzony formant, który dziedziczy z `Control`, należy podać kod, który umożliwia formantu do renderowania jej graficzną reprezentację.</span><span class="sxs-lookup"><span data-stu-id="bfee1-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="bfee1-106">Jeśli utworzysz formant użytkownika przez dziedziczenie z `UserControl`, lub są dziedziczone z jednej z kontrolek Windows Forms, może zastąpić standardowa graficzną reprezentację i podanie kodu grafiki.</span><span class="sxs-lookup"><span data-stu-id="bfee1-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="bfee1-107">Jeśli chcesz udostępnić niestandardowe renderowanie kontrolek składowych `UserControl` tworzenia, opcje stają się bardziej ograniczone, ale nadal zezwalają na szeroką gamę możliwości graficznego dla aplikacji i formantów.</span><span class="sxs-lookup"><span data-stu-id="bfee1-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bfee1-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bfee1-108">In This Section</span></span>  
 [<span data-ttu-id="bfee1-109">Renderowanie kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bfee1-109">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)  
 <span data-ttu-id="bfee1-110">Pokazuje, jak program logikę, która wyświetla kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="bfee1-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="bfee1-111">Kontrolki rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="bfee1-111">User-Drawn Controls</span></span>](user-drawn-controls.md)  
 <span data-ttu-id="bfee1-112">Zestawienie etapy pisania i zastępowanie kod renderowania dla formantu.</span><span class="sxs-lookup"><span data-stu-id="bfee1-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="bfee1-113">Kontrolki składników</span><span class="sxs-lookup"><span data-stu-id="bfee1-113">Constituent Controls</span></span>](constituent-controls.md)  
 <span data-ttu-id="bfee1-114">W tym artykule opisano, jak implementować niestandardowe renderowanie kodu dla składowych kontrolek formularzy i kontrolek użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bfee1-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="bfee1-115">Instrukcje: Ukrywanie formantu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="bfee1-115">How to: Make Your Control Invisible at Run Time</span></span>](how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="bfee1-116">Ilustruje sposób używania <xref:System.Windows.Forms.Control.Visible%2A> właściwości, aby ukryć i pokazać kontrolki.</span><span class="sxs-lookup"><span data-stu-id="bfee1-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="bfee1-117">Instrukcje: Zachować kontrolę z przezroczystym tłem</span><span class="sxs-lookup"><span data-stu-id="bfee1-117">How to: Give Your Control a Transparent Background</span></span>](how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="bfee1-118">Ilustruje sposób używania <xref:System.Windows.Forms.Control.SetStyle%2A> metodę w celu utworzenia kolor tła nieprzezroczyste, przezroczysta lub częściowo przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="bfee1-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="bfee1-119">Renderowanie kontrolek przy użyciu stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="bfee1-119">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="bfee1-120">Przedstawia sposób renderowania kontrolek przy użyciu stylów wizualnych w systemach operacyjnych, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="bfee1-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bfee1-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="bfee1-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="bfee1-122">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="bfee1-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="bfee1-123">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="bfee1-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="bfee1-124">W tym artykule opisano tę metodę.</span><span class="sxs-lookup"><span data-stu-id="bfee1-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bfee1-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bfee1-125">Related Sections</span></span>  
 [<span data-ttu-id="bfee1-126">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="bfee1-126">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="bfee1-127">Wprowadza funkcje graficzne interfejsu GDI + z punktu widzenia programu Visual Studio i zawiera linki do dodatkowych informacji.</span><span class="sxs-lookup"><span data-stu-id="bfee1-127">Introduces GDI+ graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="bfee1-128">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="bfee1-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="bfee1-129">W tym artykule opisano rodzaje niestandardowe formanty, które można tworzyć.</span><span class="sxs-lookup"><span data-stu-id="bfee1-129">Describes the kinds of custom controls you can author.</span></span>
