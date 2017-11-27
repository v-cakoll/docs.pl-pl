---
title: "Porady: tworzenie formantu powiązanego oraz formatowanie wyświetlanych danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8c2836d841215ed3ca8e04461b1298cd41287de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="d5ba2-102">Porady: tworzenie formantu powiązanego oraz formatowanie wyświetlanych danych</span><span class="sxs-lookup"><span data-stu-id="d5ba2-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="d5ba2-103">Z wiązanie danych formularzy systemu Windows, można sformatować danych wyświetlanych w formancie powiązane z danymi przy użyciu **formatowanie i zaawansowane powiązanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5ba2-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d5ba2-105">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d5ba2-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d5ba2-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="d5ba2-107">Powiązanie formantu i formatowanie wyświetlanych danych</span><span class="sxs-lookup"><span data-stu-id="d5ba2-107">To bind a control and format the displayed data</span></span>  
  
1.  <span data-ttu-id="d5ba2-108">Połączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="d5ba2-109">Aby uzyskać więcej informacji, zobacz [połączenie ze źródłem danych](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="d5ba2-109">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="d5ba2-110">W formularzu wybierz kontrolkę, a następnie otwórz okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3.  <span data-ttu-id="d5ba2-111">Rozwiń węzeł **(DataBindings)** właściwości, a następnie w **(zaawansowane)** kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu] (../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) do wyświetlenia **formatowanie i zaawansowane powiązanie** okno dialogowe, które zawiera pełną listę właściwości dla tego formantu.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4.  <span data-ttu-id="d5ba2-112">Wybierz właściwość, aby powiązać, a następnie kliknij przycisk **powiązanie** strzałki.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="d5ba2-113">Zostanie wyświetlona lista dostępnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-113">A list of available data sources is displayed.</span></span>  
  
5.  <span data-ttu-id="d5ba2-114">Rozwiń źródło danych, które chcesz powiązać do momentu znalezienia element danych, który ma.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="d5ba2-115">Na przykład są wiązane wartość kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6.  <span data-ttu-id="d5ba2-116">Kliknij nazwę elementu, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-116">Click the name of an element to bind to.</span></span>  
  
7.  <span data-ttu-id="d5ba2-117">W **Format typu** kliknij formatu, który chcesz zastosować do danych wyświetlanych w formancie.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="d5ba2-118">W każdym przypadku można określić wartość wyświetlana w formancie, jeśli źródło danych zawiera <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="d5ba2-119">W przeciwnym razie wartość opcji się nieco różnić, w zależności od wybranego typu formatu.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="d5ba2-120">W poniższej tabeli przedstawiono typy formatu i opcje.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="d5ba2-121">Typ formatu</span><span class="sxs-lookup"><span data-stu-id="d5ba2-121">Format type</span></span>|<span data-ttu-id="d5ba2-122">Opcja formatowania</span><span class="sxs-lookup"><span data-stu-id="d5ba2-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="d5ba2-123">Bez formatowania</span><span class="sxs-lookup"><span data-stu-id="d5ba2-123">No Formatting</span></span>|<span data-ttu-id="d5ba2-124">Brak opcji.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-124">No options.</span></span>|  
    |<span data-ttu-id="d5ba2-125">numeryczne</span><span class="sxs-lookup"><span data-stu-id="d5ba2-125">Numeric</span></span>|<span data-ttu-id="d5ba2-126">Określ liczbę miejsc dziesiętnych, używając **miejsc dziesiętnych** formantu góra dół.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="d5ba2-127">Waluta</span><span class="sxs-lookup"><span data-stu-id="d5ba2-127">Currency</span></span>|<span data-ttu-id="d5ba2-128">Określ liczbę miejsc dziesiętnych, używając **miejsc dziesiętnych** formantu góra dół.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="d5ba2-129">Data i godzina</span><span class="sxs-lookup"><span data-stu-id="d5ba2-129">Date Time</span></span>|<span data-ttu-id="d5ba2-130">Wybierz sposób wyświetlania daty i godziny wybranie jednego z elementów w **typu** pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="d5ba2-131">Naukowe</span><span class="sxs-lookup"><span data-stu-id="d5ba2-131">Scientific</span></span>|<span data-ttu-id="d5ba2-132">Określ liczbę miejsc dziesiętnych, używając **miejsc dziesiętnych** formantu góra dół.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="d5ba2-133">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="d5ba2-133">Custom</span></span>|<span data-ttu-id="d5ba2-134">Określ ciąg formatu niestandardowego za pomocą.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="d5ba2-135">Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d5ba2-135">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="d5ba2-136">**Uwaga:** pomyślnie obiegu między źródłem danych a powiązanej Kontrolki niestandardowe ciągi formatów nie ma gwarancji.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="d5ba2-137">Obsługi zamiast <xref:System.Windows.Forms.Binding.Parse> lub <xref:System.Windows.Forms.Binding.Format> zdarzenia dla tego powiązania i zastosować niestandardowe formatowanie kodu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8.  <span data-ttu-id="d5ba2-138">Kliknij przycisk **OK** zamknąć **formatowanie i zaawansowane powiązanie** okno dialogowe i wrócić do okna właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5ba2-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ba2-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5ba2-139">See Also</span></span>  
 [<span data-ttu-id="d5ba2-140">Porady: Tworzenie prostego formantu powiązanego na formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d5ba2-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [<span data-ttu-id="d5ba2-141">Sprawdzanie poprawności danych użytkownika w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d5ba2-141">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [<span data-ttu-id="d5ba2-142">Powiązanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d5ba2-142">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
