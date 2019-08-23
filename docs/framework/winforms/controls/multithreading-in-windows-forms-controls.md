---
title: Wielowątkowość w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952686"
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="71176-102">Wielowątkowość w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="71176-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="71176-103">W wielu aplikacjach można zwiększyć czas odpowiedzi interfejsu użytkownika, wykonując operacje czasochłonne na innym wątku.</span><span class="sxs-lookup"><span data-stu-id="71176-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="71176-104">Dostępnych jest wiele narzędzi do wielowątkowości formantów Windows Forms, takich jak <xref:System.Threading> przestrzeń nazw <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> , Metoda i `BackgroundWorker` składnik.</span><span class="sxs-lookup"><span data-stu-id="71176-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71176-105">Składnik zastępuje i dodaje funkcje <xref:System.Threading> do przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metodę, jednak są one zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. `BackgroundWorker`</span><span class="sxs-lookup"><span data-stu-id="71176-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="71176-106">Aby uzyskać więcej informacji, zobacz [Omówienie składnika BackgroundWorker](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="71176-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71176-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="71176-107">In This Section</span></span>  
 [<span data-ttu-id="71176-108">Instrukcje: Ustaw bezpieczne dla wątków wywołania formantów Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71176-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="71176-109">Pokazuje, w jaki sposób zapewnić bezpieczne wątki do formantów Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="71176-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="71176-110">Instrukcje: Użyj wątku w tle do wyszukiwania plików</span><span class="sxs-lookup"><span data-stu-id="71176-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="71176-111">Pokazuje, jak używać <xref:System.Threading> przestrzeni nazw <xref:System.Windows.Forms.Control.BeginInvoke%2A> i metody do wyszukiwania plików asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="71176-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="71176-112">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="71176-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="71176-113">Dokumentuje składnik, który hermetyzuje wątek roboczy dla operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="71176-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="71176-114">Dokumenty, jak załadować dźwięk asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="71176-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="71176-115">Dokumenty, jak asynchronicznie ładować obraz.</span><span class="sxs-lookup"><span data-stu-id="71176-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="71176-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="71176-116">Related Sections</span></span>  
 [<span data-ttu-id="71176-117">Instrukcje: Uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="71176-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="71176-118">Pokazuje, jak wykonać czasochłonną operację za pomocą <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="71176-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="71176-119">BackgroundWorker, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="71176-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="71176-120">Zawiera tematy opisujące, jak używać <xref:System.ComponentModel.BackgroundWorker> składnika dla operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="71176-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
