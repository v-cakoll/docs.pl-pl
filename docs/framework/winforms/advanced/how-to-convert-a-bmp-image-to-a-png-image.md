---
title: 'Instrukcje: Konwertowanie obrazu BMP na format PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: e11e2874853fb924b2da09f9fdc986873941f141
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676448"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="e4086-102">Instrukcje: Konwertowanie obrazu BMP na format PNG</span><span class="sxs-lookup"><span data-stu-id="e4086-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="e4086-103">Często należy przekonwertować z jednego obrazu pliku formatu do innego.</span><span class="sxs-lookup"><span data-stu-id="e4086-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="e4086-104">Możesz łatwo zrobić ta konwersja przez wywołanie metody <xref:System.Drawing.Image.Save%2A> metody <xref:System.Drawing.Image> klasy i określając <xref:System.Drawing.Imaging.ImageFormat> dla formatu plików odpowiedni obraz.</span><span class="sxs-lookup"><span data-stu-id="e4086-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4086-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4086-105">Example</span></span>  
 <span data-ttu-id="e4086-106">Poniższy przykład załaduje obraz BMP z typem, a następnie zapisuje obraz w formacie PNG.</span><span class="sxs-lookup"><span data-stu-id="e4086-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4086-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e4086-107">Compiling the Code</span></span>  
 <span data-ttu-id="e4086-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e4086-108">This example requires:</span></span>  
  
-   <span data-ttu-id="e4086-109">Aplikacja Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e4086-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="e4086-110">Odwołanie do `System.Drawing.Imaging` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e4086-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4086-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4086-111">See also</span></span>
- [<span data-ttu-id="e4086-112">Instrukcje: Lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="e4086-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [<span data-ttu-id="e4086-113">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="e4086-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
- [<span data-ttu-id="e4086-114">Typy map bitowych</span><span class="sxs-lookup"><span data-stu-id="e4086-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
