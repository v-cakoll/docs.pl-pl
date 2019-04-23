---
title: 'Instrukcje: Stosowanie macierzy kolorów ustawiania wartości alfa na obrazach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 79937f0801a790d4ff1ab327aaaf45ef1b881827
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199547"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="c925d-102">Instrukcje: Stosowanie macierzy kolorów ustawiania wartości alfa na obrazach</span><span class="sxs-lookup"><span data-stu-id="c925d-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="c925d-103"><xref:System.Drawing.Bitmap> Klasy (który dziedziczy z <xref:System.Drawing.Image> klasy) oraz <xref:System.Drawing.Imaging.ImageAttributes> klasy zapewniają funkcje służące do pobierania i ustawiania wartości pikseli.</span><span class="sxs-lookup"><span data-stu-id="c925d-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="c925d-104">Możesz użyć <xref:System.Drawing.Imaging.ImageAttributes> klasy, aby zmodyfikować alfa wartości dla całego obrazu lub może wywołać <xref:System.Drawing.Bitmap.SetPixel%2A> metody <xref:System.Drawing.Bitmap> klasy, aby zmodyfikować wartości poszczególnych pikseli.</span><span class="sxs-lookup"><span data-stu-id="c925d-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c925d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c925d-105">Example</span></span>  
 <span data-ttu-id="c925d-106"><xref:System.Drawing.Imaging.ImageAttributes> Klasa ma wiele właściwości, które służy do modyfikowania obrazów podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="c925d-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="c925d-107">W poniższym przykładzie <xref:System.Drawing.Imaging.ImageAttributes> obiekt jest używany do ustawiania wartości alfa do 80 procent o tym, co było.</span><span class="sxs-lookup"><span data-stu-id="c925d-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="c925d-108">Odbywa się przez inicjowanie macierzy kolorów i ustawienie alfa, wartość w macierzy, aby 0,8 skalowania.</span><span class="sxs-lookup"><span data-stu-id="c925d-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="c925d-109">Adres macierzy kolorów jest przekazywany do <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiektu, a <xref:System.Drawing.Imaging.ImageAttributes> obiekt jest przekazywany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c925d-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="c925d-110">Podczas renderowania, wartości alfa w mapie bitowej są konwertowane do 80 procent o tym, co było.</span><span class="sxs-lookup"><span data-stu-id="c925d-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="c925d-111">Skutkuje to obrazu, która jest zmieszana w tle.</span><span class="sxs-lookup"><span data-stu-id="c925d-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="c925d-112">Jak pokazano na poniższej ilustracji, Przezroczysty; wygląd obrazu mapy bitowej Możesz zobaczyć czarna linia ciągła przy jego użyciu.</span><span class="sxs-lookup"><span data-stu-id="c925d-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="c925d-113">![Przenikanie alfa, za pomocą macierzy](./media/image2.png "obraz2")</span><span class="sxs-lookup"><span data-stu-id="c925d-113">![Alpha Blending Using a Matrix](./media/image2.png "image2")</span></span>  
  
 <span data-ttu-id="c925d-114">W przypadku obrazu na fragment białe tło, obraz, który ma zostały mieszane z kolor biały znak.</span><span class="sxs-lookup"><span data-stu-id="c925d-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="c925d-115">Gdzie obraz przecina czarna linia obrazu jest zmieszana przy użyciu kolor czarny.</span><span class="sxs-lookup"><span data-stu-id="c925d-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c925d-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c925d-116">Compiling the Code</span></span>  
 <span data-ttu-id="c925d-117">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c925d-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c925d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c925d-118">See also</span></span>

- [<span data-ttu-id="c925d-119">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c925d-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="c925d-120">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="c925d-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
