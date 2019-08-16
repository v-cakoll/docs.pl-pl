---
title: 'Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 052e619acb23fb2e25f42daf7b4eaaacb0688f31
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039427"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="d190d-102">Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych</span><span class="sxs-lookup"><span data-stu-id="d190d-102">How to: Create a Bound Control and Format the Displayed Data</span></span>

<span data-ttu-id="d190d-103">Za pomocą powiązania danych Windows Forms można sformatować dane wyświetlane w kontrolce powiązanej z danymi przy użyciu okna dialogowego **Formatowanie i powiązanie zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="d190d-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>


### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="d190d-104">Aby powiązać formant i sformatować wyświetlane dane</span><span class="sxs-lookup"><span data-stu-id="d190d-104">To bind a control and format the displayed data</span></span>

1. <span data-ttu-id="d190d-105">Nawiąż połączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="d190d-105">Connect to a data source.</span></span>

     <span data-ttu-id="d190d-106">Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia ze źródłem danych](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="d190d-106">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="d190d-107">W formularzu zaznacz kontrolkę, a następnie otwórz okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="d190d-107">In the form, select the control, and then open the Properties window.</span></span>

3. <span data-ttu-id="d190d-108">Rozwiń Właściwość **(DataBindings)** , a następnie w polu **(Zaawansowane)** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)), aby wyświetlić **Formatowanie i zaawansowane** Okno dialogowe powiązania, które zawiera kompletną listę właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d190d-108">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>

4. <span data-ttu-id="d190d-109">Wybierz właściwość, którą chcesz powiązać, a następnie kliknij strzałkę **powiązania** .</span><span class="sxs-lookup"><span data-stu-id="d190d-109">Select the property you want to bind, and then click the **Binding** arrow.</span></span>

     <span data-ttu-id="d190d-110">Zostanie wyświetlona lista dostępnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="d190d-110">A list of available data sources is displayed.</span></span>

5. <span data-ttu-id="d190d-111">Rozwiń źródło danych, do którego chcesz powiązać, dopóki nie znajdziesz jednego z nich.</span><span class="sxs-lookup"><span data-stu-id="d190d-111">Expand the data source you want to bind to until you find the single data element you want.</span></span>

     <span data-ttu-id="d190d-112">Na przykład jeśli powiążesz się z wartością kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.</span><span class="sxs-lookup"><span data-stu-id="d190d-112">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

6. <span data-ttu-id="d190d-113">Kliknij nazwę elementu, z którym ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="d190d-113">Click the name of an element to bind to.</span></span>

7. <span data-ttu-id="d190d-114">W polu **Typ formatu** kliknij format, który ma zostać zastosowany do danych wyświetlanych w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="d190d-114">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>

     <span data-ttu-id="d190d-115">W każdym przypadku można określić wartość wyświetlaną w kontrolce, jeśli źródło danych zawiera <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="d190d-115">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="d190d-116">W przeciwnym razie Opcje różnią się nieco w zależności od wybranego typu formatu.</span><span class="sxs-lookup"><span data-stu-id="d190d-116">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="d190d-117">W poniższej tabeli przedstawiono typy i opcje formatu.</span><span class="sxs-lookup"><span data-stu-id="d190d-117">The following table shows the format types and options.</span></span>

    |<span data-ttu-id="d190d-118">Typ formatu</span><span class="sxs-lookup"><span data-stu-id="d190d-118">Format type</span></span>|<span data-ttu-id="d190d-119">Opcja formatowania</span><span class="sxs-lookup"><span data-stu-id="d190d-119">Formatting option</span></span>|
    |-----------------|-----------------------|
    |<span data-ttu-id="d190d-120">Bez formatowania</span><span class="sxs-lookup"><span data-stu-id="d190d-120">No Formatting</span></span>|<span data-ttu-id="d190d-121">Brak opcji.</span><span class="sxs-lookup"><span data-stu-id="d190d-121">No options.</span></span>|
    |<span data-ttu-id="d190d-122">Numeric</span><span class="sxs-lookup"><span data-stu-id="d190d-122">Numeric</span></span>|<span data-ttu-id="d190d-123">Określ liczbę miejsc dziesiętnych przy użyciu funkcji **miejsca dziesiętnego** .</span><span class="sxs-lookup"><span data-stu-id="d190d-123">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="d190d-124">Waluta</span><span class="sxs-lookup"><span data-stu-id="d190d-124">Currency</span></span>|<span data-ttu-id="d190d-125">Określ liczbę miejsc dziesiętnych przy użyciu funkcji **miejsca dziesiętnego** .</span><span class="sxs-lookup"><span data-stu-id="d190d-125">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="d190d-126">Data i godzina</span><span class="sxs-lookup"><span data-stu-id="d190d-126">Date Time</span></span>|<span data-ttu-id="d190d-127">Wybierz, w jaki sposób ma być wyświetlana data i godzina, wybierając jeden z elementów w polu wyboru **typu** .</span><span class="sxs-lookup"><span data-stu-id="d190d-127">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|
    |<span data-ttu-id="d190d-128">Nauk</span><span class="sxs-lookup"><span data-stu-id="d190d-128">Scientific</span></span>|<span data-ttu-id="d190d-129">Określ liczbę miejsc dziesiętnych przy użyciu funkcji **miejsca dziesiętnego** .</span><span class="sxs-lookup"><span data-stu-id="d190d-129">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="d190d-130">Celnej</span><span class="sxs-lookup"><span data-stu-id="d190d-130">Custom</span></span>|<span data-ttu-id="d190d-131">Określ niestandardowy ciąg formatujący przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="d190d-131">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="d190d-132">Aby uzyskać więcej informacji, zobacz [Typy formatowania](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d190d-132">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="d190d-133">**Uwaga:**  Niestandardowe ciągi formatujące nie są gwarantowane w celu pomyślnej rundy między źródłem danych i kontrolą powiązaną.</span><span class="sxs-lookup"><span data-stu-id="d190d-133">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="d190d-134">Zamiast tego obsłużyć <xref:System.Windows.Forms.Binding.Parse> zdarzenie or <xref:System.Windows.Forms.Binding.Format> dla powiązania i zastosować niestandardowe formatowanie w kodzie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d190d-134">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|

8. <span data-ttu-id="d190d-135">Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Formatowanie i łączenie zaawansowane** i wrócić do okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="d190d-135">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>

## <a name="see-also"></a><span data-ttu-id="d190d-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d190d-136">See also</span></span>

- [<span data-ttu-id="d190d-137">Instrukcje: Tworzenie prostego formantu powiązanego w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d190d-137">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="d190d-138">Weryfikacja danych użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d190d-138">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="d190d-139">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d190d-139">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
