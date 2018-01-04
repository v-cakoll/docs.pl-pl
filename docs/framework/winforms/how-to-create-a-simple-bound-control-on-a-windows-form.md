---
title: "Porady: tworzenie prostego formantu powiązanego na formularzu systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c55480e02eac4cc4156fa119493f2fd2f57c07a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="29cd2-102">Porady: tworzenie prostego formantu powiązanego na formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="29cd2-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>
<span data-ttu-id="29cd2-103">Z *proste powiązanie*, element danych, np. wartość kolumny z tabeli zestawu danych, można wyświetlić w formancie.</span><span class="sxs-lookup"><span data-stu-id="29cd2-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="29cd2-104">Możesz można prosty — wiązanie żadnej właściwości formantu do wartości danych.</span><span class="sxs-lookup"><span data-stu-id="29cd2-104">You can simple-bind any property of a control to a data value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29cd2-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="29cd2-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="29cd2-106">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="29cd2-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="29cd2-107">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="29cd2-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-simple-bind-a-control"></a><span data-ttu-id="29cd2-108">Prosty polecenia BIND formant</span><span class="sxs-lookup"><span data-stu-id="29cd2-108">To simple-bind a control</span></span>  
  
1.  <span data-ttu-id="29cd2-109">Połączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="29cd2-109">Connect to a data source.</span></span> <span data-ttu-id="29cd2-110">Aby uzyskać więcej informacji, zobacz [połączenie ze źródłem danych](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="29cd2-110">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="29cd2-111">W formularzu, wybierz kontrolkę i wyświetlić **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="29cd2-111">In the form, select the control and display the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="29cd2-112">Rozwiń węzeł **(DataBindings)** właściwości.</span><span class="sxs-lookup"><span data-stu-id="29cd2-112">Expand the **(DataBindings)** property.</span></span>  
  
     <span data-ttu-id="29cd2-113">Właściwości często powiązane są wyświetlane poniżej **(DataBindings)** właściwości.</span><span class="sxs-lookup"><span data-stu-id="29cd2-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="29cd2-114">Na przykład w przypadku większości formantów **tekst** właściwości najczęściej jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="29cd2-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>  
  
4.  <span data-ttu-id="29cd2-115">Jeśli właściwość ma zostać powiązania nie jest jednym z często powiązane właściwości, kliknij pozycję **wielokropka** przycisk (![VisualStudioEllipsesButton — zrzut ekranu](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) w **(zaawansowane)** pole, aby wyświetlić **formatowanie i zaawansowane powiązanie** okno dialogowe z pełną listę właściwości dla tego formantu.</span><span class="sxs-lookup"><span data-stu-id="29cd2-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>  
  
5.  <span data-ttu-id="29cd2-116">Wybierz właściwość, aby powiązać i kliknij strzałkę listy rozwijanej w obszarze **powiązanie**.</span><span class="sxs-lookup"><span data-stu-id="29cd2-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>  
  
     <span data-ttu-id="29cd2-117">Zostanie wyświetlona lista dostępnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="29cd2-117">A list of available data sources is displayed.</span></span>  
  
6.  <span data-ttu-id="29cd2-118">Rozwiń źródło danych, które chcesz powiązać do momentu znalezienia element danych, który ma.</span><span class="sxs-lookup"><span data-stu-id="29cd2-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="29cd2-119">Na przykład są wiązane wartość kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.</span><span class="sxs-lookup"><span data-stu-id="29cd2-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
7.  <span data-ttu-id="29cd2-120">Kliknij nazwę elementu, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="29cd2-120">Click the name of an element to bind to.</span></span>  
  
8.  <span data-ttu-id="29cd2-121">Podczas pracy **formatowanie i zaawansowane powiązanie** okno dialogowe, kliknij przycisk **OK** aby powrócić do **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="29cd2-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>  
  
9. <span data-ttu-id="29cd2-122">Jeśli chcesz powiązać dodatkowe właściwości formantu, powtórz kroki od 3 do 7.</span><span class="sxs-lookup"><span data-stu-id="29cd2-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29cd2-123">Ponieważ formanty powiązane z prostą Pokaż tylko danych jednego elementu, jest bardzo typowy do uwzględnienia w formularzu systemu Windows z formantów powiązanych z prostą logiki nawigacji.</span><span class="sxs-lookup"><span data-stu-id="29cd2-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29cd2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29cd2-124">See Also</span></span>  
 <xref:System.Windows.Forms.Binding>  
 [<span data-ttu-id="29cd2-125">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29cd2-125">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="29cd2-126">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29cd2-126">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
