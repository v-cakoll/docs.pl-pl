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
---
# <a name="how-to-add-custom-data-to-ink-data"></a>Jak dodać niestandardowe dane do danych atramentu
Niestandardowe dane można dodać do pismo odręczne, które zostaną zapisane podczas pismo odręczne jest zapisywany w formacie serializowany odręczne (ISF).  Można zapisać danych niestandardowych do <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, lub <xref:System.Windows.Ink.Stroke>.  Możliwość zapisania danych niestandardowych na trzy obiekty daje możliwość zdecydować, najlepszym miejscem, aby zapisać dane.  Wszystkie trzy klasy użyj metody podobne do przechowywania i udostępniania danych niestandardowych.  
  
 Tylko następujące typy mogą zostać zapisane jako danych niestandardowych:  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>[]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>[]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>[]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>[]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>[]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>[]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>[]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>[]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>[]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>[]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>[]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>[]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>[]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak dodać i pobrać dane niestandardowe z <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 Poniższy przykład tworzy aplikację, która wyświetla <xref:System.Windows.Controls.InkCanvas> i przyciskami.  Po kliknięciu przycisku `switchAuthor`, umożliwia dwóch pióra do użycia przez dwa różne autorów.  Przycisk `changePenColors` zmienia kolor każdego obrysu na <xref:System.Windows.Controls.InkCanvas> zgodnie z jego autorem.  Aplikacja definiuje dwie <xref:System.Windows.Ink.DrawingAttributes> obiekty i dodaje właściwość do każdej z nich, która wskazuje, które autor zwrócił <xref:System.Windows.Ink.Stroke>.  Po kliknięciu przez użytkownika `changePenColors`, aplikacji zmieni się wygląd obiektu stroke zgodnie z wartością właściwości niestandardowej.  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
