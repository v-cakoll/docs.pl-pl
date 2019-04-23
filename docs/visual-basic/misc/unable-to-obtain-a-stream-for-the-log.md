---
title: Nie można uzyskać strumień dziennika
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 540ff3fbba72d33b2efaa58ad7a8019628f5e83f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344757"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="55719-102">Nie można uzyskać strumień dziennika</span><span class="sxs-lookup"><span data-stu-id="55719-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="55719-103">Nie można uzyskać strumienia dziennika.</span><span class="sxs-lookup"><span data-stu-id="55719-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="55719-104">Potencjalne nazwy plików na podstawie \<name > jest już w użyciu.</span><span class="sxs-lookup"><span data-stu-id="55719-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="55719-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można utworzyć nowy plik dziennika, ponieważ wszystkie potencjalne nazwy plików dziennika na podstawie \<name > jest już w użyciu.</span><span class="sxs-lookup"><span data-stu-id="55719-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="55719-106">Masz zbyt wiele plików dziennika może wskazywać architektury problem z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="55719-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="55719-107">Zobacz dokumentację <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="55719-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="55719-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="55719-108">To correct this error</span></span>  
  
1. <span data-ttu-id="55719-109">Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> właściwości <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> lub <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> obejmujący sygnatura daty w nazwie pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="55719-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2. <span data-ttu-id="55719-110">Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.</span><span class="sxs-lookup"><span data-stu-id="55719-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55719-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55719-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="55719-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="55719-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="55719-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="55719-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
