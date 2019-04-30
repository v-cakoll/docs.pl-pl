---
title: 'Instrukcje: Lista zainstalowanych dekoderów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: c92b8010def2f77f859ee0bd9cdb1ed51dd15f27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723046"
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="86f9b-102">Instrukcje: Lista zainstalowanych dekoderów</span><span class="sxs-lookup"><span data-stu-id="86f9b-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="86f9b-103">Możesz wyświetlić listę dekodery obrazów dostępnych na komputerze, w celu ustalenia, czy aplikacja może odczytywać format pliku określonego obrazu.</span><span class="sxs-lookup"><span data-stu-id="86f9b-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="86f9b-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Klasa udostępnia <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> metody statyczne, aby określić, który obraz dekodery są dostępne.</span><span class="sxs-lookup"><span data-stu-id="86f9b-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="86f9b-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> Zwraca tablicę <xref:System.Drawing.Imaging.ImageCodecInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="86f9b-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86f9b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="86f9b-106">Example</span></span>  
 <span data-ttu-id="86f9b-107">Poniższy kod generuje lista zainstalowanych dekoderów i ich wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="86f9b-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="86f9b-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="86f9b-108">Compiling the Code</span></span>  
 <span data-ttu-id="86f9b-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="86f9b-109">This example requires:</span></span>  
  
- <span data-ttu-id="86f9b-110">Aplikacja Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="86f9b-110">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="86f9b-111">A <xref:System.Windows.Forms.PaintEventArgs>, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="86f9b-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f9b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86f9b-112">See also</span></span>

- [<span data-ttu-id="86f9b-113">Instrukcje: Lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="86f9b-113">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="86f9b-114">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="86f9b-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
