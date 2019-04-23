---
title: Nie można zapisać do pliku dziennika, ponieważ zapisanie może spowodować zmniejszenie wolnego miejsca na dysku poniżej wartości ReservedSpace
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: 38cba8c01741196de9c316ed137acf750add9e89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308786"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="9bc46-102">Nie można zapisać do pliku dziennika, ponieważ zapisanie może spowodować zmniejszenie wolnego miejsca na dysku poniżej wartości ReservedSpace</span><span class="sxs-lookup"><span data-stu-id="9bc46-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>
<span data-ttu-id="9bc46-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można zapisać do pliku dziennika, ponieważ:</span><span class="sxs-lookup"><span data-stu-id="9bc46-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
-   <span data-ttu-id="9bc46-104">Ilość wolnego miejsca na dysku (w bajtach) jest mniejsza niż wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> właściwości</span><span class="sxs-lookup"><span data-stu-id="9bc46-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="9bc46-105">— i —</span><span class="sxs-lookup"><span data-stu-id="9bc46-105">—and—</span></span>  
  
-   <span data-ttu-id="9bc46-106">Wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwość <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="9bc46-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9bc46-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9bc46-107">To correct this error</span></span>  
  
1. <span data-ttu-id="9bc46-108">Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.</span><span class="sxs-lookup"><span data-stu-id="9bc46-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="9bc46-109">Zmień wartość właściwości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> właściwość mniejszą liczbę, aby zarezerwować mniej miejsca na dysku.</span><span class="sxs-lookup"><span data-stu-id="9bc46-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3. <span data-ttu-id="9bc46-110">Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwości <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> do odrzucenia komunikaty bez ostrzeżenia, jeśli nie ma wystarczającej ilości wolnego miejsca na dysku.</span><span class="sxs-lookup"><span data-stu-id="9bc46-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc46-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bc46-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="9bc46-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="9bc46-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="9bc46-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="9bc46-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
