---
title: 'Instrukcje: tworzenie kontrolki formularzy systemu Windows pokazującego postęp'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 84f0caace70f9877e84fdd01dc69216dc10fe485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950577"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="288ed-102">Instrukcje: tworzenie kontrolki formularzy systemu Windows pokazującego postęp</span><span class="sxs-lookup"><span data-stu-id="288ed-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="288ed-103">Poniższy przykład kodu pokazuje kontrolkę niestandardową `FlashTrackBar` o nazwie, która może służyć do wyświetlania użytkownikowi poziomu lub postępu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="288ed-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="288ed-104">Używa gradientu do wizualnego reprezentowania postępu.</span><span class="sxs-lookup"><span data-stu-id="288ed-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="288ed-105">`FlashTrackBar` Kontrolka ilustruje następujące koncepcje:</span><span class="sxs-lookup"><span data-stu-id="288ed-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
- <span data-ttu-id="288ed-106">Definiowanie właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="288ed-106">Defining custom properties.</span></span>  
  
- <span data-ttu-id="288ed-107">Definiowanie zdarzeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="288ed-107">Defining custom events.</span></span> <span data-ttu-id="288ed-108">`FlashTrackBar` (`ValueChanged` definiuje zdarzenie).</span><span class="sxs-lookup"><span data-stu-id="288ed-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
- <span data-ttu-id="288ed-109">Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> metody w celu zapewnienia logiki do rysowania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="288ed-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
- <span data-ttu-id="288ed-110">Obliczanie obszaru dostępnego do rysowania kontrolki przy użyciu jej <xref:System.Windows.Forms.Control.ClientRectangle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="288ed-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="288ed-111">`FlashTrackBar`robi to w `OptimizedInvalidate` metodzie.</span><span class="sxs-lookup"><span data-stu-id="288ed-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
- <span data-ttu-id="288ed-112">Implementowanie serializacji lub trwałości dla właściwości w przypadku zmiany w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="288ed-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="288ed-113">`FlashTrackBar`definiuje metody i `ShouldSerializeEndColor` dla serializowania właściwości `EndColor` i.`StartColor` `ShouldSerializeStartColor`</span><span class="sxs-lookup"><span data-stu-id="288ed-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="288ed-114">W poniższej tabeli przedstawiono właściwości niestandardowe zdefiniowane przez `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="288ed-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="288ed-115">Właściwość</span><span class="sxs-lookup"><span data-stu-id="288ed-115">Property</span></span>|<span data-ttu-id="288ed-116">Opis</span><span class="sxs-lookup"><span data-stu-id="288ed-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="288ed-117">Wskazuje, czy użytkownik może zmienić wartość paska śledzenia Flash, klikając i przeciągając go.</span><span class="sxs-lookup"><span data-stu-id="288ed-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="288ed-118">Określa kolor końcowy paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="288ed-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="288ed-119">Określa, jak dużo przyciemnienie tła względem gradientu pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="288ed-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="288ed-120">Określa maksymalną wartość paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="288ed-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="288ed-121">Określa minimalną wartość paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="288ed-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="288ed-122">Określa początkowy kolor gradientu.</span><span class="sxs-lookup"><span data-stu-id="288ed-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="288ed-123">Wskazuje, czy w gradiencie ma być wyświetlana wartość procentowa.</span><span class="sxs-lookup"><span data-stu-id="288ed-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="288ed-124">Wskazuje, czy bieżąca wartość ma być wyświetlana nad gradientem.</span><span class="sxs-lookup"><span data-stu-id="288ed-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="288ed-125">Wskazuje, czy na pasku śledzenia powinien zostać wyświetlony gradient koloru przedstawiający bieżącą wartość.</span><span class="sxs-lookup"><span data-stu-id="288ed-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="288ed-126">Określa bieżącą wartość paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="288ed-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="288ed-127">W poniższej tabeli przedstawiono dodatkowe elementy członkowskie zdefiniowane `FlashTrackBar:` przez zdarzenie zmiany właściwości i metodę, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="288ed-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="288ed-128">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="288ed-128">Member</span></span>|<span data-ttu-id="288ed-129">Opis</span><span class="sxs-lookup"><span data-stu-id="288ed-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="288ed-130">Zdarzenie wywoływane, gdy `Value` zostanie zmieniona właściwość paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="288ed-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="288ed-131">Metoda, która wywołuje `ValueChanged` zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="288ed-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="288ed-132">`FlashTrackBar`używa klasy dla danych zdarzeń i <xref:System.EventHandler> dla delegata zdarzenia. <xref:System.EventArgs></span><span class="sxs-lookup"><span data-stu-id="288ed-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="288ed-133">Aby obsłużyć odpowiednie zdarzenia EventName `FlashTrackBar` , program zastępuje następujące metody, z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>których dziedziczy:</span><span class="sxs-lookup"><span data-stu-id="288ed-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="288ed-134">Aby obsłużyć odpowiednie zdarzenia zmiany właściwości, `FlashTrackBar` program zastępuje następujące metody, z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>których dziedziczy:</span><span class="sxs-lookup"><span data-stu-id="288ed-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="288ed-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="288ed-135">Example</span></span>  
 <span data-ttu-id="288ed-136">Kontrolka definiuje dwa `FlashTrackBarValueEditor` edytory typów interfejsu użytkownika `FlashTrackBarDarkenByEditor`i, które są wyświetlane w poniższych listach kodu. `FlashTrackBar`</span><span class="sxs-lookup"><span data-stu-id="288ed-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="288ed-137">`HostApp` Klasa`FlashTrackBar` używa kontrolki w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="288ed-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="288ed-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="288ed-138">See also</span></span>

- <span data-ttu-id="288ed-139">[Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="288ed-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="288ed-140">Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="288ed-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
