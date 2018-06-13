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
ms.locfileid: "33555915"
---
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="1102b-102">Jak użyć elementu obrazu</span><span class="sxs-lookup"><span data-stu-id="1102b-102">How to: Use the Image Element</span></span>
<span data-ttu-id="1102b-103">W tym przykładzie pokazano, jak dołączać obrazy do aplikacji przy użyciu <xref:System.Windows.Controls.Image> elementu.</span><span class="sxs-lookup"><span data-stu-id="1102b-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1102b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1102b-104">Example</span></span>  
 <span data-ttu-id="1102b-105">Poniższy przykład przedstawia sposób renderowania obrazu 200 pikseli szerokości.</span><span class="sxs-lookup"><span data-stu-id="1102b-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="1102b-106">W tym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykład zarówno Składnia atrybutu i składni tagów właściwości, które są używane do definiowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="1102b-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="1102b-107">Aby uzyskać więcej informacji o składni atrybutu i składni właściwości, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1102b-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="1102b-108">A <xref:System.Windows.Media.Imaging.BitmapImage> służy do definiowania obrazu źródła danych i jest jawnie zdefiniowany na przykład składni tagu właściwości.</span><span class="sxs-lookup"><span data-stu-id="1102b-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="1102b-109">Ponadto <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> z <xref:System.Windows.Media.Imaging.BitmapImage> ma ustawioną wartość równą szerokości <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.Image>.</span><span class="sxs-lookup"><span data-stu-id="1102b-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="1102b-110">Można to zrobić, aby upewnić się, że minimalna ilość pamięci jest używana renderowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="1102b-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1102b-111">Ogólnie rzecz biorąc, jeśli chcesz określić rozmiar renderowanym obrazie, określ tylko <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A> , ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="1102b-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="1102b-112">Jeśli określono tylko jedną, współczynnik proporcji obrazu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="1102b-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="1102b-113">W przeciwnym razie obrazu nieoczekiwanie mogą występować rozciągnięty lub zawijać.</span><span class="sxs-lookup"><span data-stu-id="1102b-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="1102b-114">Do sterowania obrazu na rozciąganie zachowanie, użyj <xref:System.Windows.Controls.Image.Stretch%2A> i <xref:System.Windows.Controls.Image.StretchDirection%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1102b-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1102b-115">Po określeniu rozmiar obrazu przy użyciu jednej <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A>, należy także ustawić jedną <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> lub <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> do odpowiedniego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="1102b-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="1102b-116"><xref:System.Windows.Controls.Image.Stretch%2A> Właściwość określa, jak źródło obrazu jest rozciągany tak, aby wypełnić elementu obrazu.</span><span class="sxs-lookup"><span data-stu-id="1102b-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="1102b-117">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Stretch> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1102b-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="1102b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="1102b-118">Example</span></span>  
 <span data-ttu-id="1102b-119">Poniższy przykład przedstawia sposób renderowania obrazu 200 pikseli szerokości, przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="1102b-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1102b-120">Ustawienie <xref:System.Windows.Media.Imaging.BitmapImage> właściwości, które należy wykonać w ramach <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> i <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloku.</span><span class="sxs-lookup"><span data-stu-id="1102b-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="1102b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1102b-121">See Also</span></span>  
 [<span data-ttu-id="1102b-122">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="1102b-122">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
