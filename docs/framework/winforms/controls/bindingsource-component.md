---
title: "BindingSource — Składnik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 006cafafdf8e3c3f4da77394d6155fa52e113b58
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="bindingsource-component"></a><span data-ttu-id="1a558-102">BindingSource — Składnik</span><span class="sxs-lookup"><span data-stu-id="1a558-102">BindingSource Component</span></span>
<span data-ttu-id="1a558-103">Hermetyzuje źródło danych dla powiązania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="1a558-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="1a558-104"><xref:System.Windows.Forms.BindingSource> Składnika służy dwóch celów.</span><span class="sxs-lookup"><span data-stu-id="1a558-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="1a558-105">Po pierwsze zapewnia warstwę pośredników podczas wiązania z danymi formantów w formularzu.</span><span class="sxs-lookup"><span data-stu-id="1a558-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="1a558-106">Jest to osiągane przez powiązanie <xref:System.Windows.Forms.BindingSource> składnika do źródła danych, a następnie powiązanie formantów w formularzu do <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="1a558-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="1a558-107">Wszystkie dalsze interakcji z danymi, w tym przeglądanie, sortowanie, filtrowanie i aktualizowanie, jest realizowane za pomocą wywołania <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="1a558-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="1a558-108">Drugi, <xref:System.Windows.Forms.BindingSource> składnika może działać jako źródło danych jednoznacznie.</span><span class="sxs-lookup"><span data-stu-id="1a558-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="1a558-109">Dodawanie typów do <xref:System.Windows.Forms.BindingSource> składnik o <xref:System.Windows.Forms.BindingSource.Add%2A> metoda tworzy listę tego typu.</span><span class="sxs-lookup"><span data-stu-id="1a558-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a558-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1a558-110">In This Section</span></span>  
 [<span data-ttu-id="1a558-111">Informacje o składniku BindingSource</span><span class="sxs-lookup"><span data-stu-id="1a558-111">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 <span data-ttu-id="1a558-112">Ogólne pojęcia związane z <xref:System.Windows.Forms.BindingSource> składnika, dzięki czemu można powiązać źródła danych z formantu.</span><span class="sxs-lookup"><span data-stu-id="1a558-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="1a558-113">Porady: powiązywanie formantów formularzy systemu Windows wartościami bazy danych DBNull</span><span class="sxs-lookup"><span data-stu-id="1a558-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="1a558-114">Pokazuje sposób obsługi <xref:System.DBNull> wartości z źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="1a558-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="1a558-115">Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1a558-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="1a558-116">Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składnika do zastosowania sortowania i filtrów do wyświetlanych danych.</span><span class="sxs-lookup"><span data-stu-id="1a558-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="1a558-117">Porady: powiązanie z usługą sieci Web za pomocą formantu BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1a558-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="1a558-118">Przedstawia sposób użycia <xref:System.Windows.Forms.BindingSource> składnik do powiązania z usługą sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1a558-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="1a558-119">Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="1a558-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="1a558-120">Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składnik, aby obsługiwać błędów występujących w operacji wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="1a558-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="1a558-121">Porady: powiązanie formantu formularzy systemu Windows z typem</span><span class="sxs-lookup"><span data-stu-id="1a558-121">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="1a558-122">Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników, które można powiązać z typem.</span><span class="sxs-lookup"><span data-stu-id="1a558-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="1a558-123">Porady: powiązanie formantu formularzy systemu Windows z obiektem fabryki</span><span class="sxs-lookup"><span data-stu-id="1a558-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="1a558-124">Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników, aby powiązać obiekt fabryki lub metody.</span><span class="sxs-lookup"><span data-stu-id="1a558-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="1a558-125">Porady: dostosowywanie dodawania elementu przy formantu BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1a558-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="1a558-126">Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników do tworzenia nowych elementów i dodaj je do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1a558-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="1a558-127">Porady: wywoływanie powiadomień o zmianie za pomocą metody BindingSource Resetitem</span><span class="sxs-lookup"><span data-stu-id="1a558-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="1a558-128">Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników, aby wywołać zdarzenia zmiany powiadomienia dla źródeł danych, które nie obsługują powiadomienie o zmianie.</span><span class="sxs-lookup"><span data-stu-id="1a558-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="1a558-129">Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="1a558-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="1a558-130">Przedstawiono sposób użycia typu, która dziedziczy <xref:System.ComponentModel.INotifyPropertyChanged> z <xref:System.Windows.Forms.BindingSource> formantu.</span><span class="sxs-lookup"><span data-stu-id="1a558-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="1a558-131">Porady: odzwierciedlanie aktualizacji źródła danych w formancie formularzy systemu Windows za pomocą elementu BindingSource</span><span class="sxs-lookup"><span data-stu-id="1a558-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="1a558-132">Pokazuje, jak reagować na zmiany w źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="1a558-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="1a558-133">Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource</span><span class="sxs-lookup"><span data-stu-id="1a558-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="1a558-134">Przedstawia sposób użycia <xref:System.Windows.Forms.BindingSource> powiązanie wielu formularzy do tego samego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1a558-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1a558-135">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="1a558-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="1a558-136">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="1a558-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="1a558-137">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.BindingNavigator> formantu.</span><span class="sxs-lookup"><span data-stu-id="1a558-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1a558-138">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1a558-138">Related Sections</span></span>  
 [<span data-ttu-id="1a558-139">Powiązanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1a558-139">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="1a558-140">Zawiera łącza do tematów opisujących architektura powiązanie danych formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1a558-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="1a558-141">Zobacz też [powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="1a558-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
