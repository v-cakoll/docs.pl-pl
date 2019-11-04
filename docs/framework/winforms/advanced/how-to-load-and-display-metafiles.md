---
title: 'Porady: ładowanie i wyświetlanie metaplików'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424819"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="9dab5-102">Porady: ładowanie i wyświetlanie metaplików</span><span class="sxs-lookup"><span data-stu-id="9dab5-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="9dab5-103">Klasa <xref:System.Drawing.Imaging.Metafile>, która dziedziczy z klasy <xref:System.Drawing.Image>, zapewnia metody rejestrowania, wyświetlania i badania obrazów wektorowych.</span><span class="sxs-lookup"><span data-stu-id="9dab5-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dab5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9dab5-104">Example</span></span>  
 <span data-ttu-id="9dab5-105">Aby wyświetlić obraz wektora (metaplik) na ekranie, potrzebny jest obiekt <xref:System.Drawing.Imaging.Metafile> i <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9dab5-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="9dab5-106">Przekaż nazwę pliku (lub strumienia) do konstruktora <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="9dab5-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="9dab5-107">Po utworzeniu obiektu <xref:System.Drawing.Imaging.Metafile>, Przekaż ten obiekt <xref:System.Drawing.Imaging.Metafile> do metody <xref:System.Drawing.Graphics.DrawImage%2A> obiektu <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="9dab5-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="9dab5-108">Przykład tworzy obiekt <xref:System.Drawing.Imaging.Metafile> z pliku EMF (Enhanced Metafile), a następnie rysuje obraz w lewym górnym rogu w lokalizacji (60, 10).</span><span class="sxs-lookup"><span data-stu-id="9dab5-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="9dab5-109">Na poniższej ilustracji przedstawiono metaplik rysowany w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9dab5-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="9dab5-110">![Zrzut ekranu przedstawiający położenie obrazu.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="9dab5-110">![Screenshot showing image position.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9dab5-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9dab5-111">Compiling the Code</span></span>  
 <span data-ttu-id="9dab5-112">Poprzedni przykład jest przeznaczony do użytku z Windows Forms i wymaga `e`<xref:System.Windows.Forms.PaintEventArgs>, który jest parametrem programu obsługi zdarzeń <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="9dab5-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dab5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9dab5-113">See also</span></span>

- [<span data-ttu-id="9dab5-114">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="9dab5-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
