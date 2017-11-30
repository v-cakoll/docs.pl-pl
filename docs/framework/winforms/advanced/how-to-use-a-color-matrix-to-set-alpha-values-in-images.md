---
title: "Porady: stosowanie macierzy kolorów ustawiania wartości alfa na obrazach"
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
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba7a016c96556f2719d4a247c93df7ac698b24fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="14589-102">Porady: stosowanie macierzy kolorów ustawiania wartości alfa na obrazach</span><span class="sxs-lookup"><span data-stu-id="14589-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="14589-103"><xref:System.Drawing.Bitmap> Klasy (który dziedziczy z <xref:System.Drawing.Image> klasy) oraz <xref:System.Drawing.Imaging.ImageAttributes> klasy zapewniają funkcje służące do pobierania i ustawiania wartości pikseli.</span><span class="sxs-lookup"><span data-stu-id="14589-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="14589-104">Można użyć <xref:System.Drawing.Imaging.ImageAttributes> klasę, aby zmodyfikować alfa wartości dla całego obrazu lub można wywołać <xref:System.Drawing.Bitmap.SetPixel%2A> metody <xref:System.Drawing.Bitmap> klasy, aby zmodyfikować wartości poszczególnych pikseli.</span><span class="sxs-lookup"><span data-stu-id="14589-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14589-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="14589-105">Example</span></span>  
 <span data-ttu-id="14589-106"><xref:System.Drawing.Imaging.ImageAttributes> Klasa ma wiele właściwości, które służy do modyfikowania obrazów podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="14589-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="14589-107">W poniższym przykładzie <xref:System.Drawing.Imaging.ImageAttributes> obiekt jest używany do ustawiania wartości alfa do 80 procent jakie były.</span><span class="sxs-lookup"><span data-stu-id="14589-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="14589-108">Jest to realizowane przez inicjowania macierzy kolorów i ustawienie alfa wartość w macierzy 0,8 skalowania.</span><span class="sxs-lookup"><span data-stu-id="14589-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="14589-109">Adres macierzy kolorów są przekazywane do <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiektu i <xref:System.Drawing.Imaging.ImageAttributes> obiekt jest przekazywany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="14589-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="14589-110">Podczas renderowania wartości alfa w mapie bitowej są konwertowane na jakie były 80 procent.</span><span class="sxs-lookup"><span data-stu-id="14589-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="14589-111">Powoduje to obraz, który jest mieszane w tle.</span><span class="sxs-lookup"><span data-stu-id="14589-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="14589-112">Jak pokazano na poniższej ilustracji, Przezroczysty; wygląd obrazu mapy bitowej widać stałe czarnej linii przy jego użyciu.</span><span class="sxs-lookup"><span data-stu-id="14589-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="14589-113">![Przenikanie alfa przy użyciu macierzy](../../../../docs/framework/winforms/advanced/media/image2.png "obraz2")</span><span class="sxs-lookup"><span data-stu-id="14589-113">![Alpha Blending Using a Matrix](../../../../docs/framework/winforms/advanced/media/image2.png "image2")</span></span>  
  
 <span data-ttu-id="14589-114">W przypadku obrazu na fragment białe tło, obraz ma zostały mieszane z kolor biały znak.</span><span class="sxs-lookup"><span data-stu-id="14589-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="14589-115">Gdy obraz przecina czarnej linii obrazu jest mieszane z kolor czarny.</span><span class="sxs-lookup"><span data-stu-id="14589-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14589-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="14589-116">Compiling the Code</span></span>  
 <span data-ttu-id="14589-117">Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="14589-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14589-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14589-118">See Also</span></span>  
 [<span data-ttu-id="14589-119">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="14589-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="14589-120">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="14589-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
