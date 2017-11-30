---
title: "Porady: tworzenie formantu formularzy systemu Windows pokazującego postęp"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55b3879b894658c9a649004348a198d004040af3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="43a66-102">Porady: tworzenie formantu formularzy systemu Windows pokazującego postęp</span><span class="sxs-lookup"><span data-stu-id="43a66-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="43a66-103">Poniższy przykład kodu pokazuje formant niestandardowy o nazwie `FlashTrackBar` można wyświetlane użytkownikowi, poziomu lub postęp aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43a66-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="43a66-104">Gradient używa do wizualnego reprezentowania postępu.</span><span class="sxs-lookup"><span data-stu-id="43a66-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="43a66-105">`FlashTrackBar` Kontroli przedstawiono następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="43a66-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
-   <span data-ttu-id="43a66-106">Definiowanie właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="43a66-106">Defining custom properties.</span></span>  
  
-   <span data-ttu-id="43a66-107">Definiowanie zdarzeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="43a66-107">Defining custom events.</span></span> <span data-ttu-id="43a66-108">(`FlashTrackBar` definiuje `ValueChanged` zdarzeń.)</span><span class="sxs-lookup"><span data-stu-id="43a66-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
-   <span data-ttu-id="43a66-109">Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> metodę w celu zapewnienia logiki, by narysować kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="43a66-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
-   <span data-ttu-id="43a66-110">Obliczanie dostępne do rysowania formantu przy użyciu obszaru jego <xref:System.Windows.Forms.Control.ClientRectangle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="43a66-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="43a66-111">`FlashTrackBar`Dzieje się tak jego `OptimizedInvalidate` metody.</span><span class="sxs-lookup"><span data-stu-id="43a66-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
-   <span data-ttu-id="43a66-112">Implementowanie serializacji lub trwałości dla właściwości, gdy zostanie zmieniona w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="43a66-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="43a66-113">`FlashTrackBar`definiuje `ShouldSerializeStartColor` i `ShouldSerializeEndColor` metody serializacji jego `StartColor` i `EndColor` właściwości.</span><span class="sxs-lookup"><span data-stu-id="43a66-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="43a66-114">W poniższej tabeli przedstawiono właściwości niestandardowe zdefiniowane przez `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="43a66-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="43a66-115">Właściwość</span><span class="sxs-lookup"><span data-stu-id="43a66-115">Property</span></span>|<span data-ttu-id="43a66-116">Opis</span><span class="sxs-lookup"><span data-stu-id="43a66-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="43a66-117">Wskazuje, czy użytkownik może zmienić wartość pasek śledzenia flash, klikając i przeciągając go.</span><span class="sxs-lookup"><span data-stu-id="43a66-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="43a66-118">Określa kolor końcowy pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="43a66-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="43a66-119">Określa stopień przyciemnianie tła względem gradientu pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="43a66-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="43a66-120">Określa maksymalną wartość pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="43a66-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="43a66-121">Określa minimalną wartość pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="43a66-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="43a66-122">Określa kolor początkowy gradientu.</span><span class="sxs-lookup"><span data-stu-id="43a66-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="43a66-123">Wskazuje, czy ma być wyświetlana wartość procentową nad gradientu.</span><span class="sxs-lookup"><span data-stu-id="43a66-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="43a66-124">Wskazuje, czy należy wyświetlić bieżącą wartość za pośrednictwem gradientu.</span><span class="sxs-lookup"><span data-stu-id="43a66-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="43a66-125">Wskazuje, czy pasek śledzenia powinien być wyświetlany kolor gradientu przedstawiający bieżącą wartość.</span><span class="sxs-lookup"><span data-stu-id="43a66-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="43a66-126">Określa bieżącą wartość pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="43a66-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="43a66-127">W poniższej tabeli przedstawiono dodatkowe elementów członkowskich zdefiniowanych przez `FlashTrackBar:` zdarzenie zmiany właściwości i metody, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="43a66-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="43a66-128">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="43a66-128">Member</span></span>|<span data-ttu-id="43a66-129">Opis</span><span class="sxs-lookup"><span data-stu-id="43a66-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="43a66-130">Zdarzenie wywoływane, gdy `Value` właściwości śledzenia pasek zmian.</span><span class="sxs-lookup"><span data-stu-id="43a66-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="43a66-131">Metoda, który wywołuje `ValueChanged` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="43a66-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="43a66-132">`FlashTrackBar`używa <xref:System.EventArgs> klasy na potrzeby danych zdarzenia i <xref:System.EventHandler> dla delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="43a66-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="43a66-133">Do obsługi odpowiednich *EventName* zdarzenia, `FlashTrackBar` zastępuje następujące metody, które dziedziczy z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="43a66-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="43a66-134">Do obsługi odpowiednie zdarzenia zmiany właściwości `FlashTrackBar` zastępuje następujące metody, które dziedziczy z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="43a66-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="43a66-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="43a66-135">Example</span></span>  
 <span data-ttu-id="43a66-136">`FlashTrackBar` Kontroli definiuje dwie edytory typ interfejsu użytkownika, `FlashTrackBarValueEditor` i `FlashTrackBarDarkenByEditor`, które przedstawiono w następujących fragmentów kodu.</span><span class="sxs-lookup"><span data-stu-id="43a66-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="43a66-137">`HostApp` Klasy używa `FlashTrackBar` kontrolkę w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="43a66-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="43a66-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43a66-138">See Also</span></span>  
 [<span data-ttu-id="43a66-139">Rozszerzenie obsługi w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="43a66-139">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [<span data-ttu-id="43a66-140">Podstawy programowania formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="43a66-140">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)
