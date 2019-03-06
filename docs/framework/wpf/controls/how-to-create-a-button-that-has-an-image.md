---
title: 'Instrukcje: Utwórz przycisk, który posiada obraz'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: fe9f35a6f83c5a839823d94c4d3c55e01b192fb1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352038"
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="a8ecb-102">Instrukcje: Utwórz przycisk, który posiada obraz</span><span class="sxs-lookup"><span data-stu-id="a8ecb-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="a8ecb-103">W tym przykładzie pokazano jak dołączyć obraz na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8ecb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8ecb-104">Example</span></span>  
 <span data-ttu-id="a8ecb-105">Poniższy przykład tworzy dwie <xref:System.Windows.Controls.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="a8ecb-106">Jeden <xref:System.Windows.Controls.Button> zawiera tekst, a drugi zawiera obraz.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="a8ecb-107">Obraz, który znajduje się w folderze o nazwie danych, który jest podfolderem folderu projektu w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="a8ecb-108">Kiedy użytkownik kliknie <xref:System.Windows.Controls.Button> zawierającego obraz tła i tekstu z innych <xref:System.Windows.Controls.Button> zmiany.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="a8ecb-109">Ten przykład tworzy <xref:System.Windows.Controls.Button> steruje się za pomocą znaczników, ale używa kodu, aby zapisać <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a8ecb-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8ecb-110">See also</span></span>
- [<span data-ttu-id="a8ecb-111">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="a8ecb-111">Controls</span></span>](index.md)
- [<span data-ttu-id="a8ecb-112">Biblioteka kontrolek</span><span class="sxs-lookup"><span data-stu-id="a8ecb-112">Control Library</span></span>](control-library.md)
