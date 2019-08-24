---
title: 'Instrukcje: Tworzenie prostej kontrolki powiązanej na formularzu Windows Form'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: df87f00e6e03de67c3fb1adc28472c96f4a47ef4
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015631"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="02208-102">Instrukcje: Tworzenie prostego formantu powiązanego w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="02208-102">How to: Create a simple-bound control on a Windows Form</span></span>

<span data-ttu-id="02208-103">Przy użyciu *prostego powiązania*można wyświetlić pojedynczy element danych, taki jak wartość kolumny z tabeli zestawu danych, w formancie.</span><span class="sxs-lookup"><span data-stu-id="02208-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="02208-104">Można utworzyć prostą dowolną właściwość formantu do wartości danych.</span><span class="sxs-lookup"><span data-stu-id="02208-104">You can simple-bind any property of a control to a data value.</span></span>

## <a name="to-simple-bind-a-control"></a><span data-ttu-id="02208-105">Aby powiązać formant z prostą</span><span class="sxs-lookup"><span data-stu-id="02208-105">To simple-bind a control</span></span>

1. <span data-ttu-id="02208-106">Nawiąż połączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="02208-106">Connect to a data source.</span></span> <span data-ttu-id="02208-107">Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia ze źródłem danych](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="02208-107">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="02208-108">W programie Visual Studio zaznacz kontrolkę w formularzu i Wyświetl okno **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="02208-108">In Visual Studio, select the control on the form and display the **Properties** window.</span></span>

3. <span data-ttu-id="02208-109">Rozwiń Właściwość **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="02208-109">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="02208-110">Właściwości najczęściej powiązane są wyświetlane pod właściwością **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="02208-110">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="02208-111">Na przykład w większości formantów właściwość **Text** jest najczęściej powiązana.</span><span class="sxs-lookup"><span data-stu-id="02208-111">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="02208-112">Jeśli właściwość, którą chcesz powiązać, nie jest jedną z często powiązanych właściwości, kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości ](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)programu Visual Studio) w polu **(Zaawansowane)** , aby wyświetlić  **Formatowanie i zaawansowane** okno dialogowe powiązania z pełną listą właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="02208-112">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="02208-113">Wybierz właściwość, którą chcesz powiązać, a następnie kliknij strzałkę listy rozwijanej w obszarze **powiązania**.</span><span class="sxs-lookup"><span data-stu-id="02208-113">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="02208-114">Zostanie wyświetlona lista dostępnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="02208-114">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="02208-115">Rozwiń źródło danych, do którego chcesz powiązać, dopóki nie znajdziesz jednego z nich.</span><span class="sxs-lookup"><span data-stu-id="02208-115">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="02208-116">Na przykład jeśli powiążesz się z wartością kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.</span><span class="sxs-lookup"><span data-stu-id="02208-116">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="02208-117">Kliknij nazwę elementu, z którym ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="02208-117">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="02208-118">Jeśli pracujesz w oknie dialogowym **Formatowanie i zaawansowane powiązanie** , kliknij przycisk **OK** , aby powrócić do okna **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="02208-118">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="02208-119">Jeśli chcesz powiązać dodatkowe właściwości kontrolki, powtórz kroki od 3 do 7.</span><span class="sxs-lookup"><span data-stu-id="02208-119">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="02208-120">Ponieważ kontrolki proste powiązane pokazują tylko jeden element danych, jest to bardzo typowy do uwzględnienia logiki nawigacji w formularzu systemu Windows z prostymi kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="02208-120">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="02208-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02208-121">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="02208-122">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02208-122">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="02208-123">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02208-123">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
