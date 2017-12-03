---
title: "Wyświetlanie dzienników komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df1d796ec5009008e00391eea2987f5256df6c48
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="viewing-message-logs"></a>Wyświetlanie dzienników komunikatów
W tym temacie opisano sposób wyświetlania dzienników komunikatów.  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>Wyświetlanie komunikatów dzienniki w podglądzie śledzenia usługi  
 Zostanie on przekształcony komunikat jest przetwarzany przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. W związku z tym rejestrowany komunikat odzwierciedla tylko treści wiadomości w momencie zarejestrowania go, nie zawartości w sieci.  
  
 Ponieważ dane wyjściowe rejestrowania komunikatów nie ma relacji do formatu transferu wiadomości, zawsze rejestrowania komunikatów generuje dekodowane wiadomości. Jeśli zostały skonfigurowane prawidłowo rejestrowanie komunikatów, wszelkie zarejestrowany komunikat należy w postaci zwykłego tekstu. Na przykład format (zwykły tekst) zarejestrowane komunikaty, nie ma wpływu na użycie binarnego kodera wiadomości.  
  
 Dane wyjściowe XmlWriterTraceListener jest plik, który zawiera sekwencję fragmenty XML. Należy pamiętać, że plik nie jest prawidłowym plikiem XML. Zaleca się, że używasz [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlania plików dziennika komunikatów. Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [przy użyciu przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 W podglądzie śledzenia usługi, komunikaty są wyświetlane w **komunikat** kartę. Komunikaty, które spowodowały lub które są związane z, błąd przetwarzania są wyróżnione żółty (poziom ostrzeżenia) albo czerwony (poziom błędu), w zależności od ważności błędu. Dwukrotne kliknięcie komunikatu powoduje wyświetlenie komunikatów śledzenia w kontekście przetwarzania żądania.  
  
> [!NOTE]
>  Jeśli komunikat nie ma nagłówka, nie `<header/>` tag jest rejestrowane.  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>Wyświetlanie informacji zarejestrowanych przez klienta, przekazywania i usługi  
 W środowisku może znajdować się klienta, który wysyła komunikat do przekazywania, który następnie przekazuje komunikat do usługi. Jeśli rejestrowanie komunikatów jest włączona na wszystkich trzech lokalizacji, a wszystkie trzy dzienniki wiadomości są wyświetlane w [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) jednocześnie, wymiany komunikatów dziennika są nieprawidłowo wyświetlane. Jest to spowodowane `CorrelationId` i `ActivityId` w nagłówku wiadomości nie są unikatowe dla każdej pary send-receive.  
  
 Jedną z następujących metod służy do rozwiązania tego problemu.  
  
-   Tylko wyświetlić dwie z trzech dzienników wiadomości w [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) w dowolnym momencie.  
  
-   Jeśli należy wyświetlić wszystkie trzy dzienniki w [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) w tym samym czasie, można zmodyfikować usługi przekazywania przez utworzenie nowej <xref:System.ServiceModel.Channels.Message> wystąpienia. To wystąpienie powinno być kopią treści komunikatu przychodzącego, a także wszystkich nagłówków z wyjątkiem `ActivityId` i `Action` nagłówków. Poniższy przykład kodu pokazuje, jak to zrobić.  
  
```  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>Wyjątki dla zawartości rejestrowania komunikatów niedokładne  
 W następujących warunkach komunikaty są rejestrowane może nie być dokładnie reprezentację strumień oktetu obecny umieszczonego w.  
  
-   Dla klasy BasicHttpBinding, koperty nagłówki są rejestrowane na komunikaty przychodzące w / adresowania/Brak przestrzeni nazw.  
  
-   Mogą być niezgodne białe znaki.  
  
-   Dla komunikatów przychodzących pustych elementów może być reprezentowany inaczej. Na przykład \<tag >\</tagu > zamiast \<tagu / >  
  
-   Gdy rejestrowanie znanych danych osobowych jest wyłączone przez domyślne lub enableLoggingKnownPii jawne ustawienie = "true".  
  
-   Kodowanie jest włączona dla transformacji UTF-8.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Przy użyciu przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)
