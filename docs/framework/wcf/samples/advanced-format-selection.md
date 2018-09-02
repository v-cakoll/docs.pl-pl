---
title: Zaawansowane wybieranie formatu
ms.date: 03/30/2017
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
ms.openlocfilehash: e5c396ce22e9021d453a70f3826b0bd3cc6aaf42
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466626"
---
# <a name="advanced-format-selection"></a>Zaawansowane wybieranie formatu
Niniejszy przykład pokazuje, jak rozszerzyć w modelu programowania REST Windows Communication Foundation (WCF) do obsługi nowych wychodzących formatów odpowiedzi. Ponadto w przykładzie użyto szablon T4 do zwrócenia w odpowiedzi na stronie XHTML, prezentacja, jak można zaimplementować model programowania stylu widoku.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Przykład składa się z prostą usługę wraz z kodem klienta, który sprawia, że żądania do usługi.  Usługa obsługuje jednej operacji [WebGet], która ma następujący podpis metody: `Message EchoListWithGet(string list);`  
  
 Jeśli klient wysyła żądanie do usługi, udostępnia rozdzielaną przecinkami listę elementów z `list` parametr ciągu zapytania i usługa zwraca tę samą listę w jednym z następujących formatów: XML, JSON, Atom, XHTML lub jpeg.  
  
 Format odpowiedzi zwracanych przez usługę jest ustalana najpierw `format` parametr ciągu zapytania i sekundę przez dostarczony wraz z żądaniem nagłówek HTTP zaakceptować. Jeśli wartość `format` parametr ciągu zapytania jest jednym z formatów poprzedni, a następnie odpowiedź zostanie zwrócona w tym formacie. Jeśli `format` ciągu zapytania nie jest obecna, a następnie usługa wykonuje iterację przez elementy nagłówka Accept z żądania i zwraca format pierwszy typ zawartości, która obsługuje usługę.  
  
 Zwracany typ operacji jest warte odnotowania. REST usługi WCF, model programowania tylko natywnie obsługuje formaty odpowiedzi XML i JSON, gdy operacja zwraca typ inny niż <xref:System.ServiceModel.Channels.Message>. Jednakże korzystając z <xref:System.ServiceModel.Channels.Message> jako zwracany typ, deweloper ma pełną kontrolę nad jak sformatowana zawartość komunikatu.  
  
 W przykładzie użyto <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> i <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> metody służące do wykonywania serializacji listy ciągów do wiadomości XML, JSON i ATOM odpowiednio. W przypadku formatu odpowiedzi jpeg <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> metoda jest używana i obraz, który jest zapisywany do strumienia. Dla odpowiedzi XHTML <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> jest używana wraz ze wstępnie przetworzony szablon T4, który składa się z plikiem .tt i pliku .cs wygenerowany automatycznie. Plik .tt umożliwia deweloperom zapisu odpowiedzi w postaci szablonu, który zawiera zmienne i kontrolowanie struktury. Aby uzyskać więcej informacji o narzędziu T4, zobacz [generowania artefaktów, przy użyciu szablonów tekstowych](https://go.microsoft.com/fwlink/?LinkId=166023).  
  
 Przykład składa się z samodzielnie hostowana usługa i klient, który jest uruchamiany w ramach aplikacji konsoli. Po uruchomieniu aplikacji konsolowej klienta zgłasza żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi w oknie konsoli.  
  
#### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1.  Otwórz rozwiązanie dla przykładu zaawansowane wybór formatu. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator na potrzeby przykładu zostać pomyślnie uruchomiony. W tym celu kliknij prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonę i wybierając pozycję **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, Skompiluj rozwiązanie, a następnie naciśnij klawisz Ctrl-F5, aby uruchomić projekt AdvancedFormatSelection aplikacji konsoli bez debugowania. W oknie konsoli pojawia się i zawiera identyfikator URI uruchomioną usługę i identyfikator URI elementu HTML pomocy strony dla uruchomionej usługi.  
  
3.  Po uruchomieniu przykładu klient wysyła żądania do usługi i zapisuje odpowiedzi w oknie konsoli. Zwróć uwagę, różnych formatów odpowiedzi: XML, JSON, Atom i XHTML.  
  
4.  Są następnie wyświetlony monit, aby przejść do identyfikatora URI, w którym możesz poprosić o odpowiedzi w formacie JPEG. Otwórz przeglądarkę i przejdź do danego identyfikatora URI.  
  
5.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>Zobacz też
