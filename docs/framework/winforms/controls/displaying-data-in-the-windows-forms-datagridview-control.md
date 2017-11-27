---
title: "Wyświetlanie danych w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 839a4fd8052578e32e4d46d10e07aa52a1f23d90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="36aa6-102">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="36aa6-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="36aa6-103">`DataGridView` Kontroli jest używana do wyświetlania danych z różnych źródeł danych zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="36aa6-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="36aa6-104">Alternatywnie możesz Dodawanie wierszy i kolumn do formantu i ręcznie umieścić w nim danych.</span><span class="sxs-lookup"><span data-stu-id="36aa6-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="36aa6-105">Powiązywanie formantu ze źródłem danych, może wygenerować kolumny automatycznie na podstawie schematu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="36aa6-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="36aa6-106">Jeśli te kolumny są niewidoczne, tak samo, jak mają być, można ukryć, usunąć lub zmienić ich kolejność.</span><span class="sxs-lookup"><span data-stu-id="36aa6-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="36aa6-107">Można również dodać niepowiązanych kolumn, aby wyświetlić dane dodatkowe, które nie pochodzą ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="36aa6-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="36aa6-108">Ponadto można wyświetlić dane przy użyciu standardowych formatów (na przykład w formacie waluty), lub można dostosować formatowanie do prezentowania danych, jednak należy (np. zmiana koloru tła dla wartości ujemne lub zastępowania wartości ciągów wyświetlania z odpowiedniego obrazów).</span><span class="sxs-lookup"><span data-stu-id="36aa6-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36aa6-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="36aa6-109">In This Section</span></span>  
 [<span data-ttu-id="36aa6-110">Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="36aa6-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="36aa6-111">Opisuje opcje wypełniania formantu z danymi.</span><span class="sxs-lookup"><span data-stu-id="36aa6-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="36aa6-112">Formatowanie danych w oknie formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="36aa6-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="36aa6-113">Opisuje opcje formatowania komórki wyświetlanej wartości.</span><span class="sxs-lookup"><span data-stu-id="36aa6-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="36aa6-114">Wskazówki: Tworzenie formantu DataGridView formularzy Windows niepowiązanych</span><span class="sxs-lookup"><span data-stu-id="36aa6-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="36aa6-115">Opisuje sposób ręcznego wypełnić kontrolki z danymi.</span><span class="sxs-lookup"><span data-stu-id="36aa6-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="36aa6-116">Porady: wiązanie danych formularzy systemu Windows formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="36aa6-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="36aa6-117">Opisuje sposób wypełnienia kontrolki z danych przez to powiązanie `BindingSource` zawierający informacje pobrane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="36aa6-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="36aa6-118">Porady: automatyczne generowanie kolumn w Windows powiązane z danymi formancie DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="36aa6-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="36aa6-119">Opisuje sposób automatycznego generowania kolumn na podstawie źródła powiązana z danymi.</span><span class="sxs-lookup"><span data-stu-id="36aa6-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="36aa6-120">Porady: usuwanie utworzonych automatycznie kolumn z systemu Windows do formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="36aa6-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="36aa6-121">Opisuje sposób ukryć lub usunąć kolumny generowane automatycznie na podstawie źródła danych powiązania.</span><span class="sxs-lookup"><span data-stu-id="36aa6-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="36aa6-122">Porady: Zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="36aa6-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="36aa6-123">Opisuje sposób zmieniać kolejności kolumn generowane automatycznie na podstawie źródła danych powiązania.</span><span class="sxs-lookup"><span data-stu-id="36aa6-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="36aa6-124">Porady: Dodawanie niepowiązanych kolumn do systemu Windows z danymi formancie DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="36aa6-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="36aa6-125">Opisuje sposób uzupełnienia danych ze źródła danych powiązania przez wyświetlanie dodatkowych, niepowiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="36aa6-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="36aa6-126">Porady: powiązanie obiektów z formantów DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="36aa6-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="36aa6-127">Opisuje sposób do powiązania kontrolki do kolekcji obiektów dowolnego, dzięki czemu każdy obiekt jest wyświetlany w oddzielnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="36aa6-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="36aa6-128">Porady: uzyskiwanie dostępu do obiektów powiązanych do formularzy systemu Windows wierszy formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="36aa6-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="36aa6-129">Opisuje sposób pobrać obiekt powiązany z określonego wiersza formantu.</span><span class="sxs-lookup"><span data-stu-id="36aa6-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="36aa6-130">Wskazówki: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="36aa6-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="36aa6-131">Opisuje sposób wyświetlania danych z dwóch tabel w bazie danych, aby wartości wyświetlane w jednym `DataGridView` formantu są zależne od aktualnie zaznaczonego wiersza w inny formant.</span><span class="sxs-lookup"><span data-stu-id="36aa6-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="36aa6-132">Porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="36aa6-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="36aa6-133">Opisuje sposób obsługi <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzeń, aby zmienić wygląd komórek w zależności od ich wartości.</span><span class="sxs-lookup"><span data-stu-id="36aa6-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="36aa6-134">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="36aa6-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="36aa6-135">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="36aa6-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="36aa6-136">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="36aa6-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="36aa6-137">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="36aa6-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="36aa6-138">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="36aa6-138">Related Sections</span></span>  
 [<span data-ttu-id="36aa6-139">Formantu DataGridView formularzy wprowadzania danych w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="36aa6-139">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="36aa6-140">Udostępnia tematów opisujących sposób zmiany przez użytkowników, dodawanie i modyfikowanie danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="36aa6-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36aa6-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36aa6-141">See Also</span></span>  
 [<span data-ttu-id="36aa6-142">DataGridView — formant</span><span class="sxs-lookup"><span data-stu-id="36aa6-142">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="36aa6-143">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="36aa6-143">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
