---
title: 'Porady: wyszukiwanie danych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3ed7138c142a83584ecd19ccaebe0e31e421ce3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="6b71c-102">Porady: wyszukiwanie danych w formancie DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="6b71c-102">How to: Search Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="6b71c-103">W przypadku używania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolkę, która zawiera dużą liczbę rekordów, może zajść potrzeba Pozwalanie użytkownikom wyszukiwanie określonego rekordu.</span><span class="sxs-lookup"><span data-stu-id="6b71c-103">When you are using a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that contains many records, you may want to let users search for a specific record.</span></span> <span data-ttu-id="6b71c-104">Zamiast wyszukiwanie danych w formancie, można zaimplementować wyszukiwania, badając odpowiadającego <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="6b71c-104">Rather than searching the data in the control itself, you can implement a search by querying the underlying <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="6b71c-105">Jeśli element zostanie znaleziony, można użyć <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> właściwości zaznacz element i przewiń go do widoku.</span><span class="sxs-lookup"><span data-stu-id="6b71c-105">If the item is found, you can then use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> property to select the item and scroll it into view.</span></span>  
  
### <a name="to-implement-search"></a><span data-ttu-id="6b71c-106">Aby zaimplementować wyszukiwania</span><span class="sxs-lookup"><span data-stu-id="6b71c-106">To implement search</span></span>  
  
1.  <span data-ttu-id="6b71c-107">Przeciągnij <xref:System.Windows.Forms.TextBox> kontrolować z **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="6b71c-107">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="6b71c-108">W oknie Właściwości zmień **nazwa** właściwości **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="6b71c-108">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="6b71c-109">Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="6b71c-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="6b71c-110">W oknie Właściwości zmień **nazwa** właściwości **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="6b71c-110">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="6b71c-111">Zmień **tekst** właściwości **wyszukiwania**.</span><span class="sxs-lookup"><span data-stu-id="6b71c-111">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="6b71c-112">Kliknij dwukrotnie <xref:System.Windows.Forms.Button> sterowania, aby otworzyć edytora kodu i Dodaj następujący kod do `SearchButton_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6b71c-112">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     <span data-ttu-id="6b71c-113">Zastąp *ProductsBindingSource* o nazwie <xref:System.Windows.Forms.BindingSource> dla Twojego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>i Zastąp *ProductID* nazwą pola, które chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="6b71c-113">Replace *ProductsBindingSource* with the name of the <xref:System.Windows.Forms.BindingSource> for your <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and replace *ProductID* with the name of the field that you want to search.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b71c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b71c-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="6b71c-115">Wprowadzenie do formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6b71c-115">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="6b71c-116">Rozwiązywanie problemów z formantem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6b71c-116">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="6b71c-117">Porady: Zmienianie wyglądu formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6b71c-117">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
