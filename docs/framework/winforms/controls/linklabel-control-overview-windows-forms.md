---
title: "LinkLabel — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0cb01c0fc5503a5bf16e1f191d87ae90907ec816
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linklabel-control-overview-windows-forms"></a><span data-ttu-id="4c66a-102">LinkLabel — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="4c66a-102">LinkLabel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="4c66a-103">Formularze systemu Windows <xref:System.Windows.Forms.LinkLabel> sterowanie umożliwia dodawanie łączy stylu sieci Web do aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4c66a-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to add Web-style links to Windows Forms applications.</span></span> <span data-ttu-id="4c66a-104">Można użyć <xref:System.Windows.Forms.LinkLabel> kontroli dla wszystko, co umożliwia <xref:System.Windows.Forms.Label> sterować dla; można też określić część tekstu jako łącze do pliku, folderu lub strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4c66a-104">You can use the <xref:System.Windows.Forms.LinkLabel> control for everything that you can use the <xref:System.Windows.Forms.Label> control for; you also can set part of the text as a link to a file, folder, or Web page.</span></span>  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a><span data-ttu-id="4c66a-105">Co można zrobić za pomocą formantu LinkLabel</span><span class="sxs-lookup"><span data-stu-id="4c66a-105">What You Can Do with the LinkLabel Control</span></span>  
 <span data-ttu-id="4c66a-106">Oprócz tych właściwości, metod i zdarzeń <xref:System.Windows.Forms.Label> kontroli, <xref:System.Windows.Forms.LinkLabel> formant ma właściwości hiperłącza i kolory łączy.</span><span class="sxs-lookup"><span data-stu-id="4c66a-106">In addition to all the properties, methods, and events of the <xref:System.Windows.Forms.Label> control, the <xref:System.Windows.Forms.LinkLabel> control has properties for hyperlinks and link colors.</span></span> <span data-ttu-id="4c66a-107"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Właściwość ustawia obszar tekst, który uaktywnia łącze.</span><span class="sxs-lookup"><span data-stu-id="4c66a-107">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property sets the area of the text that activates the link.</span></span> <span data-ttu-id="4c66a-108"><xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, I <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> właściwości ustawione kolory łącza.</span><span class="sxs-lookup"><span data-stu-id="4c66a-108">The <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> properties set the colors of the link.</span></span> <span data-ttu-id="4c66a-109"><xref:System.Windows.Forms.LinkLabel.LinkClicked> Zdarzeń określa, co się stanie w przypadku wybrania tekst łącza.</span><span class="sxs-lookup"><span data-stu-id="4c66a-109">The <xref:System.Windows.Forms.LinkLabel.LinkClicked> event determines what happens when the link text is selected.</span></span>  
  
 <span data-ttu-id="4c66a-110">Najprostsza stosowania <xref:System.Windows.Forms.LinkLabel> formant jest do wyświetlenia przy użyciu jednego łącza <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości, ale można również wyświetlić wiele hiperłącza, za pomocą <xref:System.Windows.Forms.LinkLabel.Links%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4c66a-110">The simplest use of the <xref:System.Windows.Forms.LinkLabel> control is to display a single link using the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property, but you can also display multiple hyperlinks using the <xref:System.Windows.Forms.LinkLabel.Links%2A> property.</span></span> <span data-ttu-id="4c66a-111"><xref:System.Windows.Forms.LinkLabel.Links%2A> Właściwość umożliwia dostęp do kolekcji łączy.</span><span class="sxs-lookup"><span data-stu-id="4c66a-111">The <xref:System.Windows.Forms.LinkLabel.Links%2A> property enables you to access a collection of links.</span></span> <span data-ttu-id="4c66a-112">Można również określić, że dane w <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> właściwości poszczególnych <xref:System.Windows.Forms.LinkLabel.Link> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4c66a-112">You can also specify data in the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property of each individual <xref:System.Windows.Forms.LinkLabel.Link> object.</span></span> <span data-ttu-id="4c66a-113">Wartość <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> właściwości może służyć do przechowywania lokalizację pliku do wyświetlania lub adres witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4c66a-113">The value of the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property can be used to store the location of a file to display or the address of a Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c66a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c66a-114">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel>  
 [<span data-ttu-id="4c66a-115">Informacje o formancie etykiety</span><span class="sxs-lookup"><span data-stu-id="4c66a-115">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="4c66a-116">Porady: łączenie z obiektu lub strony sieci Web za pomocą formantu LinkLabel formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4c66a-116">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [<span data-ttu-id="4c66a-117">Porady: Zmienianie wyglądu formantu LinkLabel formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4c66a-117">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
