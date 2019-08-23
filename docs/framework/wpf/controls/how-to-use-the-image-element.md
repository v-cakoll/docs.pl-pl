---
title: 'Instrukcje: Używanie elementu obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
ms.openlocfilehash: 164eee7c10d9e388c6e6ee695af479ca2d6974b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958326"
---
# <a name="how-to-use-the-image-element"></a>Instrukcje: Używanie elementu obrazu
Ten przykład pokazuje, <xref:System.Windows.Controls.Image> jak dołączać obrazy w aplikacji za pomocą elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak renderować obraz 200 pikseli szerokości. W tym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie zarówno składnia atrybutu, jak i składnia tagów właściwości są używane do definiowania obrazu. Aby uzyskać więcej informacji na temat składni atrybutów i składni właściwości, zobacz [Omówienie właściwości zależności](../advanced/dependency-properties-overview.md). A <xref:System.Windows.Media.Imaging.BitmapImage> służy do definiowania danych źródłowych obrazu i jest jawnie zdefiniowany dla przykładu składni tagów właściwości. Ponadto <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.Image>ma ustawioną taką samą szerokość jak w. <xref:System.Windows.Media.Imaging.BitmapImage> W tym celu należy się upewnić, że minimalna ilość pamięci jest używana do renderowania obrazu.  
  
> [!NOTE]
> Ogólnie rzecz biorąc, jeśli chcesz określić rozmiar renderowanego obrazu, określ tylko <xref:System.Windows.FrameworkElement.Width%2A> lub, <xref:System.Windows.FrameworkElement.Height%2A> ale nie oba. Jeśli określisz tylko jeden, współczynnik proporcji obrazu zostanie zachowany. W przeciwnym razie obraz może zostać nieoczekiwanie wyświetlony lub wyciągnięty. Aby kontrolować zachowanie rozciągania obrazu, użyj <xref:System.Windows.Controls.Image.Stretch%2A> właściwości i. <xref:System.Windows.Controls.Image.StretchDirection%2A>  
  
> [!NOTE]
> <xref:System.Windows.FrameworkElement.Width%2A> Po określeniu rozmiaru obrazu przy użyciu albo lub <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> należy również ustawić albo <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> na ten sam rozmiar.  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> Właściwość określa, w jaki sposób źródło obrazu jest rozciągane w celu wypełnienia elementu obrazu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Stretch> Wyliczenie.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak renderować obraz 200 pikseli szerokości przy użyciu kodu.  
  
> [!NOTE]
> Ustawienia <xref:System.Windows.Media.Imaging.BitmapImage> właściwości muszą być wykonywane <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> w bloku i <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> .  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Zobacz także

- [Obrazowanie — przegląd](../graphics-multimedia/imaging-overview.md)
