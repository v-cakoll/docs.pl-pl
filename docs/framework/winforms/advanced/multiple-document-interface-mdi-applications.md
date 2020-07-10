---
title: Aplikacje interfejsu wielu dokumentów (MDI)
description: Dowiedz się, w jaki sposób Windows Forms aplikacje interfejsu wielu dokumentów (MDI) umożliwiają wyświetlanie wielu dokumentów w tym samym czasie, z każdym dokumentem wyświetlanym w osobnym oknie.
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174656"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="f693f-103">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="f693f-103">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="f693f-104">Aplikacje interfejsu wielu dokumentów (MDI) umożliwiają wyświetlanie wielu dokumentów w tym samym czasie, przy czym każdy dokument jest wyświetlany w osobnym oknie.</span><span class="sxs-lookup"><span data-stu-id="f693f-104">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="f693f-105">Aplikacje MDI często mają element menu okna z podmenumi do przełączania między oknami lub dokumentami.</span><span class="sxs-lookup"><span data-stu-id="f693f-105">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f693f-106">Istnieją pewne różnice w zachowaniu między formularzami MDI i oknami interfejsu jednostronicowego (SDI) w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f693f-106">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="f693f-107">`Opacity`Właściwość nie ma wpływu na wygląd formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="f693f-107">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="f693f-108">Ponadto metoda nie <xref:System.Windows.Forms.Form.CenterToParent%2A> wpływa na zachowanie formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="f693f-108">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f693f-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f693f-109">In This Section</span></span>  
 [<span data-ttu-id="f693f-110">Porady: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="f693f-110">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="f693f-111">Zawiera wskazówki dotyczące tworzenia kontenera dla wielu dokumentów w aplikacji MDI.</span><span class="sxs-lookup"><span data-stu-id="f693f-111">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="f693f-112">Porady: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="f693f-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="f693f-113">Zawiera wskazówki dotyczące tworzenia jednego lub kilku okien, które działają w ramach formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="f693f-113">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="f693f-114">Instrukcje: określanie elementu podrzędnego MDI Active</span><span class="sxs-lookup"><span data-stu-id="f693f-114">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="f693f-115">Zawiera wskazówki dotyczące weryfikowania okna podrzędnego z fokusem (i wysyłania jego zawartości do schowka).</span><span class="sxs-lookup"><span data-stu-id="f693f-115">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="f693f-116">Instrukcje: wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="f693f-116">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="f693f-117">Zawiera wskazówki dotyczące transportowania informacji do aktywnego okna podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f693f-117">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="f693f-118">Porady: aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="f693f-118">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="f693f-119">Oferuje wskazówki dotyczące dzielenia, kaskadowania lub rozmieszczania podrzędnych okien aplikacji MDI.</span><span class="sxs-lookup"><span data-stu-id="f693f-119">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
