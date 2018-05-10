---
title: Automatyczne wybieranie formatu
ms.date: 03/30/2017
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
ms.openlocfilehash: 8c26253bee069bf9bbc009ea219e6c12cab034ef
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="automatic-format-selection"></a>Automatyczne wybieranie formatu
W tym przykładzie pokazano, jak włączyć automatyczne wybieranie formatu (XML lub JSON) z resztą Windows Communication Foundation (WCF) programowania modelu, a także sposobu jawnie ustawić format w kodzie operacji.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Próbka składa się z usługą wraz z kodu klienta, który wysyła żądania do usługi. Usługa obsługuje jeden protokół HTTP `GET` operacji (`EchoWithGet`) i jeden HTTP `POST` operacji (`EchoWithPost`). Obie operacje oczekiwany ciąg, a następnie wróć ciąg w odpowiedzi. Z `GET` operacji ciąg znajduje się w parametr ciągu zapytania identyfikatora URI. Z `POST` operacji ciąg znajduje się w treści żądania serializacji w danych XML. Usługa jest w stanie zwracanie odpowiedzi w XML lub JSON przy użyciu nowego automatycznego wyboru formatu i formatu konieczne wybór funkcji w [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
 W przykładzie automatycznego wyboru formatu jest włączona, przy użyciu pliku App.config. Na domyślny punkt końcowy HTTP w sieci Web `automaticFormatSelectionEnabled` atrybutu została podana wartość `true`. W przypadku automatycznego wyboru formatu włączone infrastruktura WCF wybiera najbardziej odpowiedni format odpowiedzi (XML lub JSON) podane nagłówki HTTP Zaakceptuj lub typ zawartości żądania. Deweloper nie są wymagane do świadczenia dodatkowy kod ani konfiguracji innych niż ustawienie `automaticFormatSelectionEnabled` atrybutu `true` Aby użyć tej nowej funkcji. W kodzie klienta w pliku Program.cs żądania są wysyłane zarówno do `GET` i `POST` operacji usługi z określonego jako "application/xml" lub "application/json" nagłówka HTTP zaakceptować i zwraca odpowiedź w tym odpowiedni format.  
  
 Również w `GET` operacja, Wybieranie formatu konieczne jest używana. `GET` Operacja wyszukuje opcjonalny `format` parametr ciągu zapytania i jeśli jest obecny, określa format odpowiedzi na <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> właściwości. Imperatively ustawienie format odpowiedzi w ten sposób przesłania automatycznego wyboru formatu programach infrastruktura WCF.  
  
 Próbka składa się z własnym hostowana usługa i klient, który jest uruchamiany w ramach aplikacji konsoli. Podczas działania aplikacji konsoli, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie przykładowej automatycznego wyboru formatu. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator przykładowej może zostać pomyślnie uruchomiony. To zrobić, klikając prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikony, jak i wybierz **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B Skompiluj rozwiązanie, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić projekt AutomaticFormatSelection aplikacji konsoli. W oknie konsoli zostanie wyświetlony i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi.  
  
3.  Jak działa próbki, klient wysyła żądania do usługi i zapisuje odpowiedzi w oknie konsoli. Zwróć uwagę, formaty odpowiedzi w pliku XML i JSON.  
  
4.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>Zobacz też
