---
title: "Nie można uzyskać strumienia dla dziennika"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dba511ecd2a5c050fc2c037ac437e38715609e95
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="1590b-102">Nie można uzyskać strumienia dla dziennika</span><span class="sxs-lookup"><span data-stu-id="1590b-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="1590b-103">Nie można uzyskać strumienia dla dziennika.</span><span class="sxs-lookup"><span data-stu-id="1590b-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="1590b-104">Potencjalne nazwy plików oparte na \<name > są już używane.</span><span class="sxs-lookup"><span data-stu-id="1590b-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="1590b-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można utworzyć nowy plik dziennika, ponieważ wszystkie potencjalne nazwy plików dziennika na podstawie \<name > są już używane.</span><span class="sxs-lookup"><span data-stu-id="1590b-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="1590b-106">O zbyt wiele plików dziennika może wskazywać architektury problem z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="1590b-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="1590b-107">Zajrzyj do dokumentacji <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="1590b-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1590b-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1590b-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="1590b-109">Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> właściwości <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> lub <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> uwzględnienie sygnaturę daty w polu Nazwa pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="1590b-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="1590b-110">Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.</span><span class="sxs-lookup"><span data-stu-id="1590b-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1590b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1590b-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="1590b-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="1590b-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [<span data-ttu-id="1590b-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="1590b-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
