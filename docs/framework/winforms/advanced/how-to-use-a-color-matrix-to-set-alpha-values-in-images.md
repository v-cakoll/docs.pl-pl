---
title: 'Porady: stosowanie macierzy kolorów ustawiania wartości alfa na obrazach'
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
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423738"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="1433a-102">Porady: stosowanie macierzy kolorów ustawiania wartości alfa na obrazach</span><span class="sxs-lookup"><span data-stu-id="1433a-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="1433a-103">Klasa <xref:System.Drawing.Bitmap> (która dziedziczy z klasy <xref:System.Drawing.Image>) i Klasa <xref:System.Drawing.Imaging.ImageAttributes> zapewniają funkcje pobierania i ustawiania wartości pikseli.</span><span class="sxs-lookup"><span data-stu-id="1433a-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="1433a-104">Za pomocą klasy <xref:System.Drawing.Imaging.ImageAttributes> można modyfikować wartości alfa dla całego obrazu lub wywołać metodę <xref:System.Drawing.Bitmap.SetPixel%2A> klasy <xref:System.Drawing.Bitmap>, aby modyfikować poszczególne wartości pikseli.</span><span class="sxs-lookup"><span data-stu-id="1433a-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1433a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="1433a-105">Example</span></span>  
 <span data-ttu-id="1433a-106">Klasa <xref:System.Drawing.Imaging.ImageAttributes> ma wiele właściwości, których można użyć do modyfikowania obrazów podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="1433a-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="1433a-107">W poniższym przykładzie obiekt <xref:System.Drawing.Imaging.ImageAttributes> jest używany do ustawiania wszystkich wartości alfa na 80 procent ich wielkości.</span><span class="sxs-lookup"><span data-stu-id="1433a-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="1433a-108">Jest to realizowane przez zainicjowanie macierzy kolorów i ustawienie wartości skalowania alfa w macierzy na 0,8.</span><span class="sxs-lookup"><span data-stu-id="1433a-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="1433a-109">Adres macierzy kolorów jest przesyłany do metody <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> obiektu <xref:System.Drawing.Imaging.ImageAttributes>, a obiekt <xref:System.Drawing.Imaging.ImageAttributes> jest przesyłany do metody <xref:System.Drawing.Graphics.DrawString%2A> obiektu <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="1433a-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="1433a-110">Podczas renderowania wartości alfa w mapie bitowej są konwertowane na 80 procent ich wielkości.</span><span class="sxs-lookup"><span data-stu-id="1433a-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="1433a-111">Powoduje to obraz, który jest mieszany z tłem.</span><span class="sxs-lookup"><span data-stu-id="1433a-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="1433a-112">Jak widać na poniższej ilustracji, obraz mapy bitowej wygląda niewidoczny; za jego pomocą można wyświetlić pełną czarną linię.</span><span class="sxs-lookup"><span data-stu-id="1433a-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="1433a-113">![Zrzut ekranu przedstawiający mieszanie alfa przy użyciu macierzy.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "Obraz2")</span><span class="sxs-lookup"><span data-stu-id="1433a-113">![Screenshot of alpha blending using a matrix.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")</span></span>  
  
 <span data-ttu-id="1433a-114">Gdy obraz znajduje się na białej części tła, obraz został zmieszany z kolorem biały.</span><span class="sxs-lookup"><span data-stu-id="1433a-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="1433a-115">Gdy obraz przecina czarną linię, obraz zostanie zmieszany z kolorem czarnym.</span><span class="sxs-lookup"><span data-stu-id="1433a-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1433a-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1433a-116">Compiling the Code</span></span>  
 <span data-ttu-id="1433a-117">Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="1433a-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1433a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1433a-118">See also</span></span>

- [<span data-ttu-id="1433a-119">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1433a-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="1433a-120">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="1433a-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
