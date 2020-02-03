---
title: Wyświetlanie danych w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: d02362895d75df3735d19554bd44bb8ac443c6c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745871"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8c452-102">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8c452-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8c452-103">Formant `DataGridView` służy do wyświetlania danych z różnych zewnętrznych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="8c452-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="8c452-104">Alternatywnie możesz dodać wiersze i kolumny do kontrolki i ręcznie wypełnić je danymi.</span><span class="sxs-lookup"><span data-stu-id="8c452-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="8c452-105">Gdy powiążesz formant ze źródłem danych, możesz generować kolumny automatycznie w oparciu o schemat źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8c452-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="8c452-106">Jeśli te kolumny nie są wyświetlane w taki sam sposób, jak chcesz, można je ukryć, usunąć lub zmienić ich kolejność.</span><span class="sxs-lookup"><span data-stu-id="8c452-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="8c452-107">Możesz również dodać kolumny niepowiązane, aby wyświetlić dodatkowe dane, które nie pochodzą ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8c452-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="8c452-108">Ponadto można wyświetlać dane przy użyciu standardowych formatów (takich jak format waluty) lub dostosować formatowanie wyświetlania, aby przedstawić dane, co jest konieczne (na przykład zmiana koloru tła dla liczb ujemnych lub zastępowanie wartości ciągu). przy użyciu odpowiednich obrazów).</span><span class="sxs-lookup"><span data-stu-id="8c452-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c452-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8c452-109">In This Section</span></span>  
 [<span data-ttu-id="8c452-110">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8c452-111">Opisuje opcje wypełniania kontrolki danymi.</span><span class="sxs-lookup"><span data-stu-id="8c452-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="8c452-112">Formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8c452-113">Opisuje opcje formatowania wartości wyświetlanych komórki.</span><span class="sxs-lookup"><span data-stu-id="8c452-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="8c452-114">Przewodnik: tworzenie niepowiązanej kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8c452-115">Opisuje sposób ręcznego wypełniania formantu danymi.</span><span class="sxs-lookup"><span data-stu-id="8c452-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="8c452-116">Instrukcje: wiązanie danych z kontrolką DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8c452-117">Opisuje sposób wypełniania formantu danymi przez powiązanie go z `BindingSource` zawierającym informacje pobrane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8c452-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="8c452-118">Instrukcje: automatyczne generowanie kolumn w powiązanej z danymi kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="8c452-119">Opisuje sposób automatycznego generowania kolumn na podstawie powiązanego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8c452-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="8c452-120">Instrukcje: usuwanie utworzonych automatycznie kolumn z kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="8c452-121">Opisuje sposób ukrywania lub usuwania kolumn generowanych automatycznie z powiązanego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8c452-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="8c452-122">Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8c452-123">Opisuje sposób ponownego rozmieszczenia kolumn generowanych automatycznie z powiązanego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8c452-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="8c452-124">Instrukcje: dodawanie niepowiązanych kolumn do powiązanej z danymi kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="8c452-125">Opisuje sposób uzupełniania danych z powiązanego źródła danych przez wyświetlanie dodatkowych, niepowiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="8c452-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="8c452-126">Instrukcje: wiązanie obiektów z kontrolkami DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="8c452-127">Opisuje sposób powiązania kontrolki z kolekcją dowolnych obiektów, aby każdy obiekt był wyświetlany w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="8c452-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="8c452-128">Instrukcje: uzyskiwanie dostępu do obiektów powiązanych z wierszami kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="8c452-129">Opisuje sposób pobierania obiektu powiązanego z określonym wierszem formantu.</span><span class="sxs-lookup"><span data-stu-id="8c452-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="8c452-130">Przewodnik: tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="8c452-131">Opisuje sposób wyświetlania danych z dwóch powiązanych tabel bazy danych, dzięki czemu wartości wyświetlane w jednym `DataGridView` kontrolce zależą od aktualnie zaznaczonego wiersza w innej kontrolce.</span><span class="sxs-lookup"><span data-stu-id="8c452-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="8c452-132">Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8c452-133">Opisuje, jak obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>, aby zmienić wygląd komórek w zależności od ich wartości.</span><span class="sxs-lookup"><span data-stu-id="8c452-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8c452-134">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="8c452-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="8c452-135">Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8c452-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="8c452-136">Zawiera dokumentację referencyjną dla właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c452-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="8c452-137">Zawiera dokumentację referencyjną składnika <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="8c452-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8c452-138">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="8c452-138">Related Sections</span></span>  
 [<span data-ttu-id="8c452-139">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8c452-140">Zawiera tematy opisujące sposób zmiany sposobu, w jaki użytkownicy mogą dodawać i modyfikować dane w formancie.</span><span class="sxs-lookup"><span data-stu-id="8c452-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c452-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c452-141">See also</span></span>

- [<span data-ttu-id="8c452-142">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8c452-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="8c452-143">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c452-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
