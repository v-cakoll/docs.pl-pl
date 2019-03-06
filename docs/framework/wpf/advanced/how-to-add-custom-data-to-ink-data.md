---
title: 'Instrukcje: Dodaj niestandardowe dane do danych atramentu'
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: c524e30943a21426e2e5e8fe6ae009999924fead
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361671"
---
# <a name="how-to-add-custom-data-to-ink-data"></a>Instrukcje: Dodaj niestandardowe dane do danych atramentu
Możesz dodać niestandardowe dane do pisma odręcznego, w którym zostanie zapisany w przypadku pisma odręcznego jest zapisywany w formacie pisma odręcznego serializacji (ISF).  Można zapisać niestandardowe dane do <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, lub <xref:System.Windows.Ink.Stroke>.  Możliwość zapisywania niestandardowych danych na trzy obiekty daje możliwość zdecydować, najlepszym miejscem, aby zapisać dane.  Wszystkie trzy klasy korzystając z podobnych metod do przechowywania i dostępu do danych niestandardowych.  
  
 Tylko następujące typy mogą być zapisywane jako dane niestandardowe:  
  
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
 Poniższy przykład pokazuje, jak dodawanie i pobieranie danych niestandardowych z <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 Poniższy przykład tworzy aplikację, która wyświetla <xref:System.Windows.Controls.InkCanvas> oraz dwa przyciski.  Po kliknięciu przycisku `switchAuthor`, umożliwia dwóch pióra, który będzie używany przez dwóch różnych autorów.  Przycisk `changePenColors` zmienia kolor każdego obrysu na <xref:System.Windows.Controls.InkCanvas> według autora.  Aplikacja definiuje dwa <xref:System.Windows.Ink.DrawingAttributes> obiektów i dodaje właściwość niestandardową do każdego z nich, który wskazuje, które autor narysowane <xref:System.Windows.Ink.Stroke>.  Kiedy użytkownik kliknie `changePenColors`, aplikacja zmieni się wygląd obiektu stroke zgodnie z wartością właściwości niestandardowej.  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
