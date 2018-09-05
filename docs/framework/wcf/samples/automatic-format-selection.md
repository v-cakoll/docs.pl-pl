---
title: Automatyczne wybieranie formatu
ms.date: 03/30/2017
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
ms.openlocfilehash: 4fd695195f5c7c13bc088248a6b3c12388328d37
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659764"
---
# <a name="automatic-format-selection"></a>Automatyczne wybieranie formatu
W tym przykładzie pokazano, jak włączyć automatyczne wybieranie formatu (XML lub JSON) z użyciem usług REST Windows Communication Foundation (WCF), programowania modelu, a także jak jawnie ustawić format w kodzie operacji.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Przykład składa się z usługi wraz z kodem klienta, który sprawia, że żądania do usługi. Usługa obsługuje pojedynczy HTTP `GET` operacji (`EchoWithGet`) i jednego HTTP `POST` operacji (`EchoWithPost`). Obie operacje oczekiwany ciąg, a następnie wróć ciągu w odpowiedzi. Za pomocą `GET` operacji, ciąg jest podawany jako parametr ciągu zapytania identyfikatora URI. Za pomocą `POST` operacji ciągu znajduje się w treści żądania, serializowane w kodzie XML. Usługa jest w stanie do zwracania odpowiedzi XML lub JSON, wykorzystując nowe automatyczne wybieranie formatu i format imperatywne wybór funkcji w [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
 W tym przykładzie automatyczne wybieranie formatu jest włączona, przy użyciu pliku App.config. Na domyślny punkt końcowy protokołu HTTP sieci Web `automaticFormatSelectionEnabled` atrybut ma wartość `true`. W przypadku automatyczne wybieranie formatu włączone infrastruktura WCF wybiera najbardziej odpowiedni format odpowiedzi (XML lub JSON) podane nagłówki HTTP Zaakceptuj lub Content-Type żądania. Deweloper nie jest wymagane do zapewnienia dodatkowego kodu ani konfiguracji innych niż ustawienie `automaticFormatSelectionEnabled` atrybutu `true` do korzystania z nowej funkcji. W kodzie klienta w pliku Program.cs, są wysyłane żądania na wartość oba `GET` i `POST` operacje usługi przy użyciu nagłówka HTTP zaakceptować, określony jako "application/xml" lub "application/json" i zwraca odpowiedź w tym odpowiedni format.  
  
 Również w `GET` operacja, imperatywne Formatuj zaznaczenie jest używana. `GET` Operacji sprawdza, czy opcjonalny `format` parametr ciągu zapytania, a jeśli jest obecny, ustawia format odpowiedzi na <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> właściwości. Obowiązkowo ustawienie formatu odpowiedzi w ten sposób zastąpienia automatyczne wybieranie formatu wykonywane przez infrastrukturę usługi WCF.  
  
 Przykład składa się z samodzielnie hostowana usługa i klient, który jest uruchamiany w ramach aplikacji konsoli. Po uruchomieniu aplikacji konsolowej klienta zgłasza żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi w oknie konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie dla automatycznego przykładu wybór formatu. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator na potrzeby przykładu zostać pomyślnie uruchomiony. W tym celu kliknij prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonę i wybierz pozycję **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, Skompiluj rozwiązanie, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić projekt AutomaticFormatSelection aplikacji konsoli. W oknie konsoli pojawia się i zawiera identyfikator URI uruchomioną usługę i identyfikator URI elementu HTML pomocy strony dla uruchomionej usługi.  
  
3.  Po uruchomieniu przykładu klient wysyła żądania do usługi i zapisuje odpowiedzi w oknie konsoli. Zwróć uwagę, różne formaty odpowiedzi w XML i JSON.  
  
4.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>Zobacz też
