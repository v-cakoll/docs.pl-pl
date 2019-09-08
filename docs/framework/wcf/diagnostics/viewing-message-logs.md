---
title: Wyświetlanie dzienników komunikatów
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: b0f35d4cca037e663c5c298103c4a8228bb16d52
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797304"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="3e16b-102">Wyświetlanie dzienników komunikatów</span><span class="sxs-lookup"><span data-stu-id="3e16b-102">Viewing Message Logs</span></span>
<span data-ttu-id="3e16b-103">W tym temacie opisano sposób wyświetlania dzienników komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3e16b-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="3e16b-104">Wyświetlanie dzienników komunikatów w przeglądarce śledzenia usługi</span><span class="sxs-lookup"><span data-stu-id="3e16b-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="3e16b-105">Komunikat zostanie przekształcony, ponieważ jest przetwarzany przez funkcję WCF.</span><span class="sxs-lookup"><span data-stu-id="3e16b-105">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="3e16b-106">W związku z tym rejestrowany komunikat odzwierciedla tylko zawartość komunikatu w punkcie, w którym została zarejestrowana, a nie zawartość w sieci.</span><span class="sxs-lookup"><span data-stu-id="3e16b-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="3e16b-107">Ponieważ dane wyjściowe rejestrowania komunikatów nie mają relacji z formatem transferu wiadomości, funkcja rejestrowania komunikatów zawsze wyświetla zdekodowany komunikat.</span><span class="sxs-lookup"><span data-stu-id="3e16b-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="3e16b-108">Jeśli skonfigurowano rejestrowanie komunikatów prawidłowo, każdy zarejestrowany komunikat powinien być w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="3e16b-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="3e16b-109">Na przykład format (zwykły tekst) rejestrowanych komunikatów nie ma wpływ na użycie kodera komunikatów binarnych.</span><span class="sxs-lookup"><span data-stu-id="3e16b-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="3e16b-110">Dane wyjściowe XmlWriterTraceListener to plik zawierający sekwencję fragmentów kodu XML.</span><span class="sxs-lookup"><span data-stu-id="3e16b-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="3e16b-111">Należy pamiętać, że plik nie jest prawidłowym plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="3e16b-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="3e16b-112">Zaleca się, aby wyświetlić pliki dziennika komunikatów za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="3e16b-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="3e16b-113">Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [Używanie przeglądarki śledzenia usługi do wyświetlania skorelowanych śladów i rozwiązywania problemów](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="3e16b-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="3e16b-114">W przeglądarce śledzenia usługi komunikaty są wyświetlane na karcie **wiadomość** . Komunikaty, które spowodowały lub są związane z, błędem przetwarzania są wyróżnione kolorem żółtym (poziom ostrzegawczy) lub czerwony (poziom błędu), w zależności od wagi błędu.</span><span class="sxs-lookup"><span data-stu-id="3e16b-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="3e16b-115">Dwukrotne kliknięcie komunikatu powoduje wyświetlenie śledzenia komunikatów w kontekście żądania przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="3e16b-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e16b-116">Jeśli komunikat nie ma nagłówka, żaden tag `<header/>` nie jest rejestrowany.</span><span class="sxs-lookup"><span data-stu-id="3e16b-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="3e16b-117">Wyświetlanie komunikatów zarejestrowanych przez klienta, przekaźnik i usługę</span><span class="sxs-lookup"><span data-stu-id="3e16b-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="3e16b-118">Środowisko może zawierać klienta, który wysyła komunikat do przekaźnika, który następnie przekazuje komunikat do usługi.</span><span class="sxs-lookup"><span data-stu-id="3e16b-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="3e16b-119">Gdy rejestrowanie komunikatów jest włączone we wszystkich trzech lokalizacjach, a wszystkie trzy dzienniki komunikatów są wyświetlane w [narzędziu Podgląd śledzenia usługi (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) jednocześnie, wymiany dzienników komunikatów będą nieprawidłowo renderowane.</span><span class="sxs-lookup"><span data-stu-id="3e16b-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="3e16b-120">Dzieje się tak, `CorrelationId` ponieważ `ActivityId` i w nagłówku wiadomości nie są unikatowe dla każdej pary wysyłania i odbierania.</span><span class="sxs-lookup"><span data-stu-id="3e16b-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="3e16b-121">Aby rozwiązać ten problem, można użyć jednej z poniższych metod.</span><span class="sxs-lookup"><span data-stu-id="3e16b-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
- <span data-ttu-id="3e16b-122">W każdej chwili należy wyświetlać dwa z trzech dzienników komunikatów w [narzędziu Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="3e16b-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
- <span data-ttu-id="3e16b-123">Jeśli konieczne jest wyświetlenie wszystkich trzech dzienników w [narzędziu Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) w tym samym czasie, można zmodyfikować usługę przekaźnika, tworząc nowe <xref:System.ServiceModel.Channels.Message> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="3e16b-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="3e16b-124">To wystąpienie powinno być kopią treści wiadomości przychodzącej oraz wszystkimi nagłówkami z wyjątkiem `ActivityId` nagłówków i. `Action`</span><span class="sxs-lookup"><span data-stu-id="3e16b-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="3e16b-125">Poniższy przykład kodu demonstruje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="3e16b-125">The following example code demonstrates how to do this.</span></span>  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="3e16b-126">Wyjątkowe przypadki dotyczące niedokładnej zawartości rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="3e16b-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="3e16b-127">W następujących warunkach rejestrowane komunikaty mogą nie być dokładną reprezentacją strumienia oktetów obecnego w sieci.</span><span class="sxs-lookup"><span data-stu-id="3e16b-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
- <span data-ttu-id="3e16b-128">W przypadku BasicHttpBinding nagłówki kopert są rejestrowane dla wiadomości przychodzących w przestrzeni nazw/Addressing/none.</span><span class="sxs-lookup"><span data-stu-id="3e16b-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
- <span data-ttu-id="3e16b-129">Białe znaki mogą być niezgodne.</span><span class="sxs-lookup"><span data-stu-id="3e16b-129">White spaces can be mismatched.</span></span>  
  
- <span data-ttu-id="3e16b-130">W przypadku wiadomości przychodzących puste elementy mogą być reprezentowane w różny sposób.</span><span class="sxs-lookup"><span data-stu-id="3e16b-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="3e16b-131">Na przykład \<tag >\</tag > zamiast \<znacznika/></span><span class="sxs-lookup"><span data-stu-id="3e16b-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
- <span data-ttu-id="3e16b-132">W przypadku wyłączenia znanego rejestrowania przez dane OSOBowe są domyślnie lub jawne ustawienie enableLoggingKnownPii = "true".</span><span class="sxs-lookup"><span data-stu-id="3e16b-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
- <span data-ttu-id="3e16b-133">Kodowanie jest włączone do przekształcania na UTF-8.</span><span class="sxs-lookup"><span data-stu-id="3e16b-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e16b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e16b-134">See also</span></span>

- [<span data-ttu-id="3e16b-135">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="3e16b-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="3e16b-136">Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="3e16b-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="3e16b-137">Rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="3e16b-137">Message Logging</span></span>](message-logging.md)
