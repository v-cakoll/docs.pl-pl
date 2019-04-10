---
title: 'Instrukcje: Ładowanie i wyświetlanie metaplików'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 39b7251b2789c7410e1d59b4aa7990a2f73055fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229358"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="d13eb-102">Instrukcje: Ładowanie i wyświetlanie metaplików</span><span class="sxs-lookup"><span data-stu-id="d13eb-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="d13eb-103"><xref:System.Drawing.Imaging.Metafile> Klasy, która dziedziczy po elemencie <xref:System.Drawing.Image> klasy, zawiera metody służące do rejestrowania, wyświetlanie i badanie obrazy wektorowe.</span><span class="sxs-lookup"><span data-stu-id="d13eb-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d13eb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d13eb-104">Example</span></span>  
 <span data-ttu-id="d13eb-105">Aby wyświetlić obraz wektora (metaplik) na ekranie, należy <xref:System.Drawing.Imaging.Metafile> obiektu i <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d13eb-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="d13eb-106">Przekazać nazwę pliku (lub strumienia) do <xref:System.Drawing.Imaging.Metafile> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d13eb-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="d13eb-107">Po utworzeniu <xref:System.Drawing.Imaging.Metafile> obiektów, przekaż go <xref:System.Drawing.Imaging.Metafile> obiekt <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d13eb-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="d13eb-108">W przykładzie jest tworzony <xref:System.Drawing.Imaging.Metafile> obiektu z pliku EMF (rozszerzony metaplik) i następnie Rysuje obraz z jego lewego górnego rogu w (60, 10).</span><span class="sxs-lookup"><span data-stu-id="d13eb-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="d13eb-109">Poniższa ilustracja przedstawia metaplik rysowane w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d13eb-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="d13eb-110">![Pozycja obrazu](./media/imageposition2.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="d13eb-110">![Image Position](./media/imageposition2.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d13eb-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d13eb-111">Compiling the Code</span></span>  
 <span data-ttu-id="d13eb-112">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d13eb-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d13eb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d13eb-113">See also</span></span>

- [<span data-ttu-id="d13eb-114">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="d13eb-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
