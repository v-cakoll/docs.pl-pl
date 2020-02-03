---
title: Tworzenie kontrolki pokazującej postęp
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
ms.openlocfilehash: 9d2cf353ba2309380221bb51733baaca1b81a5d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731175"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="bb71e-102">Porady: tworzenie formantu formularzy systemu Windows pokazującego postęp</span><span class="sxs-lookup"><span data-stu-id="bb71e-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="bb71e-103">Poniższy przykład kodu pokazuje kontrolkę niestandardową o nazwie `FlashTrackBar`, która może służyć do wyświetlania użytkownikowi poziomu lub postępu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb71e-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="bb71e-104">Używa gradientu do wizualnego reprezentowania postępu.</span><span class="sxs-lookup"><span data-stu-id="bb71e-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="bb71e-105">Formant `FlashTrackBar` ilustruje następujące koncepcje:</span><span class="sxs-lookup"><span data-stu-id="bb71e-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
- <span data-ttu-id="bb71e-106">Definiowanie właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bb71e-106">Defining custom properties.</span></span>  
  
- <span data-ttu-id="bb71e-107">Definiowanie zdarzeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bb71e-107">Defining custom events.</span></span> <span data-ttu-id="bb71e-108">(`FlashTrackBar` definiuje zdarzenie `ValueChanged`).</span><span class="sxs-lookup"><span data-stu-id="bb71e-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
- <span data-ttu-id="bb71e-109">Zastępowanie metody <xref:System.Windows.Forms.Control.OnPaint%2A> w celu zapewnienia logiki do rysowania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="bb71e-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
- <span data-ttu-id="bb71e-110">Obliczanie obszaru dostępnego do rysowania formantu przy użyciu jego właściwości <xref:System.Windows.Forms.Control.ClientRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb71e-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="bb71e-111">`FlashTrackBar` robi to w `OptimizedInvalidate` metodzie.</span><span class="sxs-lookup"><span data-stu-id="bb71e-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
- <span data-ttu-id="bb71e-112">Implementowanie serializacji lub trwałości dla właściwości w przypadku zmiany w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb71e-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="bb71e-113">`FlashTrackBar` definiuje metody `ShouldSerializeStartColor` i `ShouldSerializeEndColor` do serializacji `StartColor` i `EndColor` właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb71e-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="bb71e-114">W poniższej tabeli przedstawiono właściwości niestandardowe zdefiniowane przez `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="bb71e-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="bb71e-115">Właściwość</span><span class="sxs-lookup"><span data-stu-id="bb71e-115">Property</span></span>|<span data-ttu-id="bb71e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="bb71e-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="bb71e-117">Wskazuje, czy użytkownik może zmienić wartość paska śledzenia Flash, klikając i przeciągając go.</span><span class="sxs-lookup"><span data-stu-id="bb71e-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="bb71e-118">Określa kolor końcowy paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bb71e-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="bb71e-119">Określa, jak dużo przyciemnienie tła względem gradientu pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="bb71e-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="bb71e-120">Określa maksymalną wartość paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bb71e-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="bb71e-121">Określa minimalną wartość paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bb71e-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="bb71e-122">Określa początkowy kolor gradientu.</span><span class="sxs-lookup"><span data-stu-id="bb71e-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="bb71e-123">Wskazuje, czy w gradiencie ma być wyświetlana wartość procentowa.</span><span class="sxs-lookup"><span data-stu-id="bb71e-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="bb71e-124">Wskazuje, czy bieżąca wartość ma być wyświetlana nad gradientem.</span><span class="sxs-lookup"><span data-stu-id="bb71e-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="bb71e-125">Wskazuje, czy na pasku śledzenia powinien zostać wyświetlony gradient koloru przedstawiający bieżącą wartość.</span><span class="sxs-lookup"><span data-stu-id="bb71e-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="bb71e-126">Określa bieżącą wartość paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bb71e-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="bb71e-127">W poniższej tabeli przedstawiono dodatkowe elementy członkowskie zdefiniowane przez `FlashTrackBar:` zdarzenia zmiany właściwości i metody, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="bb71e-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="bb71e-128">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bb71e-128">Member</span></span>|<span data-ttu-id="bb71e-129">Opis</span><span class="sxs-lookup"><span data-stu-id="bb71e-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="bb71e-130">Zdarzenie wywoływane, gdy zostanie zmieniona właściwość `Value` paska śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bb71e-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="bb71e-131">Metoda, która wywołuje zdarzenie `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="bb71e-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="bb71e-132">`FlashTrackBar` używa klasy <xref:System.EventArgs> dla danych zdarzenia i <xref:System.EventHandler> dla delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bb71e-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="bb71e-133">Aby obsłużyć odpowiednie zdarzenia *EventName* , `FlashTrackBar` zastępuje następujące metody, które dziedziczy od <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="bb71e-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="bb71e-134">Aby obsłużyć odpowiednie zdarzenia zmiany właściwości, `FlashTrackBar` zastępuje następujące metody, które dziedziczy po <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="bb71e-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="bb71e-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb71e-135">Example</span></span>  
 <span data-ttu-id="bb71e-136">Formant `FlashTrackBar` definiuje dwa edytory typów interfejsu użytkownika, `FlashTrackBarValueEditor` i `FlashTrackBarDarkenByEditor`, które są wyświetlane na poniższej liście.</span><span class="sxs-lookup"><span data-stu-id="bb71e-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="bb71e-137">Klasa `HostApp` używa kontrolki `FlashTrackBar` w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb71e-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="bb71e-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb71e-138">See also</span></span>

- <span data-ttu-id="bb71e-139">[Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="bb71e-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="bb71e-140">Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb71e-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
