---
title: Nie można zapisać do pliku dziennika, ponieważ spowodowałoby przekroczenie wartości MaximumSize zapis do niego
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 28a4b9286b13f8c7c72c4e98871846c2ca265aa9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619799"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="aa5bc-102">Nie można zapisać do pliku dziennika, ponieważ spowodowałoby przekroczenie wartości MaximumSize zapis do niego</span><span class="sxs-lookup"><span data-stu-id="aa5bc-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>
<span data-ttu-id="aa5bc-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można zapisać do pliku dziennika, ponieważ:</span><span class="sxs-lookup"><span data-stu-id="aa5bc-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="aa5bc-104">Rozmiar pliku dziennika (w bajtach) jest większa niż wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> właściwości</span><span class="sxs-lookup"><span data-stu-id="aa5bc-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="aa5bc-105">— i —</span><span class="sxs-lookup"><span data-stu-id="aa5bc-105">—and—</span></span>  
  
- <span data-ttu-id="aa5bc-106">Wartość <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwość <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="aa5bc-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aa5bc-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="aa5bc-107">To correct this error</span></span>  
  
1. <span data-ttu-id="aa5bc-108">Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.</span><span class="sxs-lookup"><span data-stu-id="aa5bc-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="aa5bc-109">Zmień wartość właściwości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> właściwości, aby umożliwić większe dzienniki.</span><span class="sxs-lookup"><span data-stu-id="aa5bc-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3. <span data-ttu-id="aa5bc-110">Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> właściwości <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> do odrzucenia komunikaty bez ostrzeżenia, jeśli dziennik jest zbyt duży.</span><span class="sxs-lookup"><span data-stu-id="aa5bc-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa5bc-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa5bc-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="aa5bc-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="aa5bc-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="aa5bc-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="aa5bc-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
