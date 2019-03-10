---
title: BindingSource — Składnik
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 54639edb512a8bc6c5909282d5e4c210439e2a6e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717599"
---
# <a name="bindingsource-component"></a><span data-ttu-id="d605a-102">BindingSource — Składnik</span><span class="sxs-lookup"><span data-stu-id="d605a-102">BindingSource Component</span></span>
<span data-ttu-id="d605a-103">Hermetyzuje źródła danych dla powiązania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d605a-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="d605a-104"><xref:System.Windows.Forms.BindingSource> Składnika służy do dwóch celów.</span><span class="sxs-lookup"><span data-stu-id="d605a-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="d605a-105">Po pierwsze zapewnia warstwę operatorów pośrednich podczas tworzenia wiązania kontrolek w formularzu do danych.</span><span class="sxs-lookup"><span data-stu-id="d605a-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="d605a-106">Jest to realizowane przez powiązanie <xref:System.Windows.Forms.BindingSource> do źródła danych, a następnie powiązanie kontrolek w formularzu do <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="d605a-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="d605a-107">Wszystkie dalszej interakcji z dane, w tym przeglądanie, sortowanie, filtrowanie i aktualizowaniem odbywa się przy użyciu wywołań <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="d605a-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="d605a-108">Drugi <xref:System.Windows.Forms.BindingSource> składnika może działać jako źródło silnie typizowanych danych.</span><span class="sxs-lookup"><span data-stu-id="d605a-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="d605a-109">Dodawanie typu <xref:System.Windows.Forms.BindingSource> składnika za pomocą <xref:System.Windows.Forms.BindingSource.Add%2A> metoda tworzy listę tego typu.</span><span class="sxs-lookup"><span data-stu-id="d605a-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d605a-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d605a-110">In This Section</span></span>  
 [<span data-ttu-id="d605a-111">BindingSource, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="d605a-111">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)  
 <span data-ttu-id="d605a-112">Ogólne pojęcia związane z <xref:System.Windows.Forms.BindingSource> składnik, który pozwala powiązać źródła danych z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="d605a-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="d605a-113">Instrukcje: Powiązywanie kontrolek formularzy Windows Forms bazy danych DBNull</span><span class="sxs-lookup"><span data-stu-id="d605a-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="d605a-114">Pokazuje, jak obsługiwać <xref:System.DBNull> wartości ze źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="d605a-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="d605a-115">Instrukcje: Sortowanie i filtrowanie danych ADO.NET za pomocą Windows składnika BindingSource formularzy</span><span class="sxs-lookup"><span data-stu-id="d605a-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="d605a-116">Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnika, aby zastosować sortuje i filtruje do wyświetlanych danych.</span><span class="sxs-lookup"><span data-stu-id="d605a-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="d605a-117">Instrukcje: Powiązanie z usługą sieci Web przy użyciu kontrolki BindingSource formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d605a-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="d605a-118">Ilustruje sposób używania <xref:System.Windows.Forms.BindingSource> składnika do utworzenia powiązania z usługą sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d605a-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="d605a-119">Instrukcje: Obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="d605a-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="d605a-120">Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnik do poprawnego działania obsługi błędów występujących w operacji wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="d605a-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="d605a-121">Instrukcje: Powiązanie z typem formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d605a-121">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="d605a-122">Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnika powiązanie z typem.</span><span class="sxs-lookup"><span data-stu-id="d605a-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="d605a-123">Instrukcje: Powiąż formant programu Windows Forms z obiektem fabryki</span><span class="sxs-lookup"><span data-stu-id="d605a-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="d605a-124">Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnika, aby powiązać obiekt fabryki lub metody.</span><span class="sxs-lookup"><span data-stu-id="d605a-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="d605a-125">Instrukcje: Dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d605a-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="d605a-126">Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składników do tworzenia nowych elementów i dodać je do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d605a-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="d605a-127">Instrukcje: Wywoływanie powiadomień o zmianie za BindingSource Resetitem</span><span class="sxs-lookup"><span data-stu-id="d605a-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="d605a-128">Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnik, aby wywoływać zdarzenia, powiadomienia o zmianie dla źródeł danych, które nie obsługują powiadomienie o zmianie.</span><span class="sxs-lookup"><span data-stu-id="d605a-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="d605a-129">Instrukcje: Wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="d605a-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="d605a-130">Pokazuje, jak używać typu, który dziedziczy z <xref:System.ComponentModel.INotifyPropertyChanged> z <xref:System.Windows.Forms.BindingSource> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d605a-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="d605a-131">Instrukcje: Odzwierciedlanie aktualizacji źródła danych w kontrolce Windows Forms przy użyciu kontrolki BindingSource</span><span class="sxs-lookup"><span data-stu-id="d605a-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="d605a-132">Pokazuje, jak reagować na zmiany źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="d605a-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="d605a-133">Instrukcje: Udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource</span><span class="sxs-lookup"><span data-stu-id="d605a-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="d605a-134">Ilustruje sposób używania <xref:System.Windows.Forms.BindingSource> powiązanie wielu formularzy do tego samego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d605a-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d605a-135">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d605a-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="d605a-136">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="d605a-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="d605a-137">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.BindingNavigator> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d605a-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d605a-138">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d605a-138">Related Sections</span></span>  
 [<span data-ttu-id="d605a-139">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d605a-139">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="d605a-140">Zawiera łącza do tematów opisujących architektura powiązanie danych formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="d605a-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="d605a-141">Zobacz też [powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d605a-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
