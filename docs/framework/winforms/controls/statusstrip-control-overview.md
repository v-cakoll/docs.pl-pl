---
title: StatusStrip — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: 9356ca85003987eabf4f62a25acad45d73e144fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627242"
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="a0063-102">StatusStrip — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="a0063-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="a0063-103">A <xref:System.Windows.Forms.StatusStrip> kontrolka Wyświetla informacje dotyczące obiektu są wyświetlane na <xref:System.Windows.Forms.Form>, składniki obiektu lub informacji kontekstowych, które odnoszą się do tego obiektu operacji w ramach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0063-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="a0063-104">Zazwyczaj <xref:System.Windows.Forms.StatusStrip> kontrola składa się z <xref:System.Windows.Forms.ToolStripStatusLabel> obiektów, z których każda wyświetla tekst i/lub ikonę.</span><span class="sxs-lookup"><span data-stu-id="a0063-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="a0063-105"><xref:System.Windows.Forms.StatusStrip> Może również zawierać <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, i <xref:System.Windows.Forms.ToolStripProgressBar> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a0063-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="a0063-106">Wartość domyślna <xref:System.Windows.Forms.StatusStrip> ma nie paneli.</span><span class="sxs-lookup"><span data-stu-id="a0063-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="a0063-107">Aby dodać zespoły do <xref:System.Windows.Forms.StatusStrip>, użyj <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a0063-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a0063-108">Brak rozbudowana Obsługa obsługi <xref:System.Windows.Forms.StatusStrip> elementów i Typowe polecenia w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0063-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="a0063-109">Zobacz też [StatusStrip — Edytor kolekcji elementów](https://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip — okno dialogowe zadania](https://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="a0063-109">Also see [StatusStrip Items Collection Editor](https://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](https://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="a0063-110">Mimo że <xref:System.Windows.Forms.StatusStrip> zastępuje i rozszerza <xref:System.Windows.Forms.StatusBar> kontrolki z poprzednich wersji <xref:System.Windows.Forms.StatusBar> został zachowany na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości wybranie opcji.</span><span class="sxs-lookup"><span data-stu-id="a0063-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="a0063-111">StatusStrip — ważne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a0063-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="a0063-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a0063-112">Name</span></span>|<span data-ttu-id="a0063-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a0063-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="a0063-114">Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.StatusStrip> obsługuje przepełnienie funkcji.</span><span class="sxs-lookup"><span data-stu-id="a0063-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="a0063-115">Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.StatusStrip> odcinkach od końca do końca w jego <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="a0063-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="a0063-116">Klasy ważne pomocnika StatusStrip</span><span class="sxs-lookup"><span data-stu-id="a0063-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="a0063-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a0063-117">Name</span></span>|<span data-ttu-id="a0063-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a0063-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="a0063-119">Reprezentuje panelu w <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="a0063-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="a0063-120">Wyświetla skojarzoną <xref:System.Windows.Forms.ToolStripDropDown> z którego użytkownik może wybrać jeden element.</span><span class="sxs-lookup"><span data-stu-id="a0063-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="a0063-121">Reprezentuje kontrolkę legalną dwuczęściową przycisk standardowy i menu rozwijanego.</span><span class="sxs-lookup"><span data-stu-id="a0063-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="a0063-122">Wyświetla stan ukończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="a0063-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0063-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0063-123">See also</span></span>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
