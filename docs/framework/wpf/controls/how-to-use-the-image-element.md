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
ms.openlocfilehash: 967159894e25721bdf380f851712e91d76088f87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696281"
---
# <a name="how-to-use-the-image-element"></a>Instrukcje: Używanie elementu obrazu
W tym przykładzie pokazano, jak dołączać obrazy do aplikacji przy użyciu <xref:System.Windows.Controls.Image> elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak by renderować obraz 200 pikseli szerokości. W tym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykład składni atrybutów i składnia znacznika właściwości, które są używane do definiowania obrazu. Aby uzyskać więcej informacji na temat składni atrybutów i składnia właściwości, zobacz [Przegląd właściwości zależności](../advanced/dependency-properties-overview.md). A <xref:System.Windows.Media.Imaging.BitmapImage> służy do definiowania danych źródłowych obrazu i jest jawnie zdefiniowany na przykład składni tagu właściwości. Ponadto <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> z <xref:System.Windows.Media.Imaging.BitmapImage> jest ustawiona na taką samą szerokość jako <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.Image>. Odbywa się, aby upewnić się, że minimalna ilość pamięci jest używany, renderowanie obrazu.  
  
> [!NOTE]
>  Ogólnie rzecz biorąc, jeśli chcesz określić rozmiar renderowanym obrazie, określ tylko <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A> , ale nie oba. Jeśli określono tylko jeden, jest zachowywany współczynnik proporcji obrazu. W przeciwnym razie obrazu nieoczekiwanie może występować w rozproszonym lub zawijać. Do kontrolowania obrazu użytkownika rozciąganie zachowanie, użyj <xref:System.Windows.Controls.Image.Stretch%2A> i <xref:System.Windows.Controls.Image.StretchDirection%2A> właściwości.  
  
> [!NOTE]
>  Po określeniu rozmiaru obrazu z oboma <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A>, należy także ustawić jedną <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> lub <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> do tego samego odpowiedniego rozmiaru.  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> Właściwość określa, jak źródło obrazu jest rozciągany tak, aby wypełnić elementu obrazu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Stretch> wyliczenia.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak renderować obraz 200 pikseli przy użyciu kodu.  
  
> [!NOTE]
>  Ustawienie <xref:System.Windows.Media.Imaging.BitmapImage> właściwości musi odbywać się w obrębie <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> i <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloku.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Zobacz także

- [Obrazowanie — przegląd](../graphics-multimedia/imaging-overview.md)
