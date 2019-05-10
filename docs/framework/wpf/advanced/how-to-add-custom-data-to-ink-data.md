---
title: 'Instrukcje: Dodawanie niestandardowych danych do danych pisma odręcznego'
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: 7c59a205df5358daec101339cc6a308c8e38a9d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640868"
---
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="df9d0-102">Instrukcje: Dodawanie niestandardowych danych do danych pisma odręcznego</span><span class="sxs-lookup"><span data-stu-id="df9d0-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="df9d0-103">Możesz dodać niestandardowe dane do pisma odręcznego, w którym zostanie zapisany w przypadku pisma odręcznego jest zapisywany w formacie pisma odręcznego serializacji (ISF).</span><span class="sxs-lookup"><span data-stu-id="df9d0-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="df9d0-104">Można zapisać niestandardowe dane do <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, lub <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="df9d0-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="df9d0-105">Możliwość zapisywania niestandardowych danych na trzy obiekty daje możliwość zdecydować, najlepszym miejscem, aby zapisać dane.</span><span class="sxs-lookup"><span data-stu-id="df9d0-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="df9d0-106">Wszystkie trzy klasy korzystając z podobnych metod do przechowywania i dostępu do danych niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="df9d0-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="df9d0-107">Tylko następujące typy mogą być zapisywane jako dane niestandardowe:</span><span class="sxs-lookup"><span data-stu-id="df9d0-107">Only the following types can be saved as custom data:</span></span>  
  
- <xref:System.Boolean>  
  
- <span data-ttu-id="df9d0-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-108"><xref:System.Boolean>[]</span></span>  
  
- <xref:System.Byte>  
  
- <span data-ttu-id="df9d0-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-109"><xref:System.Byte>[]</span></span>  
  
- <xref:System.Char>  
  
- <span data-ttu-id="df9d0-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-110"><xref:System.Char>[]</span></span>  
  
- <xref:System.DateTime>  
  
- <span data-ttu-id="df9d0-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-111"><xref:System.DateTime>[]</span></span>  
  
- <xref:System.Decimal>  
  
- <span data-ttu-id="df9d0-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-112"><xref:System.Decimal>[]</span></span>  
  
- <xref:System.Double>  
  
- <span data-ttu-id="df9d0-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-113"><xref:System.Double>[]</span></span>  
  
- <xref:System.Int16>  
  
- <span data-ttu-id="df9d0-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-114"><xref:System.Int16>[]</span></span>  
  
- <xref:System.Int32>  
  
- <span data-ttu-id="df9d0-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-115"><xref:System.Int32>[]</span></span>  
  
- <xref:System.Int64>  
  
- <span data-ttu-id="df9d0-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-116"><xref:System.Int64>[]</span></span>  
  
- <xref:System.Single>  
  
- <span data-ttu-id="df9d0-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-117"><xref:System.Single>[]</span></span>  
  
- <xref:System.String>  
  
- <xref:System.UInt16>  
  
- <span data-ttu-id="df9d0-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-118"><xref:System.UInt16>[]</span></span>  
  
- <xref:System.UInt32>  
  
- <span data-ttu-id="df9d0-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-119"><xref:System.UInt32>[]</span></span>  
  
- <xref:System.UInt64>  
  
- <span data-ttu-id="df9d0-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="df9d0-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="df9d0-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="df9d0-121">Example</span></span>  
 <span data-ttu-id="df9d0-122">Poniższy przykład pokazuje, jak dodawanie i pobieranie danych niestandardowych z <xref:System.Windows.Ink.StrokeCollection>.</span><span class="sxs-lookup"><span data-stu-id="df9d0-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="df9d0-123">Poniższy przykład tworzy aplikację, która wyświetla <xref:System.Windows.Controls.InkCanvas> oraz dwa przyciski.</span><span class="sxs-lookup"><span data-stu-id="df9d0-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="df9d0-124">Po kliknięciu przycisku `switchAuthor`, umożliwia dwóch pióra, który będzie używany przez dwóch różnych autorów.</span><span class="sxs-lookup"><span data-stu-id="df9d0-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="df9d0-125">Przycisk `changePenColors` zmienia kolor każdego obrysu na <xref:System.Windows.Controls.InkCanvas> według autora.</span><span class="sxs-lookup"><span data-stu-id="df9d0-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="df9d0-126">Aplikacja definiuje dwa <xref:System.Windows.Ink.DrawingAttributes> obiektów i dodaje właściwość niestandardową do każdego z nich, który wskazuje, które autor narysowane <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="df9d0-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="df9d0-127">Kiedy użytkownik kliknie `changePenColors`, aplikacja zmieni się wygląd obiektu stroke zgodnie z wartością właściwości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="df9d0-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
