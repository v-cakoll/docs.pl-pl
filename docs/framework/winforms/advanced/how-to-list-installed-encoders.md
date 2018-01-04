---
title: "Porady: lista zainstalowanych koderów"
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
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec3ce7d2d933226162664826764c818eacf97afc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="a3d5f-102">Porady: lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="a3d5f-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="a3d5f-103">Można wyświetlić listę kodery obrazów dostępne na komputerze, w celu ustalenia, czy aplikacji można zapisać w formacie pliku określonego obrazu.</span><span class="sxs-lookup"><span data-stu-id="a3d5f-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="a3d5f-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Klasa udostępnia <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> metody statyczne, aby ustalić, który obraz koderów są dostępne.</span><span class="sxs-lookup"><span data-stu-id="a3d5f-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="a3d5f-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>Zwraca tablicę <xref:System.Drawing.Imaging.ImageCodecInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a3d5f-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3d5f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3d5f-106">Example</span></span>  
 <span data-ttu-id="a3d5f-107">Poniższy przykład kodu generuje listę zainstalowanych koderów i ich wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="a3d5f-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a3d5f-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a3d5f-108">Compiling the Code</span></span>  
 <span data-ttu-id="a3d5f-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a3d5f-109">This example requires:</span></span>  
  
-   <span data-ttu-id="a3d5f-110">Aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a3d5f-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="a3d5f-111">A <xref:System.Windows.Forms.PaintEventArgs>, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="a3d5f-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d5f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3d5f-112">See Also</span></span>  
 [<span data-ttu-id="a3d5f-113">Instrukcje: lista zainstalowanych dekoderów</span><span class="sxs-lookup"><span data-stu-id="a3d5f-113">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [<span data-ttu-id="a3d5f-114">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="a3d5f-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
