---
title: "Aplikacje interfejsu wielu dokumentów (MDI)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c122931b0a00f487ddab07550913988462cfd50e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="9ec30-102">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="9ec30-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="9ec30-103">Aplikacje interfejsu wielu dokumentów (MDI) umożliwiają wyświetlanie wielu dokumentów w tym samym czasie, każdy dokument wyświetlany w osobnym oknie.</span><span class="sxs-lookup"><span data-stu-id="9ec30-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="9ec30-104">MDI — aplikacje często mają elementu menu okna zawierającego podmenu do przełączania między systemem windows lub dokumenty.</span><span class="sxs-lookup"><span data-stu-id="9ec30-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ec30-105">Istnieją pewne różnice zachowanie między formularze MDI i interfejsu pojedynczego dokumentu (SDI) systemu windows w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9ec30-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="9ec30-106">`Opacity` Właściwość nie ma wpływu na wyglądu formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="9ec30-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="9ec30-107">Ponadto <xref:System.Windows.Forms.Form.CenterToParent%2A> — metoda nie ma wpływu na zachowanie formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="9ec30-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ec30-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9ec30-108">In This Section</span></span>  
 [<span data-ttu-id="9ec30-109">Porady: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="9ec30-109">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="9ec30-110">Zawiera wskazówki dotyczące tworzenia kontenera dla wielu dokumentów w aplikacji MDI.</span><span class="sxs-lookup"><span data-stu-id="9ec30-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="9ec30-111">Porady: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="9ec30-111">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="9ec30-112">Zawiera wskazówki dotyczące tworzenia co najmniej jednego systemu windows, które działają w ramach formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="9ec30-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="9ec30-113">Porady: ustalić podrzędnego Active MDI</span><span class="sxs-lookup"><span data-stu-id="9ec30-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="9ec30-114">Zawiera wskazówki dotyczące weryfikacji okno podrzędne, które ma fokus (i wysyłanie zawartości do Schowka).</span><span class="sxs-lookup"><span data-stu-id="9ec30-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="9ec30-115">Porady: wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="9ec30-115">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="9ec30-116">Zawiera wskazówki dotyczące informacji do okna aktywny transport.</span><span class="sxs-lookup"><span data-stu-id="9ec30-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="9ec30-117">Porady: Aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="9ec30-117">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="9ec30-118">Zapewnia instrukcje dla kafelków, kaskadowych lub rozmieszczanie okien podrzędnych MDI aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9ec30-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
