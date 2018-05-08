---
title: Jak użyć elementu obrazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
ms.openlocfilehash: 11481533af7b3ad75b571f9f97251c123e0af1b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-image-element"></a>Jak użyć elementu obrazu
W tym przykładzie pokazano, jak dołączać obrazy do aplikacji przy użyciu <xref:System.Windows.Controls.Image> elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób renderowania obrazu 200 pikseli szerokości. W tym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykład zarówno Składnia atrybutu i składni tagów właściwości, które są używane do definiowania obrazu. Aby uzyskać więcej informacji o składni atrybutu i składni właściwości, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). A <xref:System.Windows.Media.Imaging.BitmapImage> służy do definiowania obrazu źródła danych i jest jawnie zdefiniowany na przykład składni tagu właściwości. Ponadto <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> z <xref:System.Windows.Media.Imaging.BitmapImage> ma ustawioną wartość równą szerokości <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.Image>. Można to zrobić, aby upewnić się, że minimalna ilość pamięci jest używana renderowania obrazu.  
  
> [!NOTE]
>  Ogólnie rzecz biorąc, jeśli chcesz określić rozmiar renderowanym obrazie, określ tylko <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A> , ale nie oba. Jeśli określono tylko jedną, współczynnik proporcji obrazu są zachowywane. W przeciwnym razie obrazu nieoczekiwanie mogą występować rozciągnięty lub zawijać. Do sterowania obrazu na rozciąganie zachowanie, użyj <xref:System.Windows.Controls.Image.Stretch%2A> i <xref:System.Windows.Controls.Image.StretchDirection%2A> właściwości.  
  
> [!NOTE]
>  Po określeniu rozmiar obrazu przy użyciu jednej <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A>, należy także ustawić jedną <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> lub <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> do odpowiedniego rozmiaru.  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> Właściwość określa, jak źródło obrazu jest rozciągany tak, aby wypełnić elementu obrazu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Stretch> wyliczenia.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób renderowania obrazu 200 pikseli szerokości, przy użyciu kodu.  
  
> [!NOTE]
>  Ustawienie <xref:System.Windows.Media.Imaging.BitmapImage> właściwości, które należy wykonać w ramach <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> i <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloku.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazowanie — przegląd](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
