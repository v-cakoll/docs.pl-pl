---
title: 'Instrukcje: Używanie tabeli ponownego mapowania kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: 72965d6968aab256579929acc00e629bcd3c71f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707339"
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="0e8c9-102">Instrukcje: Używanie tabeli ponownego mapowania kolorów</span><span class="sxs-lookup"><span data-stu-id="0e8c9-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="0e8c9-103">Ponowne mapowanie jest procesem konwertowania kolory na obrazie zgodnie z tabeli ponownego mapowania kolorów.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="0e8c9-104">Tabeli ponownego mapowania kolorów jest tablicą <xref:System.Drawing.Imaging.ColorMap> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="0e8c9-105">Każdy <xref:System.Drawing.Imaging.ColorMap> obiektów w tablicy ma <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> właściwości i <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="0e8c9-106">Gdy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rysuje na ilustracji każdego piksela obraz, który jest porównywany z tablicy stare kolory.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="0e8c9-107">Jeśli kolor piksela odpowiada stary kolor, jego kolor jest zmieniany na odpowiedniej nowy kolor.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="0e8c9-108">Kolory są zmieniane tylko w przypadku renderowania — wartości kolorów sam obraz (przechowywane w <xref:System.Drawing.Image> lub <xref:System.Drawing.Bitmap> obiektu) nie są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="0e8c9-109">Aby narysować ponownie zmapowany obrazu, zainicjowania tablicy <xref:System.Drawing.Imaging.ColorMap> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="0e8c9-110">Ta tablica do przekazania <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiektu, a następnie przekazać <xref:System.Drawing.Imaging.ImageAttributes> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e8c9-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e8c9-111">Example</span></span>  
 <span data-ttu-id="0e8c9-112">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku RemapInput.bmp.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="0e8c9-113">Ten kod tworzy tabeli ponownego mapowania kolorów, która składa się z pojedynczego <xref:System.Drawing.Imaging.ColorMap> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="0e8c9-114"><xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Właściwość `ColorRemap` obiekt ma kolor czerwony i <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> właściwość ma kolor niebieski.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="0e8c9-115">Obraz jest rysowane raz bez ponownego mapowania i drugi raz z ponownego mapowania.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="0e8c9-116">Proces ponownego mapowania zmienia wszystkie piksele czerwony na niebieski.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="0e8c9-117">Poniższa ilustracja pokazuje oryginalny obraz po lewej stronie i ponownie zmapowany obraz po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 <span data-ttu-id="0e8c9-118">![Ponowne mapowanie kolorów](./media/colortrans7.png "colortrans7")</span><span class="sxs-lookup"><span data-stu-id="0e8c9-118">![Color ReMap](./media/colortrans7.png "colortrans7")</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e8c9-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0e8c9-119">Compiling the Code</span></span>  
 <span data-ttu-id="0e8c9-120">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0e8c9-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e8c9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e8c9-121">See also</span></span>
- [<span data-ttu-id="0e8c9-122">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="0e8c9-122">Recoloring Images</span></span>](recoloring-images.md)
- [<span data-ttu-id="0e8c9-123">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="0e8c9-123">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
