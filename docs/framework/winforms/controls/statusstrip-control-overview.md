---
title: "StatusStrip — Informacje o formancie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d1eb698dbb9168bf5de6d3982e19e69d170ac0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="f475d-102">StatusStrip — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="f475d-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="f475d-103">A <xref:System.Windows.Forms.StatusStrip> kontroli Wyświetla informacje o przeglądanym na obiekt <xref:System.Windows.Forms.Form>, składniki obiektu lub informacje kontekstowe, które odnoszą się do tego obiektu operacji w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f475d-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="f475d-104">Zazwyczaj <xref:System.Windows.Forms.StatusStrip> kontrola składa się z <xref:System.Windows.Forms.ToolStripStatusLabel> obiektów, z których każdy zawiera tekst i ikony.</span><span class="sxs-lookup"><span data-stu-id="f475d-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="f475d-105"><xref:System.Windows.Forms.StatusStrip> Może również zawierać <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, i <xref:System.Windows.Forms.ToolStripProgressBar> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f475d-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="f475d-106">Wartość domyślna <xref:System.Windows.Forms.StatusStrip> ma nie paneli.</span><span class="sxs-lookup"><span data-stu-id="f475d-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="f475d-107">Aby dodać paneli <xref:System.Windows.Forms.StatusStrip>, użyj <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f475d-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f475d-108">Brak kompleksową obsługę Obsługa <xref:System.Windows.Forms.StatusStrip> elementów i Typowe polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f475d-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="f475d-109">Zobacz też [edytora kolekcji elementy StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [okno dialogowe zadania StatusStrip](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f475d-109">Also see [StatusStrip Items Collection Editor](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="f475d-110">Mimo że <xref:System.Windows.Forms.StatusStrip> zastępuje i rozszerza <xref:System.Windows.Forms.StatusBar> kontrolę nad poprzednie wersje <xref:System.Windows.Forms.StatusBar> są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="f475d-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="f475d-111">Elementy członkowskie ważne StatusStrip</span><span class="sxs-lookup"><span data-stu-id="f475d-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="f475d-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f475d-112">Name</span></span>|<span data-ttu-id="f475d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f475d-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="f475d-114">Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.StatusStrip> obsługuje przepełnienie funkcji.</span><span class="sxs-lookup"><span data-stu-id="f475d-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="f475d-115">Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.StatusStrip> odcinkach od końca do końca w jego <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="f475d-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="f475d-116">Klasy ważnym dodatkiem StatusStrip</span><span class="sxs-lookup"><span data-stu-id="f475d-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="f475d-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f475d-117">Name</span></span>|<span data-ttu-id="f475d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f475d-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="f475d-119">Reprezentuje panelu w <xref:System.Windows.Forms.StatusStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="f475d-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="f475d-120">Wyświetla skojarzony <xref:System.Windows.Forms.ToolStripDropDown> z którego użytkownik może wybrać jeden element.</span><span class="sxs-lookup"><span data-stu-id="f475d-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="f475d-121">Reprezentuje kontrolkę dwóch części, która jest przycisk standardowy i menu rozwijanego.</span><span class="sxs-lookup"><span data-stu-id="f475d-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="f475d-122">Wyświetla stan ukończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="f475d-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f475d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f475d-123">See Also</span></span>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
