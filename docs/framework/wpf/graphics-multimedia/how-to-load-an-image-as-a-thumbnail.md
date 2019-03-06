---
title: 'Instrukcje: Załaduj obraz jako miniaturę'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: 0b5435e9b06f37dae7dc762e9035b1eca8156ca6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353391"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="7bc3e-102">Instrukcje: Załaduj obraz jako miniaturę</span><span class="sxs-lookup"><span data-stu-id="7bc3e-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="7bc3e-103">W poniższych przykładach pokazano sposób ładowania <xref:System.Windows.Controls.Image> jako miniatury w celu zachowywania pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bc3e-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bc3e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7bc3e-104">Example</span></span>  
 <span data-ttu-id="7bc3e-105">Poniższy przykład ustawia <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> właściwość <xref:System.Windows.Media.Imaging.BitmapImage> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] zmniejszyć ilość pamięci wymaganej do załadowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="7bc3e-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="7bc3e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7bc3e-106">Example</span></span>  
 <span data-ttu-id="7bc3e-107">Poniższy przykład ustawia <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> właściwość <xref:System.Windows.Media.Imaging.BitmapImage> w kodzie, aby zmniejszyć ilość pamięci wymaganej do załadowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="7bc3e-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="7bc3e-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bc3e-108">See also</span></span>
- [<span data-ttu-id="7bc3e-109">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="7bc3e-109">Imaging Overview</span></span>](imaging-overview.md)
