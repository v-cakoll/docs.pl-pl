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
ms.openlocfilehash: c2b0a89966100077d5a72edc11822c356d2de1b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522773"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="7db6b-102">Porady: ładowanie i wyświetlanie metaplików</span><span class="sxs-lookup"><span data-stu-id="7db6b-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="7db6b-103"><xref:System.Drawing.Imaging.Metafile> Klasy, która dziedziczy <xref:System.Drawing.Image> klasy, metody do rejestrowania, wyświetlanie i badanie wektor obrazów.</span><span class="sxs-lookup"><span data-stu-id="7db6b-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7db6b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7db6b-104">Example</span></span>  
 <span data-ttu-id="7db6b-105">Aby wyświetlić obraz wektora (metaplik) na ekranie, należy <xref:System.Drawing.Imaging.Metafile> obiektu i <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7db6b-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="7db6b-106">Przekaż nazwę pliku (lub strumień) do <xref:System.Drawing.Imaging.Metafile> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7db6b-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="7db6b-107">Po utworzeniu <xref:System.Drawing.Imaging.Metafile> obiektu, który przekazać <xref:System.Drawing.Imaging.Metafile> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7db6b-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="7db6b-108">W przykładzie jest tworzony <xref:System.Drawing.Imaging.Metafile> obiektów z pliku EMF (rozszerzony metaplik), a następnie Rysuje obraz z jego lewego górnego rogu na (60, 10).</span><span class="sxs-lookup"><span data-stu-id="7db6b-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="7db6b-109">Na poniższej ilustracji przedstawiono metaplik rysowana w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="7db6b-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="7db6b-110">![Pozycja obrazu](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="7db6b-110">![Image Position](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7db6b-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7db6b-111">Compiling the Code</span></span>  
 <span data-ttu-id="7db6b-112">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7db6b-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db6b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7db6b-113">See Also</span></span>  
 [<span data-ttu-id="7db6b-114">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="7db6b-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
