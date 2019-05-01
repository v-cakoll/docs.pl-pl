---
title: 'Instrukcje: Rysowanie istniejącej mapy bitowej na ekranie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: 90511adf9caffe7952e270d6fe32dd85162a29d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004184"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="e0a28-102">Instrukcje: Rysowanie istniejącej mapy bitowej na ekranie</span><span class="sxs-lookup"><span data-stu-id="e0a28-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="e0a28-103">Istniejący obraz można łatwo rysować na ekranie.</span><span class="sxs-lookup"><span data-stu-id="e0a28-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="e0a28-104">Najpierw należy utworzyć <xref:System.Drawing.Bitmap> obiektu za pomocą konstruktora mapy bitowej, który przyjmuje nazwę pliku <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="e0a28-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="e0a28-105">Ten konstruktor akceptuje obrazów z kilku różnych formatach plików, w tym BMP, GIF, JPEG, PNG i TIFF.</span><span class="sxs-lookup"><span data-stu-id="e0a28-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="e0a28-106">Po utworzeniu <xref:System.Drawing.Bitmap> obiektów, przekaż go <xref:System.Drawing.Bitmap> obiekt <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e0a28-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0a28-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0a28-107">Example</span></span>  
 <span data-ttu-id="e0a28-108">Ten przykład tworzy <xref:System.Drawing.Bitmap> obiekt z pliku JPEG i następnie rysuje mapę bitową z jego lewego górnego rogu w (60, 10).</span><span class="sxs-lookup"><span data-stu-id="e0a28-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="e0a28-109">Poniższa ilustracja przedstawia mapy bitowej rysowane w określonej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="e0a28-109">The following illustration shows the bitmap drawn at the specified location:</span></span>  
  
 ![Zrzut ekranu pokazujący obrazu na określonej pozycji.](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0a28-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e0a28-111">Compiling the Code</span></span>  
 <span data-ttu-id="e0a28-112">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e0a28-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a28-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0a28-113">See also</span></span>

- [<span data-ttu-id="e0a28-114">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0a28-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="e0a28-115">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="e0a28-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
