---
title: Aplikacje interfejsu wielu dokumentów (MDI)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0ce7c66946d03d566b21473711cb6b3315885236
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61952051"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="cb245-102">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="cb245-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="cb245-103">Aplikacje interfejsu wielu dokumentów (MDI) umożliwiają wyświetlanie wiele dokumentów w tym samym czasie za pomocą każdy dokument wyświetlany w osobnym oknie.</span><span class="sxs-lookup"><span data-stu-id="cb245-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="cb245-104">Aplikacje MDI często mają element menu Okno oraz podmenu do przełączania się między systemem windows lub dokumenty.</span><span class="sxs-lookup"><span data-stu-id="cb245-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb245-105">Istnieją pewne różnice zachowanie między formularze MDI i interfejsu pojedynczego dokumentu (SDI) systemu windows w formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cb245-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="cb245-106">`Opacity` Właściwość nie ma wpływu na wygląd formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="cb245-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="cb245-107">Ponadto <xref:System.Windows.Forms.Form.CenterToParent%2A> metoda nie ma wpływu na zachowanie formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="cb245-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb245-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cb245-108">In This Section</span></span>  
 [<span data-ttu-id="cb245-109">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="cb245-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="cb245-110">Zawiera wskazówki dotyczące tworzenia kontenera dla wielu dokumentów w aplikacji MDI.</span><span class="sxs-lookup"><span data-stu-id="cb245-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="cb245-111">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="cb245-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="cb245-112">Zawiera wskazówki dotyczące tworzenia co najmniej systemu windows, które działają w ramach formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="cb245-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="cb245-113">Instrukcje: Określanie elementu podrzędnego Active MDI</span><span class="sxs-lookup"><span data-stu-id="cb245-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="cb245-114">Zawiera wskazówki dotyczące weryfikacji okna podrzędnego, który ma fokus (i wysyła jego zawartość do Schowka).</span><span class="sxs-lookup"><span data-stu-id="cb245-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="cb245-115">Instrukcje: Wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="cb245-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="cb245-116">Zawiera wskazówki dotyczące transportowania informacji do okna podrzędnego active.</span><span class="sxs-lookup"><span data-stu-id="cb245-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="cb245-117">Instrukcje: Aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="cb245-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="cb245-118">Zawiera wskazówki dla fragmentacji, kaskadowych lub rozmieszczanie okien podrzędnych MDI aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb245-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
