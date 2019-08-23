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
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="7fef2-102">Instrukcje: Używanie elementu obrazu</span><span class="sxs-lookup"><span data-stu-id="7fef2-102">How to: Use the Image Element</span></span>
<span data-ttu-id="7fef2-103">Ten przykład pokazuje, <xref:System.Windows.Controls.Image> jak dołączać obrazy w aplikacji za pomocą elementu.</span><span class="sxs-lookup"><span data-stu-id="7fef2-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fef2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7fef2-104">Example</span></span>  
 <span data-ttu-id="7fef2-105">Poniższy przykład pokazuje, jak renderować obraz 200 pikseli szerokości.</span><span class="sxs-lookup"><span data-stu-id="7fef2-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="7fef2-106">W tym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie zarówno składnia atrybutu, jak i składnia tagów właściwości są używane do definiowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="7fef2-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="7fef2-107">Aby uzyskać więcej informacji na temat składni atrybutów i składni właściwości, zobacz [Omówienie właściwości zależności](../advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7fef2-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="7fef2-108">A <xref:System.Windows.Media.Imaging.BitmapImage> służy do definiowania danych źródłowych obrazu i jest jawnie zdefiniowany dla przykładu składni tagów właściwości.</span><span class="sxs-lookup"><span data-stu-id="7fef2-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="7fef2-109">Ponadto <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.Image>ma ustawioną taką samą szerokość jak w. <xref:System.Windows.Media.Imaging.BitmapImage></span><span class="sxs-lookup"><span data-stu-id="7fef2-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="7fef2-110">W tym celu należy się upewnić, że minimalna ilość pamięci jest używana do renderowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="7fef2-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fef2-111">Ogólnie rzecz biorąc, jeśli chcesz określić rozmiar renderowanego obrazu, określ tylko <xref:System.Windows.FrameworkElement.Width%2A> lub, <xref:System.Windows.FrameworkElement.Height%2A> ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="7fef2-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="7fef2-112">Jeśli określisz tylko jeden, współczynnik proporcji obrazu zostanie zachowany.</span><span class="sxs-lookup"><span data-stu-id="7fef2-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="7fef2-113">W przeciwnym razie obraz może zostać nieoczekiwanie wyświetlony lub wyciągnięty.</span><span class="sxs-lookup"><span data-stu-id="7fef2-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="7fef2-114">Aby kontrolować zachowanie rozciągania obrazu, użyj <xref:System.Windows.Controls.Image.Stretch%2A> właściwości i. <xref:System.Windows.Controls.Image.StretchDirection%2A></span><span class="sxs-lookup"><span data-stu-id="7fef2-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fef2-115"><xref:System.Windows.FrameworkElement.Width%2A> Po określeniu rozmiaru obrazu przy użyciu albo lub <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> należy również ustawić albo <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> na ten sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="7fef2-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="7fef2-116"><xref:System.Windows.Controls.Image.Stretch%2A> Właściwość określa, w jaki sposób źródło obrazu jest rozciągane w celu wypełnienia elementu obrazu.</span><span class="sxs-lookup"><span data-stu-id="7fef2-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="7fef2-117">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Stretch> Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="7fef2-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="7fef2-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="7fef2-118">Example</span></span>  
 <span data-ttu-id="7fef2-119">Poniższy przykład pokazuje, jak renderować obraz 200 pikseli szerokości przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="7fef2-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fef2-120">Ustawienia <xref:System.Windows.Media.Imaging.BitmapImage> właściwości muszą być wykonywane <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> w bloku i <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> .</span><span class="sxs-lookup"><span data-stu-id="7fef2-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="7fef2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fef2-121">See also</span></span>

- [<span data-ttu-id="7fef2-122">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="7fef2-122">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
