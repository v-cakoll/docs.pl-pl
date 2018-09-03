---
title: Powiązywanie danych formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: cfb4c59c76142420f479b0b16a6d80317e98d159
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486013"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="e9030-102">Powiązywanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e9030-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="e9030-103">Powiązanie danych w formularzach Windows Forms zapewnia sposób wyświetlania i zmiany informacji ze źródła danych w kontrolkach w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e9030-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="e9030-104">Możesz powiązać zarówno źródeł danych tradycyjnych, jak i praktycznie dowolne strukturę, która zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="e9030-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9030-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e9030-105">In This Section</span></span>  
 [<span data-ttu-id="e9030-106">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9030-106">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 <span data-ttu-id="e9030-107">Zawiera omówienie powiązanie danych w formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e9030-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="e9030-108">Źródła danych obsługiwane przez formularze Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9030-108">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="e9030-109">W tym artykule opisano źródeł danych, które mogą służyć za pomocą interfejsu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e9030-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="e9030-110">Interfejsy dotyczące wiązania danych</span><span class="sxs-lookup"><span data-stu-id="e9030-110">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 <span data-ttu-id="e9030-111">Opisano kilka interfejsów używane dla wiązania danych Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e9030-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="e9030-112">Instrukcje: nawigowanie po danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9030-112">How to: Navigate Data in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="e9030-113">Pokazuje, jak przechodzenie przez elementy w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="e9030-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="e9030-114">Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9030-114">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="e9030-115">W tym artykule opisano różne rodzaje powiadomienia o zmianie dla powiązania danych Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e9030-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="e9030-116">Instrukcje: implementowanie interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="e9030-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="e9030-117">Pokazuje, jak zaimplementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e9030-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="e9030-118">Interfejs komunikuje się kontrolki powiązane zmiany właściwości w obiekcie firmy</span><span class="sxs-lookup"><span data-stu-id="e9030-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="e9030-119">Instrukcje: stosowanie wzorca PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="e9030-119">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="e9030-120">Przedstawia sposób zastosowania *PropertyName*wzorzec zmieniono właściwości formant użytkownika interfejsu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e9030-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="e9030-121">Instrukcje: implementowanie interfejsu ITypedList</span><span class="sxs-lookup"><span data-stu-id="e9030-121">How to: Implement the ITypedList Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="e9030-122">Pokazuje, jak włączyć funkcję odnajdywania schematu, który może być powiązana lista implementując <xref:System.ComponentModel.ITypedList> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e9030-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="e9030-123">Instrukcje: implementowanie interfejsu IListSource</span><span class="sxs-lookup"><span data-stu-id="e9030-123">How to: Implement the IListSource Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="e9030-124">Pokazuje, jak zaimplementować <xref:System.ComponentModel.IListSource> nie implementuje interfejsu, aby utworzyć klasę, które można powiązać <xref:System.Collections.IList>, ale zawiera listę z innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e9030-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="e9030-125">Instrukcje: zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych</span><span class="sxs-lookup"><span data-stu-id="e9030-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="e9030-126">Pokazuje, jak obsługiwać <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzeń, aby upewnić się, wszystkie formanty związany ze źródłem danych pozostają zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="e9030-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="e9030-127">Instrukcje: zapewnienie pozostawania wybranego wiersza w tabeli podrzędnej w prawidłowym położeniu</span><span class="sxs-lookup"><span data-stu-id="e9030-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="e9030-128">Pokazuje, jak zapewnić wybranego wiersza w tabeli podrzędnej nie zmienia się, w przypadku zmian z polem tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e9030-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="e9030-129">Zobacz też [interfejsy powiązane z wiązaniem danych](https://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [jak: Przejdź danych w formularzach Windows Forms](https://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [porady: Tworzenie prostej kontrolki powiązanej na formularzu Windows](https://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e9030-129">Also see [Interfaces Related to Data Binding](https://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [How to: Navigate Data in Windows Forms](https://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [How to: Create a Simple-Bound Control on a Windows Form](https://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e9030-130">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="e9030-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="e9030-131">W tym artykule opisano klasy, która reprezentuje powiązanie między składnikiem możliwej do wiązania i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e9030-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="e9030-132">W tym artykule opisano klasy, która hermetyzuje źródła danych dla powiązania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e9030-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e9030-133">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e9030-133">Related Sections</span></span>  
 [<span data-ttu-id="e9030-134">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="e9030-134">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 <span data-ttu-id="e9030-135">Zawiera listę tematów, które pokazują, jak używać <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="e9030-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="e9030-136">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e9030-136">DataGridView Control</span></span>](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="e9030-137">Zawiera listę tematów, które prezentują sposób użycia formantu datagrid możliwej do wiązania.</span><span class="sxs-lookup"><span data-stu-id="e9030-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="e9030-138">Zobacz też [uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e9030-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
