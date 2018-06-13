---
title: Nie można uzyskać strumienia dla dziennika
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 3f5ac83e6957d6d5883bf5ab191e2a922c874df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639541"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="ad850-102">Nie można uzyskać strumienia dla dziennika</span><span class="sxs-lookup"><span data-stu-id="ad850-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="ad850-103">Nie można uzyskać strumienia dla dziennika.</span><span class="sxs-lookup"><span data-stu-id="ad850-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="ad850-104">Potencjalne nazwy plików oparte na \<name > są już używane.</span><span class="sxs-lookup"><span data-stu-id="ad850-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="ad850-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można utworzyć nowy plik dziennika, ponieważ wszystkie potencjalne nazwy plików dziennika na podstawie \<name > są już używane.</span><span class="sxs-lookup"><span data-stu-id="ad850-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="ad850-106">O zbyt wiele plików dziennika może wskazywać architektury problem z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="ad850-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="ad850-107">Zajrzyj do dokumentacji <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ad850-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ad850-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ad850-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="ad850-109">Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> właściwości <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> lub <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> uwzględnienie sygnaturę daty w polu Nazwa pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="ad850-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="ad850-110">Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.</span><span class="sxs-lookup"><span data-stu-id="ad850-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad850-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad850-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="ad850-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="ad850-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [<span data-ttu-id="ad850-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="ad850-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
