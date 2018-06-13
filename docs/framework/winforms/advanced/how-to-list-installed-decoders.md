---
title: 'Porady: lista zainstalowanych dekoderów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: 8a9dce0e4fd833bbda7bec5d35d26ef09a1fa761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523712"
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="40339-102">Porady: lista zainstalowanych dekoderów</span><span class="sxs-lookup"><span data-stu-id="40339-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="40339-103">Możesz wyświetlić listę dekodery obrazów dostępne na komputerze, w celu ustalenia, czy aplikacja może odczytywać format pliku określonego obrazu.</span><span class="sxs-lookup"><span data-stu-id="40339-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="40339-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Klasa udostępnia <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> metody statyczne, aby ustalić, który obraz dekodery są dostępne.</span><span class="sxs-lookup"><span data-stu-id="40339-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="40339-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> Zwraca tablicę <xref:System.Drawing.Imaging.ImageCodecInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="40339-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40339-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="40339-106">Example</span></span>  
 <span data-ttu-id="40339-107">Poniższy przykład kodu generuje listę zainstalowanych dekoderów i ich wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="40339-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40339-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="40339-108">Compiling the Code</span></span>  
 <span data-ttu-id="40339-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="40339-109">This example requires:</span></span>  
  
-   <span data-ttu-id="40339-110">Aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="40339-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="40339-111">A <xref:System.Windows.Forms.PaintEventArgs>, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="40339-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40339-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40339-112">See Also</span></span>  
 [<span data-ttu-id="40339-113">Instrukcje: lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="40339-113">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="40339-114">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="40339-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
