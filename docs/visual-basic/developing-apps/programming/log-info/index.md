---
title: Rejestrowanie informacji z aplikacji
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: 43738b2d654435532a98654cbc40af134d43f02c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410026"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="c403b-102">Rejestrowanie informacji z aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c403b-102">Logging Information from the Application (Visual Basic)</span></span>

<span data-ttu-id="c403b-103">Ta sekcja zawiera tematy, które opisują, jak rejestrować informacje z aplikacji przy `My.Application.Log` użyciu `My.Log` obiektu lub i jak zwiększyć możliwości rejestrowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c403b-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="c403b-104">`Log`Obiekt zawiera metody zapisywania informacji w detektorach dzienników aplikacji, a `Log` Właściwość zaawansowana obiektu `TraceSource` zawiera szczegółowe informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c403b-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="c403b-105">`Log`Obiekt jest konfigurowany przez plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c403b-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="c403b-106">`My.Log`Obiekt jest dostępny tylko dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c403b-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="c403b-107">W przypadku aplikacji klienckich Użyj programu `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="c403b-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="c403b-108">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="c403b-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="c403b-109">Zadania</span><span class="sxs-lookup"><span data-stu-id="c403b-109">Tasks</span></span>  
  
|<span data-ttu-id="c403b-110">Do</span><span class="sxs-lookup"><span data-stu-id="c403b-110">To</span></span>|<span data-ttu-id="c403b-111">Zobacz</span><span class="sxs-lookup"><span data-stu-id="c403b-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="c403b-112">Zapisz informacje o zdarzeniu w dziennikach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c403b-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="c403b-113">Instrukcje: zapisywanie komunikatów dziennika</span><span class="sxs-lookup"><span data-stu-id="c403b-113">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)|  
|<span data-ttu-id="c403b-114">Zapisz informacje o wyjątkach w dziennikach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c403b-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="c403b-115">Instrukcje: rejestrowanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="c403b-115">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)|  
|<span data-ttu-id="c403b-116">Zapisuj informacje o śledzeniu do dzienników aplikacji podczas uruchamiania i zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c403b-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="c403b-117">Instrukcje: rejestrowanie komunikatów podczas uruchamiania lub zamykania aplikacji</span><span class="sxs-lookup"><span data-stu-id="c403b-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="c403b-118">Skonfiguruj `My.Application.Log` , aby zapisywać informacje w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="c403b-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="c403b-119">Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym</span><span class="sxs-lookup"><span data-stu-id="c403b-119">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="c403b-120">Skonfiguruj `My.Application.Log` , aby zapisywać informacje w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c403b-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="c403b-121">Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="c403b-121">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="c403b-122">Zmień miejsce `My.Application.Log` zapisu informacji.</span><span class="sxs-lookup"><span data-stu-id="c403b-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="c403b-123">Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="c403b-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="c403b-124">Określ, gdzie są `My.Application.Log` zapisywane informacje.</span><span class="sxs-lookup"><span data-stu-id="c403b-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="c403b-125">Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="c403b-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="c403b-126">Utwórz odbiornik dziennika niestandardowego dla programu `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="c403b-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="c403b-127">Przewodnik: tworzenie odbiorców dzienników niestandardowych</span><span class="sxs-lookup"><span data-stu-id="c403b-127">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="c403b-128">Filtrowanie danych wyjściowych `My.Application.Log` dzienników.</span><span class="sxs-lookup"><span data-stu-id="c403b-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="c403b-129">Przewodnik: filtrowanie danych wyjściowych elementu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="c403b-129">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c403b-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c403b-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="c403b-131">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="c403b-131">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="c403b-132">Rozwiązywanie problemów: odbiorcy dzienników</span><span class="sxs-lookup"><span data-stu-id="c403b-132">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
