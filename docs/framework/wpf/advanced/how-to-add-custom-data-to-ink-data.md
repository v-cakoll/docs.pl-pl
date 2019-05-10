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
# <a name="how-to-add-custom-data-to-ink-data"></a>Instrukcje: Dodawanie niestandardowych danych do danych pisma odręcznego
Możesz dodać niestandardowe dane do pisma odręcznego, w którym zostanie zapisany w przypadku pisma odręcznego jest zapisywany w formacie pisma odręcznego serializacji (ISF).  Można zapisać niestandardowe dane do <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, lub <xref:System.Windows.Ink.Stroke>.  Możliwość zapisywania niestandardowych danych na trzy obiekty daje możliwość zdecydować, najlepszym miejscem, aby zapisać dane.  Wszystkie trzy klasy korzystając z podobnych metod do przechowywania i dostępu do danych niestandardowych.  
  
 Tylko następujące typy mogą być zapisywane jako dane niestandardowe:  
  
- <xref:System.Boolean>  
  
- <xref:System.Boolean>[]  
  
- <xref:System.Byte>  
  
- <xref:System.Byte>[]  
  
- <xref:System.Char>  
  
- <xref:System.Char>[]  
  
- <xref:System.DateTime>  
  
- <xref:System.DateTime>[]  
  
- <xref:System.Decimal>  
  
- <xref:System.Decimal>[]  
  
- <xref:System.Double>  
  
- <xref:System.Double>[]  
  
- <xref:System.Int16>  
  
- <xref:System.Int16>[]  
  
- <xref:System.Int32>  
  
- <xref:System.Int32>[]  
  
- <xref:System.Int64>  
  
- <xref:System.Int64>[]  
  
- <xref:System.Single>  
  
- <xref:System.Single>[]  
  
- <xref:System.String>  
  
- <xref:System.UInt16>  
  
- <xref:System.UInt16>[]  
  
- <xref:System.UInt32>  
  
- <xref:System.UInt32>[]  
  
- <xref:System.UInt64>  
  
- <xref:System.UInt64>[]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodawanie i pobieranie danych niestandardowych z <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 Poniższy przykład tworzy aplikację, która wyświetla <xref:System.Windows.Controls.InkCanvas> oraz dwa przyciski.  Po kliknięciu przycisku `switchAuthor`, umożliwia dwóch pióra, który będzie używany przez dwóch różnych autorów.  Przycisk `changePenColors` zmienia kolor każdego obrysu na <xref:System.Windows.Controls.InkCanvas> według autora.  Aplikacja definiuje dwa <xref:System.Windows.Ink.DrawingAttributes> obiektów i dodaje właściwość niestandardową do każdego z nich, który wskazuje, które autor narysowane <xref:System.Windows.Ink.Stroke>.  Kiedy użytkownik kliknie `changePenColors`, aplikacja zmieni się wygląd obiektu stroke zgodnie z wartością właściwości niestandardowej.  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
