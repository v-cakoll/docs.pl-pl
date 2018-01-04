---
title: "Wielowątkowość w formantach formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="bd7ba-102">Wielowątkowość w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bd7ba-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="bd7ba-103">W wielu aplikacjach możesz wprowadzić interfejsu użytkownika (UI) poprawę reakcji, wykonując czas operacji w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="bd7ba-104">Wiele narzędzi dostępnych dla wielowątkowości formantów formularzy systemu Windows, w tym <xref:System.Threading> przestrzeni nazw, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody i `BackgroundWorker` składnika.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd7ba-105">`BackgroundWorker` Składnika zastępuje i dodaje funkcje do <xref:System.Threading> przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody, jednak te pozostają dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="bd7ba-106">Aby uzyskać więcej informacji, zobacz [BackgroundWorker — informacje o składniku](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bd7ba-106">For more information, see [BackgroundWorker Component Overview](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd7ba-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bd7ba-107">In This Section</span></span>  
 [<span data-ttu-id="bd7ba-108">Instrukcje: bezpieczne wątkowo wywołania kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bd7ba-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="bd7ba-109">Pokazuje, jak nawiązać bezpieczne wątkowo wywołania formantów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="bd7ba-110">Instrukcje: użycie wątku w tle do wyszukiwania plików</span><span class="sxs-lookup"><span data-stu-id="bd7ba-110">How to: Use a Background Thread to Search for Files</span></span>](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="bd7ba-111">Przedstawia sposób użycia <xref:System.Threading> przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A> metody do wyszukiwania plików asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bd7ba-112">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="bd7ba-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="bd7ba-113">Dokumenty składnik, który hermetyzuje wątku roboczego dla operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="bd7ba-114">Dokumenty jak ładowanie dźwięku asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="bd7ba-115">Omówiono sposób asynchronicznie ładowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bd7ba-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bd7ba-116">Related Sections</span></span>  
 [<span data-ttu-id="bd7ba-117">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="bd7ba-117">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="bd7ba-118">Pokazuje, jak wykonać czasochłonna operacja z <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="bd7ba-119">BackgroundWorker, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="bd7ba-119">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="bd7ba-120">Udostępnia tematy, które opisują sposób użycia <xref:System.ComponentModel.BackgroundWorker> składnika dla operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="bd7ba-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
