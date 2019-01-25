---
title: 'Instrukcje: Utwórz przycisk, który posiada obraz'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: cfebe53047531ecddde42a3a0596dfd949629ecd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682079"
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="46d84-102">Instrukcje: Utwórz przycisk, który posiada obraz</span><span class="sxs-lookup"><span data-stu-id="46d84-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="46d84-103">W tym przykładzie pokazano jak dołączyć obraz na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="46d84-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46d84-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="46d84-104">Example</span></span>  
 <span data-ttu-id="46d84-105">Poniższy przykład tworzy dwie <xref:System.Windows.Controls.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="46d84-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="46d84-106">Jeden <xref:System.Windows.Controls.Button> zawiera tekst, a drugi zawiera obraz.</span><span class="sxs-lookup"><span data-stu-id="46d84-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="46d84-107">Obraz, który znajduje się w folderze o nazwie danych, który jest podfolderem folderu projektu w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="46d84-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="46d84-108">Kiedy użytkownik kliknie <xref:System.Windows.Controls.Button> zawierającego obraz tła i tekstu z innych <xref:System.Windows.Controls.Button> zmiany.</span><span class="sxs-lookup"><span data-stu-id="46d84-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="46d84-109">Ten przykład tworzy <xref:System.Windows.Controls.Button> steruje się za pomocą znaczników, ale używa kodu, aby zapisać <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="46d84-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="46d84-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46d84-110">See also</span></span>
- [<span data-ttu-id="46d84-111">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="46d84-111">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)
- [<span data-ttu-id="46d84-112">Biblioteka kontrolek</span><span class="sxs-lookup"><span data-stu-id="46d84-112">Control Library</span></span>](../../../../docs/framework/wpf/controls/control-library.md)
