---
title: 'Instrukcje: Przycinanie i skalowanie obrazów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: 1f6d721edc4f889c2da8ece63f262c7fb55192bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707703"
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="ae528-102">Instrukcje: Przycinanie i skalowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="ae528-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="ae528-103"><xref:System.Drawing.Graphics> Klasa udostępnia kilka <xref:System.Drawing.Graphics.DrawImage%2A> metod, niektóre z nich ma parametry prostokąt źródłowe i docelowe, które umożliwia przycinanie i skalowanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="ae528-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae528-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae528-104">Example</span></span>  
 <span data-ttu-id="ae528-105">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku dysku Apple.gif.</span><span class="sxs-lookup"><span data-stu-id="ae528-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="ae528-106">Kod rysuje obraz całej firmy apple w oryginalnym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="ae528-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="ae528-107">Następnie wywołuje kod <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu, aby narysować część obrazu firmy apple w prostokąta docelowego, który jest większy niż oryginalny obraz firmy apple.</span><span class="sxs-lookup"><span data-stu-id="ae528-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="ae528-108"><xref:System.Drawing.Graphics.DrawImage%2A> Metoda określa, która część firmy apple, aby narysować, analizując prostokąta źródłowego, który jest określony przez trzeci, czwarty, piąty i szósty argument.</span><span class="sxs-lookup"><span data-stu-id="ae528-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="ae528-109">W tym przypadku przycięcia firmy apple do 75 procent jego szerokość i wysokość 75 procent.</span><span class="sxs-lookup"><span data-stu-id="ae528-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="ae528-110"><xref:System.Drawing.Graphics.DrawImage%2A> Metoda określa, gdzie mają być wyznaczone przycięty firmy apple i jak duży, aby wprowadzić przycięty firmy apple, analizując prostokąta docelowego, która określony przez drugi argument.</span><span class="sxs-lookup"><span data-stu-id="ae528-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="ae528-111">W tym przypadku prostokąta docelowego jest 30 procent szerszy i 30 procent wyższe niż oryginalny obraz.</span><span class="sxs-lookup"><span data-stu-id="ae528-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="ae528-112">Poniższej ilustracji przedstawiono oryginalne firmy apple i skalowanych, przycięte firmy apple.</span><span class="sxs-lookup"><span data-stu-id="ae528-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 <span data-ttu-id="ae528-113">![Przycinanie i skalowanie](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span><span class="sxs-lookup"><span data-stu-id="ae528-113">![Crop & Scale](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae528-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ae528-114">Compiling the Code</span></span>  
 <span data-ttu-id="ae528-115">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ae528-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="ae528-116">Upewnij się zastąpić `Apple.gif` za pomocą nazwy pliku obrazu i ścieżki, które są prawidłowe w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="ae528-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae528-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae528-117">See also</span></span>
- [<span data-ttu-id="ae528-118">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="ae528-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="ae528-119">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="ae528-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
