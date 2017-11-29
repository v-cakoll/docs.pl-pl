---
title: Wprowadzanie danych w formancie DataGridView formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39d5f7763ac7b5923f0eaec757df13d675971789
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="39107-102">Wprowadzanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39107-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="39107-103">`DataGridView` Formant zawiera kilka funkcji umożliwiające zmienić sposób użytkowników, dodawanie lub modyfikowanie danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="39107-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="39107-104">Na przykład możesz wprowadzić wprowadzania danych bardziej wydajne, podając wartości domyślne dla nowych wierszy oraz alerty użytkowników w przypadku wystąpienia błędów.</span><span class="sxs-lookup"><span data-stu-id="39107-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39107-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="39107-105">In This Section</span></span>  
 [<span data-ttu-id="39107-106">Porady: Określanie trybu edycji dla formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39107-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="39107-107">Opisuje sposób zmienić sposób, w jaki użytkownicy uruchamiają edytowania komórki.</span><span class="sxs-lookup"><span data-stu-id="39107-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="39107-108">Porady: Określanie wartości domyślnych dla nowych wierszy w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39107-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="39107-109">Opisuje sposób wstępnie wiersz dla nowych rekordów zaoszczędzić czas wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="39107-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="39107-110">Używanie wiersza dla nowych rekordów w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39107-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="39107-111">Opisuje wiersz dla nowych rekordów szczegółowo, wraz z informacjami w ukryć, dostosowywanie wyglądu i na jego znaczenia <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="39107-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="39107-112">Wskazówki: Sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39107-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="39107-113">Opisuje sposób sprawdzania poprawności danych wejściowych użytkownika, aby zapobiec błędom formatowania wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="39107-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="39107-114">Wskazówki: Obsługa błędów występujących podczas wprowadzania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39107-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="39107-115">Opisuje sposób obsługi błędów wprowadzania danych, które pochodzą ze źródła danych, gdy użytkownik próbuje zatwierdzić nową wartość.</span><span class="sxs-lookup"><span data-stu-id="39107-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="39107-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="39107-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="39107-117">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="39107-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="39107-118">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.EditMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="39107-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="39107-119">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="39107-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="39107-120">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.DataError> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="39107-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="39107-121">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.CellValidating> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="39107-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="39107-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="39107-122">Related Sections</span></span>  
 [<span data-ttu-id="39107-123">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39107-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="39107-124">Udostępnia tematów opisujących sposób wypełnić kontrolki z danymi ręcznie lub z zewnętrznego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="39107-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39107-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39107-125">See Also</span></span>  
 [<span data-ttu-id="39107-126">DataGridView — formant</span><span class="sxs-lookup"><span data-stu-id="39107-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="39107-127">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39107-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
