---
title: "Porady: lista zainstalowanych dekoderów"
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
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17cbdebfa6cbb0cacacd923de4bd22125c812938
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="bb038-102">Porady: lista zainstalowanych dekoderów</span><span class="sxs-lookup"><span data-stu-id="bb038-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="bb038-103">Możesz wyświetlić listę dekodery obrazów dostępne na komputerze, w celu ustalenia, czy aplikacja może odczytywać format pliku określonego obrazu.</span><span class="sxs-lookup"><span data-stu-id="bb038-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="bb038-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Klasa udostępnia <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> metody statyczne, aby ustalić, który obraz dekodery są dostępne.</span><span class="sxs-lookup"><span data-stu-id="bb038-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="bb038-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>Zwraca tablicę <xref:System.Drawing.Imaging.ImageCodecInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bb038-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb038-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb038-106">Example</span></span>  
 <span data-ttu-id="bb038-107">Poniższy przykład kodu generuje listę zainstalowanych dekoderów i ich wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb038-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb038-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bb038-108">Compiling the Code</span></span>  
 <span data-ttu-id="bb038-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="bb038-109">This example requires:</span></span>  
  
-   <span data-ttu-id="bb038-110">Aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb038-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="bb038-111">A <xref:System.Windows.Forms.PaintEventArgs>, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="bb038-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb038-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb038-112">See Also</span></span>  
 [<span data-ttu-id="bb038-113">Porady: lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="bb038-113">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="bb038-114">Używanie kodeków obrazu w zarządzanym GDI +</span><span class="sxs-lookup"><span data-stu-id="bb038-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
