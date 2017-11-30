---
title: Rejestrowanie informacji z aplikacji (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e52aaf4c26b4fa60ee04d7df6aa96980ebbf491
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="6d144-102">Rejestrowanie informacji z aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d144-102">Logging Information from the Application (Visual Basic)</span></span>
<span data-ttu-id="6d144-103">Ta sekcja zawiera tematy, które opisano, jak rejestrowanie informacji z swojej aplikacji za pomocą `My.Application.Log` lub `My.Log` obiekt i jak rozszerzyć możliwości rejestrowania zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d144-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="6d144-104">`Log` Obiektu zapewnia metody zapisywanie informacji o aplikacji odbiorniki dzienników i `Log` zaawansowane obiektu `TraceSource` właściwości przedstawia informacje szczegółowe.</span><span class="sxs-lookup"><span data-stu-id="6d144-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="6d144-105">`Log` Obiekt został skonfigurowany w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d144-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="6d144-106">`My.Log` Obiekt jest dostępny tylko dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6d144-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="6d144-107">Dla aplikacji klienckich, należy użyć `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="6d144-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="6d144-108">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="6d144-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="6d144-109">Zadania</span><span class="sxs-lookup"><span data-stu-id="6d144-109">Tasks</span></span>  
  
|<span data-ttu-id="6d144-110">Do</span><span class="sxs-lookup"><span data-stu-id="6d144-110">To</span></span>|<span data-ttu-id="6d144-111">Zobacz</span><span class="sxs-lookup"><span data-stu-id="6d144-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="6d144-112">Zapisywanie informacji o zdarzeniach Dzienniki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d144-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="6d144-113">Porady: zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="6d144-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="6d144-114">Zapisuje informacje o wyjątku do dzienników aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d144-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="6d144-115">Porady: wyjątki rejestru</span><span class="sxs-lookup"><span data-stu-id="6d144-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="6d144-116">Zapisania informacji o śledzeniu w dziennikach aplikacji, podczas uruchamiania i wyłączania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d144-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="6d144-117">Porady: Rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji</span><span class="sxs-lookup"><span data-stu-id="6d144-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="6d144-118">Skonfiguruj `My.Application.Log` mogła zapisać informacji do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="6d144-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="6d144-119">Porady: zapisywanie informacji o pliku tekstowego zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="6d144-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="6d144-120">Skonfiguruj `My.Application.Log` mogła zapisać informacji do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6d144-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="6d144-121">Porady: zapisywanie w rejestrze zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="6d144-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="6d144-122">Gdzie zmienić `My.Application.Log` zapisuje informacje.</span><span class="sxs-lookup"><span data-stu-id="6d144-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="6d144-123">Wskazówki: Zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="6d144-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="6d144-124">Określenie miejsca `My.Application.Log` zapisuje informacje.</span><span class="sxs-lookup"><span data-stu-id="6d144-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="6d144-125">Wskazówki: Ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="6d144-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="6d144-126">Utwórz odbiornik dziennik niestandardowy dla `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="6d144-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="6d144-127">Wskazówki: Tworzenie odbiorników logu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="6d144-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="6d144-128">Filtruj dane wyjściowe z `My.Application.Log` dzienniki.</span><span class="sxs-lookup"><span data-stu-id="6d144-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="6d144-129">Wskazówki: Filtrowanie danych wyjściowych My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="6d144-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="6d144-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d144-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="6d144-131">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="6d144-131">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="6d144-132">Rozwiązywanie problemów: Odbiorniki logu</span><span class="sxs-lookup"><span data-stu-id="6d144-132">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
