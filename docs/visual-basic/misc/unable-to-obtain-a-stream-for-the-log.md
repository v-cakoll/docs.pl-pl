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
ms.openlocfilehash: dd3051b2331502c9f4f3430bbf88731b307d1b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="ef5b0-102">Nie można uzyskać strumienia dla dziennika</span><span class="sxs-lookup"><span data-stu-id="ef5b0-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="ef5b0-103">Nie można uzyskać strumienia dla dziennika.</span><span class="sxs-lookup"><span data-stu-id="ef5b0-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="ef5b0-104">Potencjalne nazwy plików oparte na \<name > są już używane.</span><span class="sxs-lookup"><span data-stu-id="ef5b0-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="ef5b0-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Klasy nie można utworzyć nowy plik dziennika, ponieważ wszystkie potencjalne nazwy plików dziennika na podstawie \<name > są już używane.</span><span class="sxs-lookup"><span data-stu-id="ef5b0-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="ef5b0-106">O zbyt wiele plików dziennika może wskazywać architektury problem z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="ef5b0-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="ef5b0-107">Zajrzyj do dokumentacji <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ef5b0-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ef5b0-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ef5b0-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="ef5b0-109">Ustaw <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> właściwości <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> lub <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> uwzględnienie sygnaturę daty w polu Nazwa pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="ef5b0-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="ef5b0-110">Archiwizowanie istniejące dzienniki i usuń je z komputera, aby umożliwić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> obiekt, aby utworzyć nowe dzienniki.</span><span class="sxs-lookup"><span data-stu-id="ef5b0-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5b0-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef5b0-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="ef5b0-112">My.Application.log — obiekt</span><span class="sxs-lookup"><span data-stu-id="ef5b0-112">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="ef5b0-113">My.log — obiekt</span><span class="sxs-lookup"><span data-stu-id="ef5b0-113">My.Log Object</span></span>](../../visual-basic/language-reference/objects/my-log-object.md)
