---
title: 'Instrukcje: Utwórz formant programu Windows Forms pokazującej postęp'
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
ms.openlocfilehash: 6910a7e2e68a3807e08a8b196dde003e1d5bc9af
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720252"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="9e946-102">Instrukcje: Utwórz formant programu Windows Forms pokazującej postęp</span><span class="sxs-lookup"><span data-stu-id="9e946-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="9e946-103">Poniższy przykład kodu pokazuje kontrolkę niestandardową o nazwie `FlashTrackBar` można pokazać użytkownikowi, poziomu lub postęp aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e946-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="9e946-104">Aby wizualnie przedstawić postęp używa gradientu.</span><span class="sxs-lookup"><span data-stu-id="9e946-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="9e946-105">`FlashTrackBar` Kontroli ilustruje następujące pojęcia:</span><span class="sxs-lookup"><span data-stu-id="9e946-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
-   <span data-ttu-id="9e946-106">Definiowanie właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="9e946-106">Defining custom properties.</span></span>  
  
-   <span data-ttu-id="9e946-107">Definiowanie zdarzeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="9e946-107">Defining custom events.</span></span> <span data-ttu-id="9e946-108">(`FlashTrackBar` definiuje `ValueChanged` zdarzenia.)</span><span class="sxs-lookup"><span data-stu-id="9e946-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
-   <span data-ttu-id="9e946-109">Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, aby zapewnić logikę narysuj kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="9e946-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
-   <span data-ttu-id="9e946-110">Obliczenia obszar rysowania kontrolki przy użyciu jego <xref:System.Windows.Forms.Control.ClientRectangle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9e946-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="9e946-111">`FlashTrackBar` robi to jej `OptimizedInvalidate` metody.</span><span class="sxs-lookup"><span data-stu-id="9e946-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
-   <span data-ttu-id="9e946-112">Implementowanie serializacji lub stanów trwałych dla właściwości, gdy zostanie zmieniona w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="9e946-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="9e946-113">`FlashTrackBar` definiuje `ShouldSerializeStartColor` i `ShouldSerializeEndColor` metody serializacji jego `StartColor` i `EndColor` właściwości.</span><span class="sxs-lookup"><span data-stu-id="9e946-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="9e946-114">W poniższej tabeli przedstawiono właściwości niestandardowe zdefiniowane przez `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="9e946-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="9e946-115">Właściwość</span><span class="sxs-lookup"><span data-stu-id="9e946-115">Property</span></span>|<span data-ttu-id="9e946-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9e946-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="9e946-117">Wskazuje, czy użytkownik może zmienić wartość pasek śledzenia flash, klikając i przeciągając je.</span><span class="sxs-lookup"><span data-stu-id="9e946-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="9e946-118">Określa końcowy kolor pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9e946-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="9e946-119">Określa stopień ciemniejszy tła względem gradientu pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="9e946-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="9e946-120">Określa maksymalną wartość pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9e946-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="9e946-121">Określa minimalną wartość pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9e946-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="9e946-122">Określa kolor początkowy gradientu.</span><span class="sxs-lookup"><span data-stu-id="9e946-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="9e946-123">Wskazuje, czy ma być wyświetlane wartości procentowej nad gradientu.</span><span class="sxs-lookup"><span data-stu-id="9e946-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="9e946-124">Wskazuje, czy do wyświetlenia bieżącej wartości ciągu gradientu.</span><span class="sxs-lookup"><span data-stu-id="9e946-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="9e946-125">Wskazuje, czy pasek śledzenia powinien być wyświetlany kolor gradientu przedstawiający bieżącą wartość.</span><span class="sxs-lookup"><span data-stu-id="9e946-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="9e946-126">Określa bieżącą wartość pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9e946-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="9e946-127">W poniższej tabeli przedstawiono dodatkowe elementy członkowskie zdefiniowane przez `FlashTrackBar:` zdarzenie zmiany właściwości i metody, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="9e946-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="9e946-128">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9e946-128">Member</span></span>|<span data-ttu-id="9e946-129">Opis</span><span class="sxs-lookup"><span data-stu-id="9e946-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="9e946-130">Zdarzenie, które jest wywołane, gdy `Value` właściwości śledzenia zmian paska.</span><span class="sxs-lookup"><span data-stu-id="9e946-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="9e946-131">Metoda, która wywołuje `ValueChanged` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9e946-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9e946-132">`FlashTrackBar` używa <xref:System.EventArgs> klasę danych zdarzenia i <xref:System.EventHandler> dla delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9e946-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="9e946-133">Do obsługi odpowiednich *EventName* zdarzenia, `FlashTrackBar` zastępuje następujących metod, która dziedziczy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="9e946-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="9e946-134">Do obsługi odpowiedniej zdarzenia zmiany właściwości `FlashTrackBar` zastępuje następujących metod, która dziedziczy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="9e946-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="9e946-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e946-135">Example</span></span>  
 <span data-ttu-id="9e946-136">`FlashTrackBar` Kontroli definiuje dwa edytory typu UI `FlashTrackBarValueEditor` i `FlashTrackBarDarkenByEditor`, które są wyświetlane w następujących fragmentów kodu.</span><span class="sxs-lookup"><span data-stu-id="9e946-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="9e946-137">`HostApp` Klasy używa `FlashTrackBar` kontrolkę w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="9e946-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="9e946-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e946-138">See also</span></span>
- <span data-ttu-id="9e946-139">[Rozszerzenie obsługi w czasie projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9e946-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="9e946-140">Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e946-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
