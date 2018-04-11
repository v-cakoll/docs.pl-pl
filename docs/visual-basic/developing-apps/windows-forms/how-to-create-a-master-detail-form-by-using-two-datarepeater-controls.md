---
title: 'Porady: Tworzenie formularza wzorzec szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f17cb86c3ea0ea056291a51becd7ecf9f73d0a73
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="6e3c5-102">Porady: tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="6e3c5-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="6e3c5-103">Powiązane dane można wyświetlić przy użyciu co najmniej dwóch <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> na tworzenie formularza wzorzec/szczegół formantów.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="6e3c5-104">Na przykład możesz wyświetlić listę klientów w jednym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>i gdy użytkownik wybierze klienta, wyświetlona zostanie lista klienta na sekundę <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="6e3c5-105">Można wyświetlić dane dotyczące przez przeciąganie elementów szczegóły, które współużytkują tego samego węzła głównego tabeli z **źródeł danych** okna na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="6e3c5-106">Na przykład, jeśli źródło danych tabeli klientów i powiązanej tabeli zamówienia, zostanie wyświetlony obu tabel jako węzły najwyższego poziomu w widoku drzewa w **źródeł danych** okna.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="6e3c5-107">Rozwiń węzeł klientów, dzięki czemu można zobaczyć kolumny.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="6e3c5-108">Zauważ, że ostatniej kolumny w liście jest rozwijane węzeł, który reprezentuje tabeli zamówienia.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="6e3c5-109">Ten węzeł reprezentuje powiązane zamówienia dla klienta.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="6e3c5-110">Aby wyświetlanie powiązanych danych w dwóch formantów DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6e3c5-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="6e3c5-111">Przeciągnij dwa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantów **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6e3c5-112">Przeciągnij uchwyt zmiany rozmiaru i pozycji do określenia rozmiaru formantów i umieść je side-by-side.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="6e3c5-113">Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e3c5-114">Jeśli **źródeł danych** okna jest pusta, Dodaj źródło danych do niej.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="6e3c5-115">Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="6e3c5-115">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="6e3c5-116">W **źródeł danych** okna, wybierz węzeł najwyższego poziomu głównego tabeli.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="6e3c5-117">Zmień typ listy wzorcowej tabeli Szczegóły klikając **szczegóły** na liście rozwijanej na węźle tabeli.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="6e3c5-118">Przeciągnij węzeł główny tabeli region szablonu elementu pierwszego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="6e3c5-119">Rozwiń węzeł główny tabeli, a następnie wybierz węzeł szczegółów powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="6e3c5-120">Zmień typ docelowej tabeli szczegółów szczegóły klikając **szczegóły** na liście rozwijanej na węźle tabeli.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="6e3c5-121">Wybierz ten węzeł tabeli i przeciągnij go na region szablonu elementu drugiego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="6e3c5-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3c5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e3c5-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="6e3c5-123">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6e3c5-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="6e3c5-124">Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6e3c5-124">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="6e3c5-125">Porady: wyświetlanie powiązanych danych w systemie Windows formularzy aplikacji</span><span class="sxs-lookup"><span data-stu-id="6e3c5-125">How to: Display Related Data in a Windows Forms Application</span></span>](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [<span data-ttu-id="6e3c5-126">Instrukcje: zmienianie wyglądu kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6e3c5-126">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="6e3c5-127">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6e3c5-127">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
