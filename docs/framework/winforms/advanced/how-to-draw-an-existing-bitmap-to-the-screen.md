---
title: "Porady: rysowanie istniejącej mapy bitowej na ekranie"
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
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b3c8aef4aee74fbcdcc80301f5d5c1020883341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="71c83-102">Porady: rysowanie istniejącej mapy bitowej na ekranie</span><span class="sxs-lookup"><span data-stu-id="71c83-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="71c83-103">Na ekranie, można łatwo Rysuj istniejącego obrazu.</span><span class="sxs-lookup"><span data-stu-id="71c83-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="71c83-104">Najpierw należy utworzyć <xref:System.Drawing.Bitmap> obiektu za pomocą konstruktora mapy bitowej, który przyjmuje nazwę pliku <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="71c83-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="71c83-105">Ten konstruktor akceptuje obrazów za pomocą kilku różnych formatach plików, w tym BMP, GIF, JPEG, PNG i TIFF.</span><span class="sxs-lookup"><span data-stu-id="71c83-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="71c83-106">Po utworzeniu <xref:System.Drawing.Bitmap> obiektu, który przekazać <xref:System.Drawing.Bitmap> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="71c83-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71c83-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="71c83-107">Example</span></span>  
 <span data-ttu-id="71c83-108">Ten przykład tworzy <xref:System.Drawing.Bitmap> obiekt plik JPEG, a następnie pobiera mapy bitowej z jego lewego górnego rogu na (60, 10).</span><span class="sxs-lookup"><span data-stu-id="71c83-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="71c83-109">Na poniższej ilustracji przedstawiono mapy bitowej rysowana w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="71c83-109">The following illustration shows the bitmap drawn at the specified location.</span></span>  
  
 <span data-ttu-id="71c83-110">![Pozycja obrazu](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span><span class="sxs-lookup"><span data-stu-id="71c83-110">![Image Position](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71c83-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="71c83-111">Compiling the Code</span></span>  
 <span data-ttu-id="71c83-112">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71c83-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c83-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71c83-113">See Also</span></span>  
 [<span data-ttu-id="71c83-114">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71c83-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="71c83-115">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="71c83-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
