---
title: Powiązanie danych
description: Dowiedz się, jak używać powiązań danych w Windows Forms, aby wyświetlać i wprowadzać zmiany w informacjach ze źródła danych w kontrolkach w formularzu.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 3dfce24147caf9b138916ca8dc3b7a9010439f58
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325542"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="333b9-103">Powiązywanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="333b9-103">Windows Forms Data Binding</span></span>
<span data-ttu-id="333b9-104">Powiązanie danych w Windows Forms umożliwia wyświetlanie i wprowadzanie zmian w informacjach ze źródła danych w kontrolkach w formularzu.</span><span class="sxs-lookup"><span data-stu-id="333b9-104">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="333b9-105">Można powiązać zarówno tradycyjne źródła danych, jak i prawie wszystkie struktury zawierające dane.</span><span class="sxs-lookup"><span data-stu-id="333b9-105">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="333b9-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="333b9-106">In This Section</span></span>  
 [<span data-ttu-id="333b9-107">Wiązanie danych i formularze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="333b9-107">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="333b9-108">Zawiera omówienie powiązań danych w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="333b9-108">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="333b9-109">Źródła danych obsługiwane przez formularze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="333b9-109">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="333b9-110">Opisuje źródła danych, które mogą być używane z Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="333b9-110">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="333b9-111">Interfejsy dotyczące wiązania danych</span><span class="sxs-lookup"><span data-stu-id="333b9-111">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="333b9-112">Opisuje kilka interfejsów używanych z Windows Forms powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="333b9-112">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="333b9-113">Instrukcje: Nawigowanie po danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="333b9-113">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="333b9-114">Pokazuje, w jaki sposób nawigować przez elementy w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="333b9-114">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="333b9-115">Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="333b9-115">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="333b9-116">Opisuje różne typy powiadomień o zmianach dla Windows Forms powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="333b9-116">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="333b9-117">Instrukcje: Implementowanie interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="333b9-117">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="333b9-118">Pokazuje, jak zaimplementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejs.</span><span class="sxs-lookup"><span data-stu-id="333b9-118">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="333b9-119">Interfejs komunikuje się z kontrolką powiązaną ze zmianą właściwości w obiekcie biznesowym</span><span class="sxs-lookup"><span data-stu-id="333b9-119">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="333b9-120">Instrukcje: Stosowanie wzorca PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="333b9-120">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="333b9-121">Pokazuje, jak zastosować wzorzec zmiany *PropertyName*do właściwości kontrolki użytkownika Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="333b9-121">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="333b9-122">Instrukcje: Implementowanie interfejsu ITypedList</span><span class="sxs-lookup"><span data-stu-id="333b9-122">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="333b9-123">Pokazuje, jak włączyć odnajdywanie schematu dla listy możliwej do powiązania przez implementację <xref:System.ComponentModel.ITypedList> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="333b9-123">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="333b9-124">Instrukcje: Implementowanie interfejsu IListSource</span><span class="sxs-lookup"><span data-stu-id="333b9-124">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="333b9-125">Pokazuje, jak zaimplementować <xref:System.ComponentModel.IListSource> interfejs do tworzenia klasy możliwej do powiązania nie implementuje <xref:System.Collections.IList> , ale zawiera listę z innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="333b9-125">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="333b9-126">Instrukcje: Zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych</span><span class="sxs-lookup"><span data-stu-id="333b9-126">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="333b9-127">Pokazuje, jak obsłużyć <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzenie, aby upewnić się, że wszystkie kontrolki powiązane ze źródłem danych pozostaną zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="333b9-127">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="333b9-128">Instrukcje: Zapewnienie pozostawania wybranego wiersza w tabeli podrzędnej w prawidłowym położeniu</span><span class="sxs-lookup"><span data-stu-id="333b9-128">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="333b9-129">Pokazuje, jak upewnić się, że wybrany wiersz tabeli podrzędnej nie zmienia się, gdy zostanie wprowadzona zmiana w polu tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="333b9-129">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="333b9-130">Zobacz również [interfejsy powiązane z powiązaniem danych](interfaces-related-to-data-binding.md), [instrukcje: nawigowanie po danych w Windows Forms](how-to-navigate-data-in-windows-forms.md)i [instrukcje: tworzenie prostej kontroli powiązanej w formularzu systemu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="333b9-130">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="333b9-131">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="333b9-131">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="333b9-132">Opisuje klasę, która reprezentuje powiązanie między składnikiem możliwym do powiązania a źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="333b9-132">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="333b9-133">Opisuje klasę, która hermetyzuje źródło danych dla powiązania z kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="333b9-133">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="333b9-134">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="333b9-134">Related Sections</span></span>  
 [<span data-ttu-id="333b9-135">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="333b9-135">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="333b9-136">Zawiera listę tematów, które pokazują, jak używać <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="333b9-136">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="333b9-137">DataGridView — Formant</span><span class="sxs-lookup"><span data-stu-id="333b9-137">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="333b9-138">Zawiera listę tematów, które pokazują, jak używać kontrolki DataGrid możliwej do powiązania.</span><span class="sxs-lookup"><span data-stu-id="333b9-138">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="333b9-139">Zobacz też [dostęp do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="333b9-139">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
