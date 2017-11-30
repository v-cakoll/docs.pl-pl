---
title: "Nie można zapisać do pliku dziennika, ponieważ zapisanie może spowodować zmniejszenie wolnego miejsca na dysku poniżej wartości ReservedSpace"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0adc3438a9473885022e9785c5381f8da0b6f303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="50d7e-102">Nie można zapisać do pliku dziennika, ponieważ zapisanie może spowodować zmniejszenie wolnego miejsca na dysku poniżej wartości ReservedSpace</span><span class="sxs-lookup"><span data-stu-id="50d7e-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>
<span data-ttu-id="50d7e-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można zapisać do pliku dziennika, ponieważ:</span><span class="sxs-lookup"><span data-stu-id="50d7e-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
-   <span data-ttu-id="50d7e-104">Ilość wolnego miejsca na dysku (w bajtach) jest mniejsza niż wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> właściwości</span><span class="sxs-lookup"><span data-stu-id="50d7e-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="50d7e-105">- i -</span><span class="sxs-lookup"><span data-stu-id="50d7e-105">—and—</span></span>  
  
-   <span data-ttu-id="50d7e-106">Wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwość <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="50d7e-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="50d7e-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="50d7e-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="50d7e-108">Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.</span><span class="sxs-lookup"><span data-stu-id="50d7e-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2.  <span data-ttu-id="50d7e-109">Zmień wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> właściwości mniejszą liczbę do zarezerwowania mniej miejsca na dysku.</span><span class="sxs-lookup"><span data-stu-id="50d7e-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3.  <span data-ttu-id="50d7e-110">Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwości <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> odrzucić wiadomości bez ostrzeżenia, jeśli nie ma wystarczającej ilości wolnego miejsca na dysku.</span><span class="sxs-lookup"><span data-stu-id="50d7e-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d7e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50d7e-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 [<span data-ttu-id="50d7e-112">My.Application.log — obiekt</span><span class="sxs-lookup"><span data-stu-id="50d7e-112">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="50d7e-113">My.log — obiekt</span><span class="sxs-lookup"><span data-stu-id="50d7e-113">My.Log Object</span></span>](../../visual-basic/language-reference/objects/my-log-object.md)
