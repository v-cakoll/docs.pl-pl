---
title: Jak dodać niestandardowe dane do danych atramentu
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: 40d883f3d3e1d504c8757c31325aa72a03da37e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544514"
---
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="46470-102">Jak dodać niestandardowe dane do danych atramentu</span><span class="sxs-lookup"><span data-stu-id="46470-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="46470-103">Niestandardowe dane można dodać do pismo odręczne, które zostaną zapisane podczas pismo odręczne jest zapisywany w formacie serializowany odręczne (ISF).</span><span class="sxs-lookup"><span data-stu-id="46470-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="46470-104">Można zapisać danych niestandardowych do <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, lub <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="46470-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="46470-105">Możliwość zapisania danych niestandardowych na trzy obiekty daje możliwość zdecydować, najlepszym miejscem, aby zapisać dane.</span><span class="sxs-lookup"><span data-stu-id="46470-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="46470-106">Wszystkie trzy klasy użyj metody podobne do przechowywania i udostępniania danych niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="46470-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="46470-107">Tylko następujące typy mogą zostać zapisane jako danych niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="46470-107">Only the following types can be saved as custom data:</span></span>  
  
-   <xref:System.Boolean>  
  
-   <span data-ttu-id="46470-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="46470-108"><xref:System.Boolean>[]</span></span>  
  
-   <xref:System.Byte>  
  
-   <span data-ttu-id="46470-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="46470-109"><xref:System.Byte>[]</span></span>  
  
-   <xref:System.Char>  
  
-   <span data-ttu-id="46470-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="46470-110"><xref:System.Char>[]</span></span>  
  
-   <xref:System.DateTime>  
  
-   <span data-ttu-id="46470-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="46470-111"><xref:System.DateTime>[]</span></span>  
  
-   <xref:System.Decimal>  
  
-   <span data-ttu-id="46470-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="46470-112"><xref:System.Decimal>[]</span></span>  
  
-   <xref:System.Double>  
  
-   <span data-ttu-id="46470-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="46470-113"><xref:System.Double>[]</span></span>  
  
-   <xref:System.Int16>  
  
-   <span data-ttu-id="46470-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="46470-114"><xref:System.Int16>[]</span></span>  
  
-   <xref:System.Int32>  
  
-   <span data-ttu-id="46470-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="46470-115"><xref:System.Int32>[]</span></span>  
  
-   <xref:System.Int64>  
  
-   <span data-ttu-id="46470-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="46470-116"><xref:System.Int64>[]</span></span>  
  
-   <xref:System.Single>  
  
-   <span data-ttu-id="46470-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="46470-117"><xref:System.Single>[]</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <span data-ttu-id="46470-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="46470-118"><xref:System.UInt16>[]</span></span>  
  
-   <xref:System.UInt32>  
  
-   <span data-ttu-id="46470-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="46470-119"><xref:System.UInt32>[]</span></span>  
  
-   <xref:System.UInt64>  
  
-   <span data-ttu-id="46470-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="46470-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="46470-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="46470-121">Example</span></span>  
 <span data-ttu-id="46470-122">W poniższym przykładzie pokazano, jak dodać i pobrać dane niestandardowe z <xref:System.Windows.Ink.StrokeCollection>.</span><span class="sxs-lookup"><span data-stu-id="46470-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="46470-123">Poniższy przykład tworzy aplikację, która wyświetla <xref:System.Windows.Controls.InkCanvas> i przyciskami.</span><span class="sxs-lookup"><span data-stu-id="46470-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="46470-124">Po kliknięciu przycisku `switchAuthor`, umożliwia dwóch pióra do użycia przez dwa różne autorów.</span><span class="sxs-lookup"><span data-stu-id="46470-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="46470-125">Przycisk `changePenColors` zmienia kolor każdego obrysu na <xref:System.Windows.Controls.InkCanvas> zgodnie z jego autorem.</span><span class="sxs-lookup"><span data-stu-id="46470-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="46470-126">Aplikacja definiuje dwie <xref:System.Windows.Ink.DrawingAttributes> obiekty i dodaje właściwość do każdej z nich, która wskazuje, które autor zwrócił <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="46470-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="46470-127">Po kliknięciu przez użytkownika `changePenColors`, aplikacji zmieni się wygląd obiektu stroke zgodnie z wartością właściwości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="46470-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
