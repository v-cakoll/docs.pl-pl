---
title: Wyświetlanie danych w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: d35fd2d17ce8d1b3c4759da1bab2370c450d2fbf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703289"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="cc461-102">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cc461-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="cc461-103">`DataGridView` Formant jest używany do wyświetlania danych z różnych źródeł danych zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="cc461-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="cc461-104">Można również dodawanie wierszy i kolumn do formantu i ręcznie wypełnić je danymi.</span><span class="sxs-lookup"><span data-stu-id="cc461-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="cc461-105">Możesz powiązać formant ze źródłem danych, może wygenerować automatycznie na podstawie schematu źródła danych kolumny.</span><span class="sxs-lookup"><span data-stu-id="cc461-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="cc461-106">Jeśli tak, jak chcesz, aby te kolumny są niewidoczne, można ukryć, usunąć lub zmienić ich kolejność.</span><span class="sxs-lookup"><span data-stu-id="cc461-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="cc461-107">Można również dodać niepowiązanych kolumn do wyświetlenia dane dodatkowe, które nie pochodzą ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="cc461-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="cc461-108">Ponadto można wyświetlić danych przy użyciu standardowych formatów (na przykład format waluty) lub możesz dostosować formatowanie na prezentowanie danych, ale musisz się (np. Zmienianie koloru tła liczb ujemnych lub zastąpienie wartości ciągu wyświetlania przy użyciu odpowiedniego obrazów).</span><span class="sxs-lookup"><span data-stu-id="cc461-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc461-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cc461-109">In This Section</span></span>  
 [<span data-ttu-id="cc461-110">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cc461-111">W tym artykule opisano opcje wypełnianie kontrolki z danymi.</span><span class="sxs-lookup"><span data-stu-id="cc461-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="cc461-112">Formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cc461-113">W tym artykule opisano opcje formatowania wartości wyświetlane w komórce.</span><span class="sxs-lookup"><span data-stu-id="cc461-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="cc461-114">Przewodnik: Tworzenie Windows niezwiązanego formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="cc461-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cc461-115">Opisuje sposób ręcznego wypełnienia kontrolki z danymi.</span><span class="sxs-lookup"><span data-stu-id="cc461-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="cc461-116">Instrukcje: Powiązanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cc461-117">Zawiera opis sposobu wypełniania kontrolki z danymi, tworząc powiązanie do `BindingSource` zawierający informacje pobierane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cc461-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="cc461-118">Instrukcje: Automatyczne generowanie kolumn w formancie DataGridView formularzy Windows powiązane z danymi</span><span class="sxs-lookup"><span data-stu-id="cc461-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="cc461-119">Opisuje sposób automatycznie wygenerować na podstawie źródła danych powiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="cc461-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="cc461-120">Instrukcje: Usuwanie utworzonych automatycznie kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="cc461-121">Opisuje sposób ukryć lub usunąć automatycznie wygenerowany na podstawie źródła danych powiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="cc461-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="cc461-122">Instrukcje: Zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cc461-123">Opisuje sposób zmiana rozmieszczenia kolumn generowane automatycznie na podstawie źródła powiązane dane.</span><span class="sxs-lookup"><span data-stu-id="cc461-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="cc461-124">Instrukcje: Dodawanie niepowiązanych kolumn do formantu DataGridView formularzy Windows powiązane z danymi</span><span class="sxs-lookup"><span data-stu-id="cc461-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="cc461-125">Opisuje sposób uzupełniają dane ze źródła powiązanych danych, wyświetlając dodatkowych, niepowiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="cc461-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="cc461-126">Instrukcje: Powiązanie obiektów do kontrolek DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="cc461-127">W tym temacie opisano kontrolkę można powiązać kolekcję obiektów dowolnego tak, aby każdy obiekt jest wyświetlana w oddzielnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="cc461-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="cc461-128">Instrukcje: Uzyskiwanie dostępu do obiektów powiązanych z Windows Forms wierszami formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="cc461-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="cc461-129">W tym artykule opisano sposób pobierania obiektu powiązany do określonego wiersza formantu.</span><span class="sxs-lookup"><span data-stu-id="cc461-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="cc461-130">Przewodnik: Tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="cc461-131">W tym artykule opisano sposób wyświetlania danych z dwóch tabel w bazie danych, aby wartości widocznych w jednym `DataGridView` kontrolki są zależne od aktualnie zaznaczonego wiersza w innej kontrolce.</span><span class="sxs-lookup"><span data-stu-id="cc461-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="cc461-132">Instrukcje: Dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cc461-133">W tym artykule opisano sposób obsługi <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzenie, aby zmienić wygląd komórki, w zależności od ich wartości.</span><span class="sxs-lookup"><span data-stu-id="cc461-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cc461-134">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="cc461-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="cc461-135">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cc461-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="cc461-136">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cc461-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="cc461-137">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="cc461-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cc461-138">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="cc461-138">Related Sections</span></span>  
 [<span data-ttu-id="cc461-139">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cc461-140">Zawiera tematy, które opisują sposób zmiany przez użytkowników, dodawanie i modyfikowanie danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="cc461-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc461-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc461-141">See also</span></span>
- [<span data-ttu-id="cc461-142">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="cc461-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="cc461-143">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc461-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
