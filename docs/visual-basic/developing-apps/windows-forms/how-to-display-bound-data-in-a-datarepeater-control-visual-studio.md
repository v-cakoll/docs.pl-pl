---
title: "Porady: wyświetlanie powiązanych danych w formancie DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770003c8879661bfc1ce683f5b6ed84483cf47ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="1b7f7-102">Porady: wyświetlanie powiązanych danych w formancie DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1b7f7-102">How to: Display Bound Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="1b7f7-103">Najczęściej używane <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania są wyświetlane powiązane dane z bazy danych lub inne źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-103">The most common use of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control is to display bound data from a database or other data source.</span></span>  
  
 <span data-ttu-id="1b7f7-104">Oprócz formanty powiązane, można dodać inne formanty, takie jak statyczną etykietę lub obraz jest powtarzany na każdej pozycji w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-104">In addition to bound controls, you may want to add other controls, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="1b7f7-105">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formantów niepowiązanych w formancie Datarepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1b7f7-105">For more information, see [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
 <span data-ttu-id="1b7f7-106">Można także powiązać ze źródłem danych w czasie wykonywania przez ustawienie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwości `True` i przypisywanie źródło danych do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-106">You can also bind to a data source at run time by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property to `True` and assigning a data source to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> property.</span></span> <span data-ttu-id="1b7f7-107">W takim przypadku należy zarządzać wszystkie interakcje ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-107">In this case, you will need to manage all interaction with the data source.</span></span> <span data-ttu-id="1b7f7-108">Aby uzyskać więcej informacji, zobacz [tryb wirtualny w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1b7f7-108">For more information, see [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a><span data-ttu-id="1b7f7-109">Aby utworzyć DataRepeater powiązane z danymi</span><span class="sxs-lookup"><span data-stu-id="1b7f7-109">To create a data-bound DataRepeater</span></span>  
  
1.  <span data-ttu-id="1b7f7-110">Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-110">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="1b7f7-111">Przeciągnij uchwyt zmiany rozmiaru i pozycji do rozmiaru i pozycji formantu.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-111">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="1b7f7-112">Należy pamiętać, że kontrolka ma dwóch regionach prostokątny.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="1b7f7-113">Górny obszar jest *szablon elementu*; formanty dodawane do szablonu zostanie powtórzona w każdej pozycji w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-113">The upper region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="1b7f7-114">Niższe region jest *okienka ekranu*, której elementy będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-114">The lower region is the *viewport*, where the items will be displayed.</span></span>  
  
     <span data-ttu-id="1b7f7-115">Można również rozmiaru i pozycji formant lub szablon elementu zmieniając **rozmiar** i **pozycji** właściwości w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-115">You can also size and position the control or the item template by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="1b7f7-116">Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-116">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1b7f7-117">Jeśli **źródeł danych** okna jest pusta, Dodaj źródło danych do niej.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-117">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="1b7f7-118">Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="1b7f7-118">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="1b7f7-119">W **źródeł danych** okna, wybierz węzeł najwyższego poziomu dla tabeli, która zawiera dane, które chcesz powiązać.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-119">In the **Data Sources** window, select the top-level node for the table that contains the data that you want to bind.</span></span>  
  
5.  <span data-ttu-id="1b7f7-120">Zmień typ docelowej tabeli `Details` klikając `Details` na liście rozwijanej na węźle tabeli.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-120">Change the drop type of the table to `Details` by clicking `Details` in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="1b7f7-121">Wybierz węzeł tabeli i przeciągnij go na region szablonu elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-121">Select the table node and drag it onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="1b7f7-122">Można określić, jakie typy formantów są wyświetlane dla każdego pola.</span><span class="sxs-lookup"><span data-stu-id="1b7f7-122">You can specify which types of controls are displayed for each field.</span></span> <span data-ttu-id="1b7f7-123">Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span><span class="sxs-lookup"><span data-stu-id="1b7f7-123">For more information, see [Set the control to be created when dragging from the Data Sources window](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7f7-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b7f7-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="1b7f7-125">Wprowadzenie do formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1b7f7-125">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1b7f7-126">Porady: wyświetlanie formantów niepowiązanych w formancie DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1b7f7-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1b7f7-127">Porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1b7f7-127">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="1b7f7-128">Porady: Zmienianie wyglądu formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1b7f7-128">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1b7f7-129">Rozwiązywanie problemów z formantem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1b7f7-129">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
