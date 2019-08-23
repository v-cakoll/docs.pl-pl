---
title: DomainUpDown — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965300"
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="9c557-102">DomainUpDown — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="9c557-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="9c557-103">Formant Windows Forms <xref:System.Windows.Forms.DomainUpDown> jest zasadniczo połączeniem pola tekstowego i pary przycisków do przesuwania w górę lub w dół na liście.</span><span class="sxs-lookup"><span data-stu-id="9c557-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="9c557-104">Kontrolka wyświetla i ustawia ciąg tekstowy z listy wyborów.</span><span class="sxs-lookup"><span data-stu-id="9c557-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="9c557-105">Użytkownik może wybrać ciąg, klikając przyciski w górę i w dół, aby przejść przez listę, naciskając klawisze strzałek w górę i w dół lub wpisując ciąg, który pasuje do elementu na liście.</span><span class="sxs-lookup"><span data-stu-id="9c557-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="9c557-106">Jednym z możliwych użycia dla tej kontrolki jest wybranie elementów z listy alfabetycznie posortowanej.</span><span class="sxs-lookup"><span data-stu-id="9c557-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c557-107">Aby posortować listę, ustaw <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> właściwość na. `true`</span><span class="sxs-lookup"><span data-stu-id="9c557-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="9c557-108">Funkcja tego formantu jest bardzo podobna do pola listy lub pola kombi, ale zajmuje bardzo mało miejsca.</span><span class="sxs-lookup"><span data-stu-id="9c557-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="9c557-109">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="9c557-109">Key Properties</span></span>  
 <span data-ttu-id="9c557-110">Właściwości klucza kontrolki to <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c557-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="9c557-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A> Właściwość zawiera listę obiektów, których wartości tekstowe są wyświetlane w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="9c557-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="9c557-112">Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> jest ustawiona na `false`, formant automatycznie uzupełnia tekst, który jest typem użytkownika i dopasowuje go do wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="9c557-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="9c557-113">Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> jest ustawiona na `true`, przewijanie do ostatniego elementu spowoduje przejście do pierwszego elementu na liście i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="9c557-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="9c557-114">Kluczowymi metodami formantu są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i. <xref:System.Windows.Forms.DomainUpDown.DownButton%2A></span><span class="sxs-lookup"><span data-stu-id="9c557-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="9c557-115">Ta kontrolka wyświetla tylko ciągi tekstowe.</span><span class="sxs-lookup"><span data-stu-id="9c557-115">This control displays only text strings.</span></span> <span data-ttu-id="9c557-116">Jeśli chcesz, aby kontrolka, która wyświetla wartości liczbowe, <xref:System.Windows.Forms.NumericUpDown> używała kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9c557-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="9c557-117">Aby uzyskać więcej informacji, zobacz [NumericUpDown Control — Omówienie](numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9c557-117">For more information, see [NumericUpDown Control Overview](numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c557-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c557-118">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- [<span data-ttu-id="9c557-119">DomainUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9c557-119">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
