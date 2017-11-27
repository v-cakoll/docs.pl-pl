---
title: "Powiązywanie danych formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60a9f66fec64ceda71dd5b70211b897c84113429
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="ee6b5-102">Powiązywanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ee6b5-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="ee6b5-103">Powiązanie danych w formularzach systemu Windows zapewnia sposób wyświetlania i wprowadź zmiany do informacji ze źródła danych w kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="ee6b5-104">Można powiązać zarówno źródeł danych tradycyjnych, jak i prawie każdego struktury, która zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee6b5-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ee6b5-105">In This Section</span></span>  
 [<span data-ttu-id="ee6b5-106">Powiązanie danych i formularze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ee6b5-106">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 <span data-ttu-id="ee6b5-107">Zawiera omówienie powiązanie danych w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="ee6b5-108">Źródła danych obsługiwane przez program Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee6b5-108">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="ee6b5-109">Zawiera opis źródła danych, które mogą być używane z formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="ee6b5-110">Interfejsy dotyczące powiązania danych</span><span class="sxs-lookup"><span data-stu-id="ee6b5-110">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 <span data-ttu-id="ee6b5-111">Opisuje kilka interfejsów używane z wiązanie danych formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="ee6b5-112">Porady: nawigowanie w danych w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ee6b5-112">How to: Navigate Data in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="ee6b5-113">Pokazuje, jak poruszać się po elementów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="ee6b5-114">Powiadomienie o zmianie w powiązaniu danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ee6b5-114">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="ee6b5-115">W tym artykule opisano różne typy powiadomienia o zmianie dla powiązania danych formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="ee6b5-116">Porady: Implementowanie interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="ee6b5-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="ee6b5-117">Pokazuje, jak wdrożyć <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="ee6b5-118">Interfejs komunikuje się z powiązanej kontrolki zmiany właściwości obiektu biznesowego</span><span class="sxs-lookup"><span data-stu-id="ee6b5-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="ee6b5-119">Porady: stosowanie wzorca PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="ee6b5-119">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="ee6b5-120">Pokazuje, jak zastosować *PropertyName*zmienione wzorzec do właściwości formantu użytkownika formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="ee6b5-121">Porady: Implementowanie interfejsu ITypedList</span><span class="sxs-lookup"><span data-stu-id="ee6b5-121">How to: Implement the ITypedList Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="ee6b5-122">Przedstawia sposób włączenia funkcji wykrywania schematu dla listy może być powiązana z zastosowaniem <xref:System.ComponentModel.ITypedList> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="ee6b5-123">Porady: Implementowanie interfejsu IListSource</span><span class="sxs-lookup"><span data-stu-id="ee6b5-123">How to: Implement the IListSource Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="ee6b5-124">Pokazuje, jak wdrożyć <xref:System.ComponentModel.IListSource> nie implementuje interfejsu do utworzenia możliwej do wiązania klasy <xref:System.Collections.IList>, ale zawiera listę z innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="ee6b5-125">Porady: Upewnij się, wiele formantów powiązanych z tym samym źródłem danych pozostają zsynchronizowane</span><span class="sxs-lookup"><span data-stu-id="ee6b5-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="ee6b5-126">Pokazuje sposób obsługi <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzeń, aby upewnić się, wszystkie formanty powiązane ze źródłem danych pozostają zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="ee6b5-127">Porady: Upewnij się, pozostaje wybranego wiersza w tabeli podrzędnej w prawidłowym położeniu</span><span class="sxs-lookup"><span data-stu-id="ee6b5-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="ee6b5-128">Przedstawia sposób zapewnienia wybranego wiersza w tabeli podrzędnej nie ulega zmianie, wprowadzania zmian do pola w tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="ee6b5-129">Zobacz też [interfejsy dotyczące powiązania danych](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [porady: Przejdź danych w formularzach systemu Windows](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [porady: Tworzenie prostego formantu powiązanego na formularzu systemu Windows](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ee6b5-129">Also see [Interfaces Related to Data Binding](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [How to: Navigate Data in Windows Forms](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [How to: Create a Simple-Bound Control on a Windows Form](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ee6b5-130">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ee6b5-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="ee6b5-131">W tym artykule opisano klasy, która reprezentuje powiązanie między składnikiem powiązania i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="ee6b5-132">W tym artykule opisano klasy, która hermetyzuje źródło danych dla powiązania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ee6b5-133">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ee6b5-133">Related Sections</span></span>  
 [<span data-ttu-id="ee6b5-134">BindingSource — składnik</span><span class="sxs-lookup"><span data-stu-id="ee6b5-134">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 <span data-ttu-id="ee6b5-135">Zawiera listę tematów, które prezentują sposób użycia <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="ee6b5-136">DataGridView — formant</span><span class="sxs-lookup"><span data-stu-id="ee6b5-136">DataGridView Control</span></span>](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="ee6b5-137">Zawiera listę tematów, które pokazują, jak używać formantu datagrid może być powiązana.</span><span class="sxs-lookup"><span data-stu-id="ee6b5-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="ee6b5-138">Zobacz też [uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ee6b5-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
