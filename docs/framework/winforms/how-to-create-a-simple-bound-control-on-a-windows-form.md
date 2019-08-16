---
title: 'Instrukcje: Tworzenie prostej kontrolki powiązanej na formularzu Windows Form'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ed1d0e423a3cdf77a242ec3214720f1466f65897
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039506"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="efda6-102">Instrukcje: Tworzenie prostej kontrolki powiązanej na formularzu Windows Form</span><span class="sxs-lookup"><span data-stu-id="efda6-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>

<span data-ttu-id="efda6-103">Przy użyciu *prostego powiązania*można wyświetlić pojedynczy element danych, taki jak wartość kolumny z tabeli zestawu danych, w formancie.</span><span class="sxs-lookup"><span data-stu-id="efda6-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="efda6-104">Można utworzyć prostą dowolną właściwość formantu do wartości danych.</span><span class="sxs-lookup"><span data-stu-id="efda6-104">You can simple-bind any property of a control to a data value.</span></span>

### <a name="to-simple-bind-a-control"></a><span data-ttu-id="efda6-105">Aby powiązać formant z prostą</span><span class="sxs-lookup"><span data-stu-id="efda6-105">To simple-bind a control</span></span>

1. <span data-ttu-id="efda6-106">Nawiąż połączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="efda6-106">Connect to a data source.</span></span> <span data-ttu-id="efda6-107">Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia ze źródłem danych](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="efda6-107">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="efda6-108">W formularzu zaznacz kontrolkę i Wyświetl okno **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="efda6-108">In the form, select the control and display the **Properties** window.</span></span>

3. <span data-ttu-id="efda6-109">Rozwiń Właściwość **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="efda6-109">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="efda6-110">Właściwości najczęściej powiązane są wyświetlane pod właściwością **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="efda6-110">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="efda6-111">Na przykład w większości formantów właściwość **Text** jest najczęściej powiązana.</span><span class="sxs-lookup"><span data-stu-id="efda6-111">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="efda6-112">Jeśli właściwość, którą chcesz powiązać, nie jest jedną z często powiązanych właściwości, kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości ](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)programu Visual Studio) w polu **(Zaawansowane)** , aby wyświetlić  **Formatowanie i zaawansowane** okno dialogowe powiązania z pełną listą właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="efda6-112">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="efda6-113">Wybierz właściwość, którą chcesz powiązać, a następnie kliknij strzałkę listy rozwijanej w obszarze **powiązania**.</span><span class="sxs-lookup"><span data-stu-id="efda6-113">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="efda6-114">Zostanie wyświetlona lista dostępnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="efda6-114">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="efda6-115">Rozwiń źródło danych, do którego chcesz powiązać, dopóki nie znajdziesz jednego z nich.</span><span class="sxs-lookup"><span data-stu-id="efda6-115">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="efda6-116">Na przykład jeśli powiążesz się z wartością kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.</span><span class="sxs-lookup"><span data-stu-id="efda6-116">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="efda6-117">Kliknij nazwę elementu, z którym ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="efda6-117">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="efda6-118">Jeśli pracujesz w oknie dialogowym **Formatowanie i zaawansowane powiązanie** , kliknij przycisk **OK** , aby powrócić do okna **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="efda6-118">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="efda6-119">Jeśli chcesz powiązać dodatkowe właściwości kontrolki, powtórz kroki od 3 do 7.</span><span class="sxs-lookup"><span data-stu-id="efda6-119">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="efda6-120">Ponieważ kontrolki proste powiązane pokazują tylko jeden element danych, jest to bardzo typowy do uwzględnienia logiki nawigacji w formularzu systemu Windows z prostymi kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="efda6-120">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="efda6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efda6-121">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="efda6-122">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="efda6-122">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="efda6-123">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="efda6-123">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
