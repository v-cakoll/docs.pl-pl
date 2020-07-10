---
title: Wyświetlanie danych w formancie DataGridView
description: Dowiedz się, jak używać kontrolki DataGridView Windows Forms do wyświetlania danych z różnych zewnętrznych źródeł danych.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: a0f3e6627290521b8c10477c31459f1486e79162
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174578"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f9354-103">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9354-103">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f9354-104">`DataGridView`Kontrolka służy do wyświetlania danych z różnych zewnętrznych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="f9354-104">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="f9354-105">Alternatywnie możesz dodać wiersze i kolumny do kontrolki i ręcznie wypełnić je danymi.</span><span class="sxs-lookup"><span data-stu-id="f9354-105">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="f9354-106">Gdy powiążesz formant ze źródłem danych, możesz generować kolumny automatycznie w oparciu o schemat źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f9354-106">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="f9354-107">Jeśli te kolumny nie są wyświetlane w taki sam sposób, jak chcesz, można je ukryć, usunąć lub zmienić ich kolejność.</span><span class="sxs-lookup"><span data-stu-id="f9354-107">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="f9354-108">Możesz również dodać kolumny niepowiązane, aby wyświetlić dodatkowe dane, które nie pochodzą ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f9354-108">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="f9354-109">Ponadto można wyświetlać dane przy użyciu standardowych formatów (takich jak format waluty) lub dostosować formatowanie wyświetlania, aby przedstawić dane, co jest konieczne (na przykład zmiana koloru tła dla liczb ujemnych lub zastępowanie wartości ciągu odpowiednimi obrazami).</span><span class="sxs-lookup"><span data-stu-id="f9354-109">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9354-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f9354-110">In This Section</span></span>  
 [<span data-ttu-id="f9354-111">Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9354-111">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f9354-112">Opisuje opcje wypełniania kontrolki danymi.</span><span class="sxs-lookup"><span data-stu-id="f9354-112">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="f9354-113">Formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-113">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f9354-114">Opisuje opcje formatowania wartości wyświetlanych komórki.</span><span class="sxs-lookup"><span data-stu-id="f9354-114">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="f9354-115">Przewodnik: tworzenie niepowiązanej kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-115">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f9354-116">Opisuje sposób ręcznego wypełniania formantu danymi.</span><span class="sxs-lookup"><span data-stu-id="f9354-116">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="f9354-117">Instrukcje: wiązanie danych z kontrolką DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-117">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f9354-118">Opisuje sposób wypełniania formantu danymi przez powiązanie go z `BindingSource` , który zawiera informacje pobrane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f9354-118">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="f9354-119">Porady: automatyczne generowanie kolumn w powiązanym z danymi formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9354-119">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="f9354-120">Opisuje sposób automatycznego generowania kolumn na podstawie powiązanego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f9354-120">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="f9354-121">Porady: usuwanie utworzonych automatycznie kolumn z formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9354-121">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="f9354-122">Opisuje sposób ukrywania lub usuwania kolumn generowanych automatycznie z powiązanego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f9354-122">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="f9354-123">Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-123">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f9354-124">Opisuje sposób ponownego rozmieszczenia kolumn generowanych automatycznie z powiązanego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f9354-124">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="f9354-125">Instrukcje: dodawanie niepowiązanych kolumn do powiązanej z danymi kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-125">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="f9354-126">Opisuje sposób uzupełniania danych z powiązanego źródła danych przez wyświetlanie dodatkowych, niepowiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="f9354-126">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="f9354-127">Instrukcje: wiązanie obiektów z kontrolkami DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-127">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="f9354-128">Opisuje sposób powiązania kontrolki z kolekcją dowolnych obiektów, aby każdy obiekt był wyświetlany w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="f9354-128">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="f9354-129">Instrukcje: uzyskiwanie dostępu do obiektów powiązanych z wierszami kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-129">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="f9354-130">Opisuje sposób pobierania obiektu powiązanego z określonym wierszem formantu.</span><span class="sxs-lookup"><span data-stu-id="f9354-130">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="f9354-131">Przewodnik: tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-131">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="f9354-132">Opisuje sposób wyświetlania danych z dwóch powiązanych tabel bazy danych, dzięki czemu wartości wyświetlane w jednym `DataGridView` formancie zależą od aktualnie zaznaczonego wiersza w innej kontrolce.</span><span class="sxs-lookup"><span data-stu-id="f9354-132">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="f9354-133">Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f9354-134">Opisuje, jak obsłużyć <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzenie, aby zmienić wygląd komórek w zależności od ich wartości.</span><span class="sxs-lookup"><span data-stu-id="f9354-134">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f9354-135">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="f9354-135">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="f9354-136">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="f9354-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="f9354-137">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9354-137">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="f9354-138">Zawiera dokumentację referencyjną <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="f9354-138">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f9354-139">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="f9354-139">Related Sections</span></span>  
 [<span data-ttu-id="f9354-140">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9354-140">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f9354-141">Zawiera tematy opisujące sposób zmiany sposobu, w jaki użytkownicy mogą dodawać i modyfikować dane w formancie.</span><span class="sxs-lookup"><span data-stu-id="f9354-141">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9354-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9354-142">See also</span></span>

- [<span data-ttu-id="f9354-143">DataGridView — Formant</span><span class="sxs-lookup"><span data-stu-id="f9354-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="f9354-144">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9354-144">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
