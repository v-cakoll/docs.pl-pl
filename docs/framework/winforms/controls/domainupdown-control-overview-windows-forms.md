---
title: DomainUpDown — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: bfe3e7239f77c6f1a0d9bb46a96c704653b43364
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102859"
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="1f800-102">DomainUpDown — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="1f800-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="1f800-103">Formularze Windows <xref:System.Windows.Forms.DomainUpDown> formant jest zasadniczo kombinacji pola tekstowego, a parę przycisków przenoszenia w górę lub w dół na liście.</span><span class="sxs-lookup"><span data-stu-id="1f800-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="1f800-104">Kontrolka Wyświetla i ustawia ciąg tekstowy z listy dostępnych opcji.</span><span class="sxs-lookup"><span data-stu-id="1f800-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="1f800-105">Użytkownik może wybrać ciąg przez kliknięcie przycisków, aby przejść na liście w górę i w dół, przez naciśnięcie klawiszy strzałek w górę i w dół lub wpisując ciąg, który pasuje do elementu na liście.</span><span class="sxs-lookup"><span data-stu-id="1f800-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="1f800-106">Jedno możliwe użycie tej kontrolki jest służąca do wybierania elementów z alfabetycznie posortowaną listę nazw.</span><span class="sxs-lookup"><span data-stu-id="1f800-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f800-107">Aby posortować listę, należy ustawić <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="1f800-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="1f800-108">Funkcja ta kontrolka jest bardzo podobne do pola listy lub pola kombi, ale zajmuje on bardzo mało miejsca.</span><span class="sxs-lookup"><span data-stu-id="1f800-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="1f800-109">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="1f800-109">Key Properties</span></span>  
 <span data-ttu-id="1f800-110">Kluczowe właściwości kontrolki są <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f800-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="1f800-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A> Właściwość zawiera listę obiektów, których wartości tekstowe są wyświetlane w formancie.</span><span class="sxs-lookup"><span data-stu-id="1f800-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="1f800-112">Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ustawiono `false`, formant automatycznie wykonuje tekstu, że użytkownik wpisuje i dopasowuje je do wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="1f800-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="1f800-113">Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ustawiono `true`, przewijania po ostatnim elemencie spowoduje przejście do pierwszego elementu na liście i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="1f800-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="1f800-114">Metody klucza kontrolki są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f800-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="1f800-115">Ta kontrolka wyświetla tylko ciągi tekstowe.</span><span class="sxs-lookup"><span data-stu-id="1f800-115">This control displays only text strings.</span></span> <span data-ttu-id="1f800-116">Jeśli chcesz, aby formant, który wyświetla wartości liczbowe, użyj <xref:System.Windows.Forms.NumericUpDown> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1f800-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="1f800-117">Aby uzyskać więcej informacji, zobacz [— informacje o formancie NumericUpDown](numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1f800-117">For more information, see [NumericUpDown Control Overview](numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f800-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f800-118">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- [<span data-ttu-id="1f800-119">DomainUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="1f800-119">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
