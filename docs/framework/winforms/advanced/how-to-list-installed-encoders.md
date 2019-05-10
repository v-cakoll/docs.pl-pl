---
title: 'Instrukcje: Lista zainstalowanych koderów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: 2634dd96b3aa5edcecde092919eb328b7f3dadc3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626843"
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="ce215-102">Instrukcje: Lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="ce215-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="ce215-103">Możesz wyświetlić listę kodeków obrazu dostępne na komputerze, w celu ustalenia, czy aplikację można zapisać do pliku określonego obrazu w formacie.</span><span class="sxs-lookup"><span data-stu-id="ce215-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="ce215-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Klasa udostępnia <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> metody statyczne, aby określić, który obraz koderów są dostępne.</span><span class="sxs-lookup"><span data-stu-id="ce215-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="ce215-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> Zwraca tablicę <xref:System.Drawing.Imaging.ImageCodecInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ce215-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce215-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce215-106">Example</span></span>  
 <span data-ttu-id="ce215-107">Poniższy kod generuje lista zainstalowanych koderów i ich wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="ce215-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ce215-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ce215-108">Compiling the Code</span></span>  
 <span data-ttu-id="ce215-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ce215-109">This example requires:</span></span>  
  
- <span data-ttu-id="ce215-110">Aplikacja Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ce215-110">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="ce215-111">A <xref:System.Windows.Forms.PaintEventArgs>, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="ce215-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce215-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce215-112">See also</span></span>

- [<span data-ttu-id="ce215-113">Instrukcje: Lista zainstalowanych dekoderów</span><span class="sxs-lookup"><span data-stu-id="ce215-113">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)
- [<span data-ttu-id="ce215-114">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="ce215-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
