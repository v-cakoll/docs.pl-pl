---
title: Wyświetlanie dzienników komunikatów
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: f368d4f8f2a214feaa24b732513a99edf2e28296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603587"
---
# <a name="viewing-message-logs"></a>Wyświetlanie dzienników komunikatów
W tym temacie opisano, jak można wyświetlić dzienniki komunikatów.  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>Wyświetlanie komunikatu dzienniki w podglądzie śledzenia usług  
 Wiadomość zostanie przekształcona jest przetwarzany przez architekturę WCF. W związku z tym rejestrowane komunikat odzwierciedla tylko treści wiadomości w momencie zarejestrowania go, nie zawartość w sieci.  
  
 Ponieważ dane wyjściowe rejestrowanie komunikatów nie ma relacji z formatem transferu wiadomości, zawsze rejestrowania komunikatów generuje zdekodowany komunikat. Jeśli zostały skonfigurowane prawidłowo rejestrowanie komunikatów, wszystkie zarejestrowane komunikaty powinna być w postaci zwykłego tekstu. Na przykład format (zwykły tekst) zarejestrowane komunikaty, nie oddziałuje użycie kodera binarnego komunikatów.  
  
 Dane wyjściowe XmlWriterTraceListener jest plik, który zawiera sekwencję fragmenty XML. Należy pamiętać, że plik nie jest prawidłowym plikiem XML. Zaleca się, że używasz [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlania plików dziennika komunikatów. Aby uzyskać więcej informacji na temat używania tego narzędzia, zobacz [za pomocą przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów z](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 W podglądzie śledzenia usługi wiadomości są wymienione w **komunikat** kartę. Komunikaty, które spowodowały lub są związane, błąd przetwarzania są wyróżnione na żółto (poziom ostrzeżenia) lub czerwony (poziom błędu), w zależności od ważności błędu. Dwukrotne kliknięcie komunikatu, wywołuje śledzenie komunikatów w kontekście przetwarzania żądania.  
  
> [!NOTE]
>  Jeśli komunikat nie ma nagłówka, nie `<header/>` tag jest rejestrowane.  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>Wyświetl komunikaty zarejestrowane przez klienta, wystąpienie usługi Relay i usługi  
 Środowisko może zawierać klienta, który wysyła wiadomość do przekazywania, który następnie przekazuje komunikat do usługi. Gdy rejestrowanie komunikatów jest włączona na wszystkich trzech lokalizacji, a wszystkie trzy dzienników komunikatów są wyświetlane w [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) jednocześnie wymianę dziennik komunikatów będzie niepoprawnie renderowany. Jest to spowodowane `CorrelationId` i `ActivityId` w nagłówku komunikatu nie są unikatowe dla każdej pary send-receive.  
  
 Aby rozwiązać ten problem, można użyć jednego z następujących metod.  
  
-   Wyświetlać tylko dwa z trzech dzienników komunikatów w [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) w dowolnym momencie.  
  
-   Czy należy wyświetlać wszystkie trzy dzienniki w [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) w tym samym czasie można zmodyfikować usługi przekazywania przez utworzenie nowego <xref:System.ServiceModel.Channels.Message> wystąpienia. To wystąpienie powinno być kopią treści komunikatu przychodzącego, a także wszystkie nagłówki z wyjątkiem `ActivityId` i `Action` nagłówków. Poniższy przykład kodu pokazuje, jak to zrobić.  
  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>Wyjątkowych przypadkach komunikat niedokładne rejestrowanie zawartości  
 W następujących warunkach rejestrowane komunikaty mogą nie być dokładnie reprezentacja strumień oktetu się na łączu.  
  
-   Dla BasicHttpBinding, koperty nagłówki są rejestrowane dla przychodzących komunikatów w / adresowania/Brak przestrzeni nazw.  
  
-   Może się nie zgadzać białych znaków.  
  
-   Dla wiadomości przychodzących pustych elementów może być reprezentowany inaczej. Na przykład \<tagu >\</tagu > zamiast \<tagu / >  
  
-   Kiedy znane rejestrowanie dane osobowe jest wyłączone przez domyślne lub enableLoggingKnownPii jawne ustawienie = "true".  
  
-   Kodowanie jest włączona dla przekształcania w formacie UTF-8.  
  
## <a name="see-also"></a>Zobacz także
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)
