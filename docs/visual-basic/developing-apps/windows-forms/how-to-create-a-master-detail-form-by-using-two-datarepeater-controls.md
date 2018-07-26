---
title: 'Porady: Tworzenie formularza wzorzec / szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245543"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="838ff-102">Porady: tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="838ff-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="838ff-103">Powiązane dane można wyświetlić przy użyciu co najmniej dwóch <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> na tworzenie formularza wzorzec/szczegół formantów.</span><span class="sxs-lookup"><span data-stu-id="838ff-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="838ff-104">Na przykład możesz chcieć wyświetlić listę klientów w jednej <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>i gdy użytkownik wybierze klienta, wyświetlić listę zamówień tego klienta w ciągu sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="838ff-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="838ff-105">Możesz wyświetlić dane dotyczące przez przeciąganie elementów szczegóły, które współużytkują ten sam węzeł główny tabeli, z **źródeł danych** okna na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="838ff-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="838ff-106">Na przykład, jeśli źródło danych tabeli Customers i powiązanej tabeli zamówienia, zostanie wyświetlony obie tabele jako węzły najwyższego poziomu w widoku drzewa w **źródeł danych** okna.</span><span class="sxs-lookup"><span data-stu-id="838ff-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="838ff-107">Rozwiń węzeł klientów, dzięki czemu można zobaczyć kolumny.</span><span class="sxs-lookup"><span data-stu-id="838ff-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="838ff-108">Należy zauważyć, że ostatnia kolumna na liście jest rozwijany węzeł, który reprezentuje tabeli zamówienia.</span><span class="sxs-lookup"><span data-stu-id="838ff-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="838ff-109">Ten węzeł reprezentuje powiązane zamówienia dla klienta.</span><span class="sxs-lookup"><span data-stu-id="838ff-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="838ff-110">Wyświetlanie powiązanych danych w dwóch formantów DataRepeater</span><span class="sxs-lookup"><span data-stu-id="838ff-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="838ff-111">Przeciągnij dwa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolki z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.</span><span class="sxs-lookup"><span data-stu-id="838ff-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="838ff-112">Przeciągnij uchwyty zmiany rozmiaru i położenia, rozmiaru kontrolki i ich położenie side-by-side.</span><span class="sxs-lookup"><span data-stu-id="838ff-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="838ff-113">Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.</span><span class="sxs-lookup"><span data-stu-id="838ff-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="838ff-114">Jeśli **źródeł danych** okna jest pusta, Dodaj źródło danych do niego.</span><span class="sxs-lookup"><span data-stu-id="838ff-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="838ff-115">Aby uzyskać więcej informacji, zobacz [dodasz nowe źródła danych](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="838ff-115">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="838ff-116">W **źródeł danych** okna, wybierz węzeł najwyższego poziomu dla głównej tabeli.</span><span class="sxs-lookup"><span data-stu-id="838ff-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="838ff-117">Zmień upuszczany typ tabeli głównej do szczegółów, klikając **szczegóły** w węźle tabeli na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="838ff-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="838ff-118">Przeciągnij węzeł główny tabeli na region szablonu elementu pierwszego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="838ff-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="838ff-119">Rozwiń węzeł główny tabeli i wybierz węzeł szczegółów powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="838ff-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="838ff-120">Zmień upuszczany typ tabeli szczegółów do szczegółów, klikając **szczegóły** w węźle tabeli na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="838ff-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="838ff-121">Wybierz węzeł w tej tabeli i przeciągnij go na region szablonu elementu drugiego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="838ff-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="838ff-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="838ff-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="838ff-123">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="838ff-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="838ff-124">Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="838ff-124">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="838ff-125">Porady: wyświetlanie powiązanych danych w Windows Forms aplikacji</span><span class="sxs-lookup"><span data-stu-id="838ff-125">How to: Display Related Data in a Windows Forms Application</span></span>](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [<span data-ttu-id="838ff-126">Instrukcje: zmienianie wyglądu kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="838ff-126">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="838ff-127">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="838ff-127">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
