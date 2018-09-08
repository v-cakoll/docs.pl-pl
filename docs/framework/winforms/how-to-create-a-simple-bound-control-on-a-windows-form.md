---
title: 'Porady: tworzenie prostego formantu powiązanego na formularzu systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 26bc136ea2b7e5bda4a57c5dad65ec3522efcd3d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138373"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="26f82-102">Porady: tworzenie prostego formantu powiązanego na formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="26f82-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>
<span data-ttu-id="26f82-103">Za pomocą *proste powiązanie*, można wyświetlić elementu danych jednego, takiego jak wartość kolumny z tabeli zestawu danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="26f82-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="26f82-104">Użytkownik może prosty wiązania dowolnej właściwości kontrolki z wartością danych.</span><span class="sxs-lookup"><span data-stu-id="26f82-104">You can simple-bind any property of a control to a data value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26f82-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="26f82-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="26f82-106">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="26f82-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="26f82-107">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="26f82-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-simple-bind-a-control"></a><span data-ttu-id="26f82-108">Do wiązania prostego formantu</span><span class="sxs-lookup"><span data-stu-id="26f82-108">To simple-bind a control</span></span>  
  
1.  <span data-ttu-id="26f82-109">Łączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="26f82-109">Connect to a data source.</span></span> <span data-ttu-id="26f82-110">Aby uzyskać więcej informacji, zobacz [nawiązania połączenia ze źródłem danych](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="26f82-110">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="26f82-111">W formularzu wybierz kontrolkę i wyświetlić **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="26f82-111">In the form, select the control and display the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="26f82-112">Rozwiń **(powiązania danych)** właściwości.</span><span class="sxs-lookup"><span data-stu-id="26f82-112">Expand the **(DataBindings)** property.</span></span>  
  
     <span data-ttu-id="26f82-113">Właściwości najczęściej powiązane są wyświetlane poniżej **(powiązania danych)** właściwości.</span><span class="sxs-lookup"><span data-stu-id="26f82-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="26f82-114">Na przykład w przypadku większości kontrolek **tekstu** właściwość najczęściej jest powiązana.</span><span class="sxs-lookup"><span data-stu-id="26f82-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>  
  
4.  <span data-ttu-id="26f82-115">Jeśli właściwość, którą chcesz powiązania nie jest jednym z powszechnie powiązanych właściwości, kliknij pozycję **wielokropka** przycisku (![VisualStudioEllipsesButton — zrzut ekranu](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) w **(zaawansowane)** pole, aby wyświetlić **formatowanie i powiązywanie zaawansowane** okno dialogowe z pełną listę właściwości dla tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="26f82-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>  
  
5.  <span data-ttu-id="26f82-116">Wybierz właściwość do powiązania, a następnie kliknij strzałkę listy rozwijanej w obszarze **powiązanie**.</span><span class="sxs-lookup"><span data-stu-id="26f82-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>  
  
     <span data-ttu-id="26f82-117">Zostanie wyświetlona lista dostępnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="26f82-117">A list of available data sources is displayed.</span></span>  
  
6.  <span data-ttu-id="26f82-118">Rozwiń źródło danych, które chcesz powiązać, dopóki nie znajdziesz element danych jednego, który ma.</span><span class="sxs-lookup"><span data-stu-id="26f82-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="26f82-119">Na przykład jeśli dokonywane jest wiązanie wartość kolumny w tabeli zestawu danych, rozwiń węzeł z nazwą zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.</span><span class="sxs-lookup"><span data-stu-id="26f82-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
7.  <span data-ttu-id="26f82-120">Kliknij nazwę elementu można powiązać.</span><span class="sxs-lookup"><span data-stu-id="26f82-120">Click the name of an element to bind to.</span></span>  
  
8.  <span data-ttu-id="26f82-121">Jeśli pracujesz **formatowanie i powiązywanie zaawansowane** okno dialogowe, kliknij przycisk **OK** aby powrócić do **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="26f82-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>  
  
9. <span data-ttu-id="26f82-122">Jeśli chcesz powiązać dodatkowe właściwości formantu, powtórz kroki od 3 do 7.</span><span class="sxs-lookup"><span data-stu-id="26f82-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26f82-123">Ponieważ formanty powiązane z prostego pokazać tylko danych jednego elementu, to bardzo typowy do uwzględnienia nawigacji logiki w formularzu Windows za pomocą formantów powiązanych z prostego.</span><span class="sxs-lookup"><span data-stu-id="26f82-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f82-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26f82-124">See Also</span></span>  
 <xref:System.Windows.Forms.Binding>  
 [<span data-ttu-id="26f82-125">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26f82-125">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="26f82-126">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26f82-126">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
