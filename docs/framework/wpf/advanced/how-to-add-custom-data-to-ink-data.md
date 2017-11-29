---
title: "Jak dodać niestandardowe dane do danych atramentu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f266f3c98ca64c80ccbb669a1cc646321754579f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="babd9-102">Jak dodać niestandardowe dane do danych atramentu</span><span class="sxs-lookup"><span data-stu-id="babd9-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="babd9-103">Niestandardowe dane można dodać do pismo odręczne, które zostaną zapisane podczas pismo odręczne jest zapisywany w formacie serializowany odręczne (ISF).</span><span class="sxs-lookup"><span data-stu-id="babd9-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="babd9-104">Można zapisać danych niestandardowych do <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, lub <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="babd9-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="babd9-105">Możliwość zapisania danych niestandardowych na trzy obiekty daje możliwość zdecydować, najlepszym miejscem, aby zapisać dane.</span><span class="sxs-lookup"><span data-stu-id="babd9-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="babd9-106">Wszystkie trzy klasy użyj metody podobne do przechowywania i udostępniania danych niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="babd9-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="babd9-107">Tylko następujące typy mogą zostać zapisane jako danych niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="babd9-107">Only the following types can be saved as custom data:</span></span>  
  
-   <xref:System.Boolean>  
  
-   <span data-ttu-id="babd9-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-108"><xref:System.Boolean>[]</span></span>  
  
-   <xref:System.Byte>  
  
-   <span data-ttu-id="babd9-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-109"><xref:System.Byte>[]</span></span>  
  
-   <xref:System.Char>  
  
-   <span data-ttu-id="babd9-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-110"><xref:System.Char>[]</span></span>  
  
-   <xref:System.DateTime>  
  
-   <span data-ttu-id="babd9-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-111"><xref:System.DateTime>[]</span></span>  
  
-   <xref:System.Decimal>  
  
-   <span data-ttu-id="babd9-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-112"><xref:System.Decimal>[]</span></span>  
  
-   <xref:System.Double>  
  
-   <span data-ttu-id="babd9-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-113"><xref:System.Double>[]</span></span>  
  
-   <xref:System.Int16>  
  
-   <span data-ttu-id="babd9-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-114"><xref:System.Int16>[]</span></span>  
  
-   <xref:System.Int32>  
  
-   <span data-ttu-id="babd9-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-115"><xref:System.Int32>[]</span></span>  
  
-   <xref:System.Int64>  
  
-   <span data-ttu-id="babd9-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-116"><xref:System.Int64>[]</span></span>  
  
-   <xref:System.Single>  
  
-   <span data-ttu-id="babd9-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-117"><xref:System.Single>[]</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <span data-ttu-id="babd9-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-118"><xref:System.UInt16>[]</span></span>  
  
-   <xref:System.UInt32>  
  
-   <span data-ttu-id="babd9-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-119"><xref:System.UInt32>[]</span></span>  
  
-   <xref:System.UInt64>  
  
-   <span data-ttu-id="babd9-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="babd9-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="babd9-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="babd9-121">Example</span></span>  
 <span data-ttu-id="babd9-122">W poniższym przykładzie pokazano, jak dodać i pobrać dane niestandardowe z <xref:System.Windows.Ink.StrokeCollection>.</span><span class="sxs-lookup"><span data-stu-id="babd9-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="babd9-123">Poniższy przykład tworzy aplikację, która wyświetla <xref:System.Windows.Controls.InkCanvas> i przyciskami.</span><span class="sxs-lookup"><span data-stu-id="babd9-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="babd9-124">Po kliknięciu przycisku `switchAuthor`, umożliwia dwóch pióra do użycia przez dwa różne autorów.</span><span class="sxs-lookup"><span data-stu-id="babd9-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="babd9-125">Przycisk `changePenColors` zmienia kolor każdego obrysu na <xref:System.Windows.Controls.InkCanvas> zgodnie z jego autorem.</span><span class="sxs-lookup"><span data-stu-id="babd9-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="babd9-126">Aplikacja definiuje dwie <xref:System.Windows.Ink.DrawingAttributes> obiekty i dodaje właściwość do każdej z nich, która wskazuje, które autor zwrócił <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="babd9-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="babd9-127">Po kliknięciu przez użytkownika `changePenColors`, aplikacji zmieni się wygląd obiektu stroke zgodnie z wartością właściwości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="babd9-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
