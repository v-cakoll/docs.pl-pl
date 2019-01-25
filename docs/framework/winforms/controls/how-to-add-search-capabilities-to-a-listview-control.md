---
title: 'Instrukcje: Dodawanie możliwości wyszukiwania do formantu ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
ms.openlocfilehash: 0f8b9535539f7f9cd8d0c8ba3a362e9ab7bef03a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716794"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a><span data-ttu-id="37174-102">Instrukcje: Dodawanie możliwości wyszukiwania do formantu ListView</span><span class="sxs-lookup"><span data-stu-id="37174-102">How to: Add Search Capabilities to a ListView Control</span></span>
<span data-ttu-id="37174-103">Często, podczas pracy z dużą listy elementów w <xref:System.Windows.Forms.ListView> kontrolki, mają być oferowane możliwości wyszukiwania do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="37174-103">Oftentimes when working with a large list of items in a <xref:System.Windows.Forms.ListView> control, you want to offer search capabilities to the user.</span></span> <span data-ttu-id="37174-104"><xref:System.Windows.Forms.ListView> Formant oferuje tej funkcji na dwa sposoby: tekst dopasowywanie i wyszukiwanie w lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="37174-104">The <xref:System.Windows.Forms.ListView> control offers this capability in two different ways: text matching and location searching.</span></span>  
  
 <span data-ttu-id="37174-105"><xref:System.Windows.Forms.ListView.FindItemWithText%2A> Metoda umożliwia wyszukiwanie tekstu w <xref:System.Windows.Forms.ListView> w widoku listy lub szczegółów danego ciągu wyszukiwania i opcjonalne początkowe i końcowe indeksu.</span><span class="sxs-lookup"><span data-stu-id="37174-105">The <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method allows you to perform a text search on a <xref:System.Windows.Forms.ListView> in list or details view, given a search string and an optional starting and ending index.</span></span> <span data-ttu-id="37174-106">Z kolei <xref:System.Windows.Forms.ListView.FindNearestItem%2A> metoda umożliwia znajdowanie element <xref:System.Windows.Forms.ListView> w widoku ikon lub Kafelek, biorąc pod uwagę zestaw współrzędnych x i y i kierunek wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="37174-106">In contrast, the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method allows you to find an item in a <xref:System.Windows.Forms.ListView> in icon or tile view, given a set of x- and y-coordinates and a direction to search.</span></span>  
  
### <a name="to-find-an-item-using-text"></a><span data-ttu-id="37174-107">Aby znaleźć element przy użyciu tekstu</span><span class="sxs-lookup"><span data-stu-id="37174-107">To find an item using text</span></span>  
  
1.  <span data-ttu-id="37174-108">Tworzenie <xref:System.Windows.Forms.ListView> za pomocą <xref:System.Windows.Forms.ListView.View%2A> właściwością <xref:System.Windows.Forms.View.Details> lub <xref:System.Windows.Forms.View.List>, a następnie wypełnij <xref:System.Windows.Forms.ListView> z elementami.</span><span class="sxs-lookup"><span data-stu-id="37174-108">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.ListView.View%2A> property set to <xref:System.Windows.Forms.View.Details> or <xref:System.Windows.Forms.View.List>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="37174-109">Wywołaj <xref:System.Windows.Forms.ListView.FindItemWithText%2A> jest metoda tekstu elementu, które chcesz znaleźć.</span><span class="sxs-lookup"><span data-stu-id="37174-109">Call the <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method, passing the text of the item you would like to find.</span></span>  
  
3.  <span data-ttu-id="37174-110">Poniższy przykład kodu demonstruje sposób tworzenia prostej <xref:System.Windows.Forms.ListView>go wypełnić przy użyciu elementów i użyj wprowadzanie tekstu przez użytkownika, aby znaleźć element na liście.</span><span class="sxs-lookup"><span data-stu-id="37174-110">The following code example demonstrates how to create a basic <xref:System.Windows.Forms.ListView>, populate it with items, and use text input from the user to find an item in the list.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a><span data-ttu-id="37174-111">Aby znaleźć element za pomocą współrzędnych x i y</span><span class="sxs-lookup"><span data-stu-id="37174-111">To find an item using x- and y-coordinates</span></span>  
  
1.  <span data-ttu-id="37174-112">Tworzenie <xref:System.Windows.Forms.ListView> za pomocą <xref:System.Windows.Forms.View> właściwością <xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>, a następnie wypełnij <xref:System.Windows.Forms.ListView> z elementami.</span><span class="sxs-lookup"><span data-stu-id="37174-112">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.View> property set to <xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="37174-113">Wywołaj <xref:System.Windows.Forms.ListView.FindNearestItem%2A> jest metoda żądaną współrzędne x i y- i kierunku chcesz przeszukać.</span><span class="sxs-lookup"><span data-stu-id="37174-113">Call the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method, passing the desired x- and y-coordinates and the direction you would like to search.</span></span>  
  
3.  <span data-ttu-id="37174-114">Poniższy przykład kodu pokazuje, jak utworzyć podstawowe ikonę <xref:System.Windows.Forms.ListView>, umieścić w nim elementy i przechwytywania <xref:System.Windows.Forms.Control.MouseDown> zdarzeń Aby znaleźć najbliższy element w górę kierunku.</span><span class="sxs-lookup"><span data-stu-id="37174-114">The following code example demonstrates how to create a basic icon <xref:System.Windows.Forms.ListView>, populate it with items, and capture the <xref:System.Windows.Forms.Control.MouseDown> event to find the nearest item in the up direction.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="37174-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37174-115">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.FindItemWithText%2A>
- <xref:System.Windows.Forms.ListView.FindNearestItem%2A>
- [<span data-ttu-id="37174-116">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="37174-116">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="37174-117">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="37174-117">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [<span data-ttu-id="37174-118">Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="37174-118">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
