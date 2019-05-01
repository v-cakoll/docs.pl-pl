---
title: Powiązywanie danych formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: ed456807137e8cf7594bc50eb0eebb67b88e6b40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800116"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="0d5fd-102">Powiązywanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0d5fd-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="0d5fd-103">Powiązanie danych w formularzach Windows Forms zapewnia sposób wyświetlania i zmiany informacji ze źródła danych w kontrolkach w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="0d5fd-104">Możesz powiązać zarówno źródeł danych tradycyjnych, jak i praktycznie dowolne strukturę, która zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d5fd-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0d5fd-105">In This Section</span></span>  
 [<span data-ttu-id="0d5fd-106">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d5fd-106">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="0d5fd-107">Zawiera omówienie powiązanie danych w formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="0d5fd-108">Źródła danych obsługiwane przez formularze Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d5fd-108">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="0d5fd-109">W tym artykule opisano źródeł danych, które mogą służyć za pomocą interfejsu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="0d5fd-110">Interfejsy dotyczące wiązania danych</span><span class="sxs-lookup"><span data-stu-id="0d5fd-110">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="0d5fd-111">Opisano kilka interfejsów używane dla wiązania danych Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="0d5fd-112">Instrukcje: Nawigowanie po danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d5fd-112">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="0d5fd-113">Pokazuje, jak przechodzenie przez elementy w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="0d5fd-114">Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d5fd-114">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="0d5fd-115">W tym artykule opisano różne rodzaje powiadomienia o zmianie dla powiązania danych Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="0d5fd-116">Instrukcje: Implementowanie interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="0d5fd-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="0d5fd-117">Pokazuje, jak zaimplementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="0d5fd-118">Interfejs komunikuje się kontrolki powiązane zmiany właściwości w obiekcie firmy</span><span class="sxs-lookup"><span data-stu-id="0d5fd-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="0d5fd-119">Instrukcje: Stosowanie wzorca PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="0d5fd-119">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="0d5fd-120">Przedstawia sposób zastosowania *PropertyName*wzorzec zmieniono właściwości formant użytkownika interfejsu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="0d5fd-121">Instrukcje: Implementowanie interfejsu ITypedList</span><span class="sxs-lookup"><span data-stu-id="0d5fd-121">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="0d5fd-122">Pokazuje, jak włączyć funkcję odnajdywania schematu, który może być powiązana lista implementując <xref:System.ComponentModel.ITypedList> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="0d5fd-123">Instrukcje: Implementowanie interfejsu IListSource</span><span class="sxs-lookup"><span data-stu-id="0d5fd-123">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="0d5fd-124">Pokazuje, jak zaimplementować <xref:System.ComponentModel.IListSource> nie implementuje interfejsu, aby utworzyć klasę, które można powiązać <xref:System.Collections.IList>, ale zawiera listę z innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="0d5fd-125">Instrukcje: Upewnij się, wiele formantów powiązanych z tym samym źródłem danych pozostają zsynchronizowane</span><span class="sxs-lookup"><span data-stu-id="0d5fd-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="0d5fd-126">Pokazuje, jak obsługiwać <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzeń, aby upewnić się, wszystkie formanty związany ze źródłem danych pozostają zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="0d5fd-127">Instrukcje: Upewnij się, że zaznaczony wiersz w tabeli podrzędnej pozostaje w prawidłowym położeniu</span><span class="sxs-lookup"><span data-stu-id="0d5fd-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="0d5fd-128">Pokazuje, jak zapewnić wybranego wiersza w tabeli podrzędnej nie zmienia się, w przypadku zmian z polem tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="0d5fd-129">Zobacz też [interfejsy powiązane z wiązaniem danych](interfaces-related-to-data-binding.md), [jak: Nawigowanie po danych w formularzach Windows Forms](how-to-navigate-data-in-windows-forms.md), i [jak: Tworzenie prostego formantu powiązanego na formularzu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="0d5fd-129">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0d5fd-130">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="0d5fd-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="0d5fd-131">W tym artykule opisano klasy, która reprezentuje powiązanie między składnikiem możliwej do wiązania i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="0d5fd-132">W tym artykule opisano klasy, która hermetyzuje źródła danych dla powiązania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0d5fd-133">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0d5fd-133">Related Sections</span></span>  
 [<span data-ttu-id="0d5fd-134">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="0d5fd-134">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="0d5fd-135">Zawiera listę tematów, które pokazują, jak używać <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="0d5fd-136">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0d5fd-136">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="0d5fd-137">Zawiera listę tematów, które prezentują sposób użycia formantu datagrid możliwej do wiązania.</span><span class="sxs-lookup"><span data-stu-id="0d5fd-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="0d5fd-138">Zobacz też [uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="0d5fd-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
