---
title: 'Porady: tworzenie pionowego tekstu'
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
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d690700224954e71b163f6e22a25e343d7e414ce
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="84606-102">Porady: tworzenie pionowego tekstu</span><span class="sxs-lookup"><span data-stu-id="84606-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="84606-103">Można użyć <xref:System.Drawing.StringFormat> obiektu w celu określenia, czy tekst być rysowany pionowo, a nie w poziomie.</span><span class="sxs-lookup"><span data-stu-id="84606-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84606-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="84606-104">Example</span></span>  
 <span data-ttu-id="84606-105">Poniższy przykład przypisuje wartość <xref:System.Drawing.StringFormatFlags.DirectionVertical> do <xref:System.Drawing.StringFormat.FormatFlags%2A> właściwość <xref:System.Drawing.StringFormat> obiektu.</span><span class="sxs-lookup"><span data-stu-id="84606-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="84606-106">Czy <xref:System.Drawing.StringFormat> obiekt jest przekazywany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="84606-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="84606-107">Wartość <xref:System.Drawing.StringFormatFlags.DirectionVertical> jest elementem członkowskim <xref:System.Drawing.StringFormatFlags> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="84606-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="84606-108">Na poniższej ilustracji przedstawiono pionowego tekstu.</span><span class="sxs-lookup"><span data-stu-id="84606-108">The following illustration shows the vertical text.</span></span>  
  
 <span data-ttu-id="84606-109">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")</span><span class="sxs-lookup"><span data-stu-id="84606-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84606-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="84606-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="84606-111">Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e` , który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="84606-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84606-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84606-112">See Also</span></span>  
 [<span data-ttu-id="84606-113">Porady: Rysowanie tekstu z GDI</span><span class="sxs-lookup"><span data-stu-id="84606-113">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
