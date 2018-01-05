---
title: "DomainUpDown — Formant (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 485640dc320809e9be5550d380b4fc9a2326e027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="domainupdown-control-windows-forms"></a><span data-ttu-id="2a836-102">DomainUpDown — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="2a836-102">DomainUpDown Control (Windows Forms)</span></span>
<span data-ttu-id="2a836-103">Formularze systemu Windows <xref:System.Windows.Forms.DomainUpDown> formant wygląda kombinację pole tekstowe i parę przyciski przenoszenia w górę lub w dół listy.</span><span class="sxs-lookup"><span data-stu-id="2a836-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control looks like a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="2a836-104">Kontrolka Wyświetla i ustawia ciąg tekstowy, z listy dostępnych opcji.</span><span class="sxs-lookup"><span data-stu-id="2a836-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="2a836-105">Użytkownik może wybrać ciąg, kilikając przyciski, aby przejść na liście, naciskając klawisze strzałek w górę i w dół lub wpisując ciąg zgodny element na liście.</span><span class="sxs-lookup"><span data-stu-id="2a836-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="2a836-106">Jeden możliwości zastosowania dla tego formantu jest wybierania elementów z posortowane alfabetycznie listę nazw.</span><span class="sxs-lookup"><span data-stu-id="2a836-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span> <span data-ttu-id="2a836-107">(Aby posortować listę, należy ustawić <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> właściwości `true`.) Funkcja tego formantu jest bardzo podobny do pola listy lub pola kombi, ale zajmuje on bardzo mało miejsca.</span><span class="sxs-lookup"><span data-stu-id="2a836-107">(To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.) The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
 <span data-ttu-id="2a836-108">Właściwości klucza formantu są <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a836-108">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="2a836-109"><xref:System.Windows.Forms.DomainUpDown.Items%2A> Właściwość zawiera listę obiektów, których wartości tekstowe są wyświetlane w formancie.</span><span class="sxs-lookup"><span data-stu-id="2a836-109">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="2a836-110">Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ma ustawioną wartość `false`, formantu automatycznie wykonuje tekstu, czy użytkownik, typy i dopasowuje je do wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="2a836-110">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="2a836-111">Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ma ustawioną wartość `true`, przewijanie poza ostatni element spowoduje przejście do pierwszego elementu na liście i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="2a836-111">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="2a836-112">Metody klucza formantu są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a836-112">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="2a836-113">Ten formant wyświetla tylko ciągi.</span><span class="sxs-lookup"><span data-stu-id="2a836-113">This control displays only text strings.</span></span> <span data-ttu-id="2a836-114">Formant, który wyświetla wartości liczbowe, należy użyć <xref:System.Windows.Forms.NumericUpDown> formantu.</span><span class="sxs-lookup"><span data-stu-id="2a836-114">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="2a836-115">Aby uzyskać więcej informacji, zobacz [formantu NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span><span class="sxs-lookup"><span data-stu-id="2a836-115">For more information, see [NumericUpDown Control](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a836-116">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2a836-116">In This Section</span></span>  
 [<span data-ttu-id="2a836-117">DomainUpDown, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2a836-117">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 <span data-ttu-id="2a836-118">Ogólne pojęcia związane z <xref:System.Windows.Forms.DomainUpDown> kontroli, co umożliwi użytkownikom do przeglądania i wybrać z listy ciągów tekstowych.</span><span class="sxs-lookup"><span data-stu-id="2a836-118">Introduces the general concepts of the <xref:System.Windows.Forms.DomainUpDown> control, which allows users to browse through and select from a list of text strings.</span></span>  
  
 [<span data-ttu-id="2a836-119">Instrukcje: dodawanie w sposób programowy elementów do kontrolki DomainUpDown formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a836-119">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 <span data-ttu-id="2a836-120">Opisuje sposób określenia ciągów tekstowych <xref:System.Windows.Forms.DomainUpDown> powinien być wyświetlany przez formant.</span><span class="sxs-lookup"><span data-stu-id="2a836-120">Describes how to specify the text strings the <xref:System.Windows.Forms.DomainUpDown> control should display.</span></span>  
  
 [<span data-ttu-id="2a836-121">Instrukcje: usuwanie elementów z kontrolki DomainUpDown formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a836-121">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 <span data-ttu-id="2a836-122">Opisuje sposób usuwania pozycji z <xref:System.Windows.Forms.DomainUpDown> kontroli w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2a836-122">Describes how to delete items from the <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2a836-123">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="2a836-123">Reference</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <span data-ttu-id="2a836-124">Ta klasa opisuje i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="2a836-124">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 <span data-ttu-id="2a836-125">Ta klasa opisuje i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="2a836-125">Describes this class and has links to all its members..</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2a836-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2a836-126">Related Sections</span></span>  
 [<span data-ttu-id="2a836-127">Formanty, które można używać w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2a836-127">Controls You Can Use On Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="2a836-128">Zawiera listę wszystkich formanty formularzy systemu Windows, linki do informacji na temat ich użycia.</span><span class="sxs-lookup"><span data-stu-id="2a836-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
