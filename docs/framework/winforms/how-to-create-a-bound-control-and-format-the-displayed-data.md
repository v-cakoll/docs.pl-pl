---
title: 'Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 543775894994c518d6069f697b145cedaa7af5b0
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015661"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="5062e-102">Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych</span><span class="sxs-lookup"><span data-stu-id="5062e-102">How to: Create a Bound Control and Format the Displayed Data</span></span>

<span data-ttu-id="5062e-103">Za pomocą powiązania danych Windows Forms można sformatować dane wyświetlane w kontrolce powiązanej z danymi przy użyciu okna dialogowego **Formatowanie i powiązanie zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="5062e-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>

## <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="5062e-104">Aby powiązać formant i sformatować wyświetlane dane</span><span class="sxs-lookup"><span data-stu-id="5062e-104">To bind a control and format the displayed data</span></span>

1. <span data-ttu-id="5062e-105">Nawiąż połączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="5062e-105">Connect to a data source.</span></span> <span data-ttu-id="5062e-106">Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia ze źródłem danych](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="5062e-106">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="5062e-107">W programie Visual Studio zaznacz kontrolkę w formularzu, a następnie otwórz okno **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="5062e-107">In Visual Studio, select the control on the form, and then open the **Properties** window.</span></span>

3. <span data-ttu-id="5062e-108">Rozwiń Właściwość **(DataBindings)** , a następnie w polu **(Zaawansowane)** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)), aby wyświetlić **Formatowanie i zaawansowane** Okno dialogowe powiązania, które zawiera kompletną listę właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5062e-108">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>

4. <span data-ttu-id="5062e-109">Wybierz właściwość, którą chcesz powiązać, a następnie wybierz strzałkę **powiązania** .</span><span class="sxs-lookup"><span data-stu-id="5062e-109">Select the property you want to bind, and then select the **Binding** arrow.</span></span>

     <span data-ttu-id="5062e-110">Zostanie wyświetlona lista dostępnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="5062e-110">A list of available data sources is displayed.</span></span>

5. <span data-ttu-id="5062e-111">Rozwiń źródło danych, do którego chcesz powiązać, dopóki nie znajdziesz jednego z nich.</span><span class="sxs-lookup"><span data-stu-id="5062e-111">Expand the data source you want to bind to until you find the single data element you want.</span></span>

     <span data-ttu-id="5062e-112">Na przykład jeśli powiążesz się z wartością kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.</span><span class="sxs-lookup"><span data-stu-id="5062e-112">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

6. <span data-ttu-id="5062e-113">Wybierz nazwę elementu, z którym ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="5062e-113">Select the name of an element to bind to.</span></span>

7. <span data-ttu-id="5062e-114">W polu **Typ formatu** wybierz format, który ma zostać zastosowany do danych wyświetlanych w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="5062e-114">In the **Format type** box, select the format you want to apply to the data displayed in the control.</span></span>

     <span data-ttu-id="5062e-115">W każdym przypadku można określić wartość wyświetlaną w kontrolce, jeśli źródło danych zawiera <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="5062e-115">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="5062e-116">W przeciwnym razie Opcje różnią się nieco w zależności od wybranego typu formatu.</span><span class="sxs-lookup"><span data-stu-id="5062e-116">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="5062e-117">W poniższej tabeli przedstawiono typy i opcje formatu.</span><span class="sxs-lookup"><span data-stu-id="5062e-117">The following table shows the format types and options.</span></span>

    |<span data-ttu-id="5062e-118">Typ formatu</span><span class="sxs-lookup"><span data-stu-id="5062e-118">Format type</span></span>|<span data-ttu-id="5062e-119">Opcja formatowania</span><span class="sxs-lookup"><span data-stu-id="5062e-119">Formatting option</span></span>|
    |-----------------|-----------------------|
    |<span data-ttu-id="5062e-120">Bez formatowania</span><span class="sxs-lookup"><span data-stu-id="5062e-120">No Formatting</span></span>|<span data-ttu-id="5062e-121">Brak opcji.</span><span class="sxs-lookup"><span data-stu-id="5062e-121">No options.</span></span>|
    |<span data-ttu-id="5062e-122">Numeric</span><span class="sxs-lookup"><span data-stu-id="5062e-122">Numeric</span></span>|<span data-ttu-id="5062e-123">Określ liczbę miejsc dziesiętnych przy użyciu funkcji **miejsca dziesiętnego** .</span><span class="sxs-lookup"><span data-stu-id="5062e-123">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="5062e-124">Waluta</span><span class="sxs-lookup"><span data-stu-id="5062e-124">Currency</span></span>|<span data-ttu-id="5062e-125">Określ liczbę miejsc dziesiętnych przy użyciu funkcji **miejsca dziesiętnego** .</span><span class="sxs-lookup"><span data-stu-id="5062e-125">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="5062e-126">Data i godzina</span><span class="sxs-lookup"><span data-stu-id="5062e-126">Date Time</span></span>|<span data-ttu-id="5062e-127">Wybierz, w jaki sposób ma być wyświetlana data i godzina, wybierając jeden z elementów w polu wyboru **typu** .</span><span class="sxs-lookup"><span data-stu-id="5062e-127">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|
    |<span data-ttu-id="5062e-128">Nauk</span><span class="sxs-lookup"><span data-stu-id="5062e-128">Scientific</span></span>|<span data-ttu-id="5062e-129">Określ liczbę miejsc dziesiętnych przy użyciu funkcji **miejsca dziesiętnego** .</span><span class="sxs-lookup"><span data-stu-id="5062e-129">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="5062e-130">Celnej</span><span class="sxs-lookup"><span data-stu-id="5062e-130">Custom</span></span>|<span data-ttu-id="5062e-131">Określ niestandardowy ciąg formatujący przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="5062e-131">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="5062e-132">Aby uzyskać więcej informacji, zobacz [Typy formatowania](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="5062e-132">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="5062e-133">**Uwaga:**  Niestandardowe ciągi formatujące nie są gwarantowane w celu pomyślnej rundy między źródłem danych i kontrolą powiązaną.</span><span class="sxs-lookup"><span data-stu-id="5062e-133">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="5062e-134">Zamiast tego obsłużyć <xref:System.Windows.Forms.Binding.Parse> zdarzenie or <xref:System.Windows.Forms.Binding.Format> dla powiązania i zastosować niestandardowe formatowanie w kodzie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5062e-134">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|

8. <span data-ttu-id="5062e-135">Wybierz **przycisk OK** , aby zamknąć okno dialogowe **Formatowanie i powiązanie zaawansowane** i wrócić do okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="5062e-135">Select **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>

## <a name="see-also"></a><span data-ttu-id="5062e-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5062e-136">See also</span></span>

- [<span data-ttu-id="5062e-137">Instrukcje: Tworzenie prostego formantu powiązanego w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5062e-137">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="5062e-138">Weryfikacja danych użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5062e-138">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="5062e-139">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5062e-139">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
