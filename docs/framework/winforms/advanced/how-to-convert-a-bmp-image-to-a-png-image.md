---
title: 'Porady: konwertowanie obrazu w formacie BMP na format PNG'
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
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ee2669c41f4ee558d9457cee7df0ae8425cf065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="7dd3f-102">Porady: konwertowanie obrazu w formacie BMP na format PNG</span><span class="sxs-lookup"><span data-stu-id="7dd3f-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="7dd3f-103">Często należy przekonwertować z jednego obrazu pliku formatu do innego.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="7dd3f-104">Wykonaj tę konwersję łatwo wywołując <xref:System.Drawing.Image.Save%2A> metody <xref:System.Drawing.Image> klasy i określając <xref:System.Drawing.Imaging.ImageFormat> formatu pliku odpowiedni obraz.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dd3f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="7dd3f-105">Example</span></span>  
 <span data-ttu-id="7dd3f-106">Poniższy przykład ładuje obrazu w formacie BMP z typem, a następnie zapisuje obraz w formacie PNG.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7dd3f-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7dd3f-107">Compiling the Code</span></span>  
 <span data-ttu-id="7dd3f-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7dd3f-108">This example requires:</span></span>  
  
-   <span data-ttu-id="7dd3f-109">Aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="7dd3f-110">Odwołanie do `System.Drawing.Imaging` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd3f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7dd3f-111">See Also</span></span>  
 [<span data-ttu-id="7dd3f-112">Instrukcje: lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="7dd3f-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="7dd3f-113">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="7dd3f-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [<span data-ttu-id="7dd3f-114">Typy map bitowych</span><span class="sxs-lookup"><span data-stu-id="7dd3f-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
