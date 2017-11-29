---
title: "DomainUpDown — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0692677b8ef596bb31b1869480603573a9ec98d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="4eb87-102">DomainUpDown — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="4eb87-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="4eb87-103">Formularze systemu Windows <xref:System.Windows.Forms.DomainUpDown> formant jest zasadniczo kombinację pola tekstowego, a para przyciski przenoszenia w górę lub w dół listy.</span><span class="sxs-lookup"><span data-stu-id="4eb87-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="4eb87-104">Kontrolka Wyświetla i ustawia ciąg tekstowy, z listy dostępnych opcji.</span><span class="sxs-lookup"><span data-stu-id="4eb87-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="4eb87-105">Użytkownik może wybrać ciąg, kilikając przyciski, aby przejść na liście, naciskając klawisze strzałek w górę i w dół lub wpisując ciąg zgodny element na liście.</span><span class="sxs-lookup"><span data-stu-id="4eb87-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="4eb87-106">Jeden możliwości zastosowania dla tego formantu jest wybierania elementów z posortowane alfabetycznie listę nazw.</span><span class="sxs-lookup"><span data-stu-id="4eb87-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4eb87-107">Aby posortować listę, należy ustawić <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="4eb87-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="4eb87-108">Funkcja tego formantu jest bardzo podobny do pola listy lub pola kombi, ale zajmuje on bardzo mało miejsca.</span><span class="sxs-lookup"><span data-stu-id="4eb87-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="4eb87-109">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="4eb87-109">Key Properties</span></span>  
 <span data-ttu-id="4eb87-110">Właściwości klucza formantu są <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="4eb87-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="4eb87-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A> Właściwość zawiera listę obiektów, których wartości tekstowe są wyświetlane w formancie.</span><span class="sxs-lookup"><span data-stu-id="4eb87-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="4eb87-112">Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ma ustawioną wartość `false`, formantu automatycznie wykonuje tekstu, czy użytkownik, typy i dopasowuje je do wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="4eb87-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="4eb87-113">Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ma ustawioną wartość `true`, przewijanie poza ostatni element spowoduje przejście do pierwszego elementu na liście i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="4eb87-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="4eb87-114">Metody klucza formantu są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="4eb87-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="4eb87-115">Ten formant wyświetla tylko ciągi.</span><span class="sxs-lookup"><span data-stu-id="4eb87-115">This control displays only text strings.</span></span> <span data-ttu-id="4eb87-116">Formant, który wyświetla wartości liczbowe, należy użyć <xref:System.Windows.Forms.NumericUpDown> formantu.</span><span class="sxs-lookup"><span data-stu-id="4eb87-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="4eb87-117">Aby uzyskać więcej informacji, zobacz [informacje o formancie NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4eb87-117">For more information, see [NumericUpDown Control Overview](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb87-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4eb87-118">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 [<span data-ttu-id="4eb87-119">DomainUpDown — formant</span><span class="sxs-lookup"><span data-stu-id="4eb87-119">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
