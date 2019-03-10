---
title: Wielowątkowość w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cc7f358a62c8057abb77e1f5a28544bb6c858d98
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703325"
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="022d0-102">Wielowątkowość w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="022d0-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="022d0-103">W wielu aplikacjach możesz wprowadzić interfejsu użytkownika (UI) zwiększyć szybkość reakcji, wykonywanie operacji czasochłonne na inny wątek.</span><span class="sxs-lookup"><span data-stu-id="022d0-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="022d0-104">Wiele narzędzi dostępnych dla wielowątkowości formantów Windows Forms, w tym <xref:System.Threading> przestrzeni nazw, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody i `BackgroundWorker` składnika.</span><span class="sxs-lookup"><span data-stu-id="022d0-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="022d0-105">`BackgroundWorker` Składnika zastępuje i dodaje funkcjonalność do <xref:System.Threading> przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody; jednak te są przechowywane zarówno w przypadku zgodności z poprzednimi wersjami, jak i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="022d0-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="022d0-106">Aby uzyskać więcej informacji, zobacz [BackgroundWorker, składnik — omówienie](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="022d0-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="022d0-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="022d0-107">In This Section</span></span>  
 [<span data-ttu-id="022d0-108">Instrukcje: Bezpieczne wątkowo wywołania kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="022d0-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="022d0-109">Pokazuje, jak bezpieczne wątkowo wywołania kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="022d0-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="022d0-110">Instrukcje: Użycie wątku w tle do wyszukiwania plików</span><span class="sxs-lookup"><span data-stu-id="022d0-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="022d0-111">Ilustruje sposób używania <xref:System.Threading> przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A> metody należy szukać plików asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="022d0-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="022d0-112">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="022d0-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="022d0-113">Dokumenty składnika, który hermetyzuje wątku roboczego dla operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="022d0-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="022d0-114">Dokumentują sposób ładowanie dźwięku asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="022d0-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="022d0-115">Dokumenty, jak załadować obraz asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="022d0-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="022d0-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="022d0-116">Related Sections</span></span>  
 [<span data-ttu-id="022d0-117">Instrukcje: Uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="022d0-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="022d0-118">Pokazuje, jak wykonywać czasochłonne operację, podając <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="022d0-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="022d0-119">BackgroundWorker, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="022d0-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="022d0-120">Zawiera tematy, które opisują sposób używania <xref:System.ComponentModel.BackgroundWorker> składnika dla operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="022d0-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
