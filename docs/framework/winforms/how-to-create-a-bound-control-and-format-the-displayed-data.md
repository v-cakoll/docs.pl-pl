---
title: 'Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 0f56fc5fa345cbe4584b61ae2622dfb0dfb35be8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225537"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="56cb6-102">Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych</span><span class="sxs-lookup"><span data-stu-id="56cb6-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="56cb6-103">Za pomocą powiązanie danych formularzy Windows, możesz sformatować dane wyświetlane w kontrolce powiązanych z danymi za pomocą **formatowanie i zaawansowane powiązanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="56cb6-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56cb6-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="56cb6-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="56cb6-105">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="56cb6-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="56cb6-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="56cb6-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="56cb6-107">Aby powiązać formant oraz formatowanie wyświetlanych danych</span><span class="sxs-lookup"><span data-stu-id="56cb6-107">To bind a control and format the displayed data</span></span>  
  
1.  <span data-ttu-id="56cb6-108">Łączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="56cb6-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="56cb6-109">Aby uzyskać więcej informacji, zobacz [nawiązania połączenia ze źródłem danych](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="56cb6-109">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="56cb6-110">W formularzu wybierz kontrolkę, a następnie otwórz okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="56cb6-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3.  <span data-ttu-id="56cb6-111">Rozwiń **(powiązania danych)** właściwości, a następnie w polu **(zaawansowane)** polu i kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](./media/vbellipsesbutton.png " vbEllipsesButton")) do wyświetlenia **formatowanie i powiązywanie zaawansowane** okno dialogowe, które zawiera pełną listę właściwości dla tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="56cb6-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](./media/vbellipsesbutton.png "vbEllipsesButton")) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4.  <span data-ttu-id="56cb6-112">Wybierz właściwość, aby powiązać, a następnie kliknij przycisk **powiązanie** strzałki.</span><span class="sxs-lookup"><span data-stu-id="56cb6-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="56cb6-113">Zostanie wyświetlona lista dostępnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="56cb6-113">A list of available data sources is displayed.</span></span>  
  
5.  <span data-ttu-id="56cb6-114">Rozwiń źródło danych, które chcesz powiązać, dopóki nie znajdziesz element danych jednego, który ma.</span><span class="sxs-lookup"><span data-stu-id="56cb6-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="56cb6-115">Na przykład jeśli dokonywane jest wiązanie wartość kolumny w tabeli zestawu danych, rozwiń węzeł z nazwą zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.</span><span class="sxs-lookup"><span data-stu-id="56cb6-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6.  <span data-ttu-id="56cb6-116">Kliknij nazwę elementu można powiązać.</span><span class="sxs-lookup"><span data-stu-id="56cb6-116">Click the name of an element to bind to.</span></span>  
  
7.  <span data-ttu-id="56cb6-117">W **sformatować typu** kliknij format, w którym chcesz zastosować do danych wyświetlanych w formancie.</span><span class="sxs-lookup"><span data-stu-id="56cb6-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="56cb6-118">W każdym przypadku można określić wartości wyświetlanej w kontrolce, jeśli źródło danych zawiera <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="56cb6-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="56cb6-119">W przeciwnym razie różne opcje nieco w zależności od wybranego typu formatu.</span><span class="sxs-lookup"><span data-stu-id="56cb6-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="56cb6-120">W poniższej tabeli przedstawiono typy formatów i opcje.</span><span class="sxs-lookup"><span data-stu-id="56cb6-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="56cb6-121">Typ formatu</span><span class="sxs-lookup"><span data-stu-id="56cb6-121">Format type</span></span>|<span data-ttu-id="56cb6-122">Opcja formatowania</span><span class="sxs-lookup"><span data-stu-id="56cb6-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="56cb6-123">Bez formatowania</span><span class="sxs-lookup"><span data-stu-id="56cb6-123">No Formatting</span></span>|<span data-ttu-id="56cb6-124">Brak opcji.</span><span class="sxs-lookup"><span data-stu-id="56cb6-124">No options.</span></span>|  
    |<span data-ttu-id="56cb6-125">Numeryczne</span><span class="sxs-lookup"><span data-stu-id="56cb6-125">Numeric</span></span>|<span data-ttu-id="56cb6-126">Określ liczbę miejsc dziesiętnych, za pomocą **miejsc dziesiętnych** formantu góra dół.</span><span class="sxs-lookup"><span data-stu-id="56cb6-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="56cb6-127">Waluta</span><span class="sxs-lookup"><span data-stu-id="56cb6-127">Currency</span></span>|<span data-ttu-id="56cb6-128">Określ liczbę miejsc dziesiętnych, za pomocą **miejsc dziesiętnych** formantu góra dół.</span><span class="sxs-lookup"><span data-stu-id="56cb6-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="56cb6-129">Data i godzina</span><span class="sxs-lookup"><span data-stu-id="56cb6-129">Date Time</span></span>|<span data-ttu-id="56cb6-130">Wybierz sposób wyświetlania daty i godziny, wybierając jeden z elementów w **typu** pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="56cb6-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="56cb6-131">naukowe</span><span class="sxs-lookup"><span data-stu-id="56cb6-131">Scientific</span></span>|<span data-ttu-id="56cb6-132">Określ liczbę miejsc dziesiętnych, za pomocą **miejsc dziesiętnych** formantu góra dół.</span><span class="sxs-lookup"><span data-stu-id="56cb6-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="56cb6-133">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="56cb6-133">Custom</span></span>|<span data-ttu-id="56cb6-134">Określ ciąg formatu niestandardowego za pomocą.</span><span class="sxs-lookup"><span data-stu-id="56cb6-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="56cb6-135">Aby uzyskać więcej informacji, zobacz [typy formatowania](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="56cb6-135">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="56cb6-136">**Uwaga:**  Tworzenie niestandardowych formatów ciągów nie ma gwarancji pomyślnie komunikacji dwustronnej między źródłem danych i powiązanej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="56cb6-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="56cb6-137">Zamiast tego obsługiwać <xref:System.Windows.Forms.Binding.Parse> lub <xref:System.Windows.Forms.Binding.Format> zdarzeń dla wiązania i zastosować niestandardowe formatowanie w kodzie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="56cb6-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8.  <span data-ttu-id="56cb6-138">Kliknij przycisk **OK** zamknąć **formatowanie i powiązywanie zaawansowane** okno dialogowe i wrócić do okna właściwości.</span><span class="sxs-lookup"><span data-stu-id="56cb6-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56cb6-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56cb6-139">See also</span></span>

- [<span data-ttu-id="56cb6-140">Instrukcje: Tworzenie prostej kontrolki powiązanej na formularzu Windows Form</span><span class="sxs-lookup"><span data-stu-id="56cb6-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="56cb6-141">Walidacja danych użytkownika w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="56cb6-141">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="56cb6-142">Powiązywanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="56cb6-142">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
