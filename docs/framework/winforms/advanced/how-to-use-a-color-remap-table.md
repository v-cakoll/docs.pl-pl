---
title: "Porady: używanie tabeli ponownego mapowania kolorów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e208aa9c98c1ca19baee83760cfd0f75972ecfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="699fe-102">Porady: używanie tabeli ponownego mapowania kolorów</span><span class="sxs-lookup"><span data-stu-id="699fe-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="699fe-103">Ponowne mapowanie jest proces konwersji kolorów obrazu zgodnie z tabeli ponownego mapowania kolorów.</span><span class="sxs-lookup"><span data-stu-id="699fe-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="699fe-104">Tabeli ponownego mapowania kolorów jest tablicą <xref:System.Drawing.Imaging.ColorMap> obiektów.</span><span class="sxs-lookup"><span data-stu-id="699fe-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="699fe-105">Każdy <xref:System.Drawing.Imaging.ColorMap> obiektu w tablicy ma <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> właściwości i <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="699fe-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="699fe-106">Gdy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rysuje jako obraz każdego piksela obrazu jest porównywany z tablicy kolorów stary.</span><span class="sxs-lookup"><span data-stu-id="699fe-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="699fe-107">Jeśli koloru piksela pasuje do starego kolorów, kolor jest zmieniany na odpowiednich nowy kolor.</span><span class="sxs-lookup"><span data-stu-id="699fe-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="699fe-108">Kolory są zmieniane tylko w przypadku renderowania — wartości kolorów samego obrazu (przechowywane w <xref:System.Drawing.Image> lub <xref:System.Drawing.Bitmap> obiektu) nie są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="699fe-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="699fe-109">Aby narysować ponownie zmapowany obrazu, zainicjowania tablicy <xref:System.Drawing.Imaging.ColorMap> obiektów.</span><span class="sxs-lookup"><span data-stu-id="699fe-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="699fe-110">Przekaż tej tablicy do <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiekt, a następnie przekazać <xref:System.Drawing.Imaging.ImageAttributes> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="699fe-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="699fe-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="699fe-111">Example</span></span>  
 <span data-ttu-id="699fe-112">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku RemapInput.bmp.</span><span class="sxs-lookup"><span data-stu-id="699fe-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="699fe-113">Kod tworzy składający się z pojedynczej tabeli ponownego mapowania kolorów <xref:System.Drawing.Imaging.ColorMap> obiektu.</span><span class="sxs-lookup"><span data-stu-id="699fe-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="699fe-114"><xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Właściwość `ColorRemap` obiekt jest czerwony i <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> właściwość jest niebieski.</span><span class="sxs-lookup"><span data-stu-id="699fe-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="699fe-115">Obraz jest rysowane raz bez ponownego mapowania, a drugi raz z ponownego mapowania.</span><span class="sxs-lookup"><span data-stu-id="699fe-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="699fe-116">Proces ponownego mapowania zmienia wszystkich red pikseli na niebieski.</span><span class="sxs-lookup"><span data-stu-id="699fe-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="699fe-117">Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i ponownie zmapowany obraz po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="699fe-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 <span data-ttu-id="699fe-118">![Ponowne mapowanie kolorów](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span><span class="sxs-lookup"><span data-stu-id="699fe-118">![Color ReMap](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="699fe-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="699fe-119">Compiling the Code</span></span>  
 <span data-ttu-id="699fe-120">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="699fe-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="699fe-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="699fe-121">See Also</span></span>  
 [<span data-ttu-id="699fe-122">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="699fe-122">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="699fe-123">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="699fe-123">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
