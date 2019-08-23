---
title: Aplikacje interfejsu wielu dokumentów (MDI)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 23e0275d5e6b081ec02d669a78e8695453360637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956559"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="b1d87-102">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="b1d87-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="b1d87-103">Aplikacje interfejsu wielu dokumentów (MDI) umożliwiają wyświetlanie wielu dokumentów w tym samym czasie, przy czym każdy dokument jest wyświetlany w osobnym oknie.</span><span class="sxs-lookup"><span data-stu-id="b1d87-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="b1d87-104">Aplikacje MDI często mają element menu okna z podmenumi do przełączania między oknami lub dokumentami.</span><span class="sxs-lookup"><span data-stu-id="b1d87-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1d87-105">Istnieją pewne różnice w zachowaniu między formularzami MDI i oknami interfejsu jednostronicowego (SDI) w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b1d87-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="b1d87-106">`Opacity` Właściwość nie ma wpływu na wygląd formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="b1d87-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="b1d87-107"><xref:System.Windows.Forms.Form.CenterToParent%2A> Ponadto metoda nie wpływa na zachowanie formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="b1d87-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1d87-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b1d87-108">In This Section</span></span>  
 [<span data-ttu-id="b1d87-109">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="b1d87-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="b1d87-110">Zawiera wskazówki dotyczące tworzenia kontenera dla wielu dokumentów w aplikacji MDI.</span><span class="sxs-lookup"><span data-stu-id="b1d87-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="b1d87-111">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="b1d87-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="b1d87-112">Zawiera wskazówki dotyczące tworzenia jednego lub kilku okien, które działają w ramach formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="b1d87-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="b1d87-113">Instrukcje: Określanie aktywnego elementu podrzędnego MDI</span><span class="sxs-lookup"><span data-stu-id="b1d87-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="b1d87-114">Zawiera wskazówki dotyczące weryfikowania okna podrzędnego z fokusem (i wysyłania jego zawartości do schowka).</span><span class="sxs-lookup"><span data-stu-id="b1d87-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="b1d87-115">Instrukcje: Wyślij dane do aktywnego elementu podrzędnego MDI</span><span class="sxs-lookup"><span data-stu-id="b1d87-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="b1d87-116">Zawiera wskazówki dotyczące transportowania informacji do aktywnego okna podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b1d87-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="b1d87-117">Instrukcje: Rozmieść formularze podrzędne MDI</span><span class="sxs-lookup"><span data-stu-id="b1d87-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="b1d87-118">Oferuje wskazówki dotyczące dzielenia, kaskadowania lub rozmieszczania podrzędnych okien aplikacji MDI.</span><span class="sxs-lookup"><span data-stu-id="b1d87-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
