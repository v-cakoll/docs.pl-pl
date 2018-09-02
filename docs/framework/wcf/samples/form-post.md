---
title: Przesłanie formularza
ms.date: 03/30/2017
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
ms.openlocfilehash: 9115b9abfa7039bf409bb9bbce54e5012d05a074
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464937"
---
# <a name="form-post"></a>Przesłanie formularza
Niniejszy przykład pokazuje, jak rozszerzyć WCF modelu programowania interfejsu REST do obsługi nowych formatów żądania przychodzące. Przykład obejmuje również implementację element formatujący może wykonywać deserializację żądania post formularza HTML w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu. Ponadto w przykładzie użyto szablon T4, aby powrócić do strony HTML, co zapewnia formularza HTML, który użytkownicy będą publikować z powrotem do usługi REST programu WCF.  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Rozszerzanie obsługi formatów żądania przychodzące.  
  
-   Integrowanie szablony T4.  
  
## <a name="discussion"></a>Dyskusja  
 Ten przykład obejmuje dwa projekty. Jeden projekt jest biblioteką HtmlFormProcessing, która zawiera żądanie niestandardowe elementu formatującego, który może wykonywać deserializację wpisów formularza HTML w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów. Drugi projekt to aplikacja konsolowa która rozszerza przykładowe podstawowej usługi do zasobów do użycia elementu formatującego żądanie niestandardowe biblioteki HtmlFormProcessing.  
  
 Niestandardowy element formatujący, który może wykonywać deserializację wpisów formularza HTML (HtmlFormRequestDispatchFormatter) akceptuje zarówno [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, które mogą być konwertowane na ciąg, w którym używana jest <xref:System.ServiceModel.Dispatcher.QueryStringConverter> i typy oznaczone <xref:System.Runtime.Serialization.DataContractAttribute> mieć tylko elementy członkowskie, które mogą być przekonwertowana z na ciąg przy użyciu QueryStringConverter.  
  
 Abstrakcyjna klasa bazowa zawiera także projekt biblioteki HtmlFormProcessing `RequestBodyDispatchFormatter`, który może służyć do tworzenia innych żądanie niestandardowe elementy formatujące. Wyprowadzanie z `RequestBodyDispatchFormatter` umożliwia deweloperom skoncentrowanie się na logice deserializacji treści żądania, umożliwiający klasy bazowej do mapowania parametrów szablonu URI parametry metody wykonać operację. W bibliotece HtmlFormProcessing projektu jest również `HtmlFormProcessingBehavior` klasy, która pokazuje, jak dziedziczyć <xref:System.ServiceModel.Description.WebHttpBehavior> zastąpić domyślny element formatujący żądania żądanie niestandardowe elementu formatującego.  
  
 Ten projekt aplikacji konsoli rozszerza [podstawowej usługi do zasobu](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbki. Przykład podstawowe usługi zasobów pokazuje, jak udostępnić zasób w taki sposób, który używa modelu programowania interfejsu REST usługi WCF. W tym przykładzie podstawowej usługi do zasobu zasobu kolekcji klientów jest uwidaczniany w taki sposób, że klienci w kolekcji można tworzyć, pobierane, aktualizowane i usuwane. Przykład podstawowe usługi zasobów używa tylko dwa natywnie obsługiwanych przychodzące żądanie formaty, XML i JSON.  
  
 Korzysta z aplikacji konsoli w tym przykładzie Post formularza niestandardowego elementu formatującego w bibliotece HtmlFormProcessing umożliwia użytkownikom tworzenie klientów, wysyłając żądanie post formularza HTML w przeglądarce. Dodaje także operację, która zwraca stronę HTML, w tym formularzu wysyłany do usługi. Ta strona HTML jest generowana z użyciem wstępnie przetworzony szablon T4, który składa się z plikiem .tt i pliku .cs wygenerowany automatycznie. Plik .tt umożliwia deweloperom zapisu odpowiedzi w postaci szablonu, który zawiera zmienne i kontrolowanie struktury. Aby uzyskać więcej informacji o narzędziu T4, zobacz [generowania artefaktów, przy użyciu szablonów tekstowych](https://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie dla przykładu Post formularza. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator, aby pomyślnie wykonać próbki. W tym celu kliknij prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonę i wybierając pozycję "Uruchom jako Administrator", z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, Skompiluj rozwiązanie, a następnie naciśnij klawisz CTRL + F5, aby uruchomić projekt FormPost aplikacji konsoli.  
  
3.  W oknie konsoli pojawia się i zawiera identyfikator URI uruchomioną usługę i identyfikator URI elementu HTML pomocy strony dla uruchomionej usługi.  
  
4.  Po uruchomieniu przykładu klienta zapisuje stan bieżącego działania czy poprzez dodawanie jest klientem, klient aktualizowanie, usuwanie klienta lub pobieranie listy obecni klienci korzystający z usługi w oknie konsoli.  
  
5.  Następnie monit przejdź do identyfikatora URI klienta formularza. Otwórz przeglądarkę i przejdź do danego identyfikatora URI. Wpisz nazwę i adres klienta, a następnie kliknij przycisk **przesyłania** przycisku.  
  
6.  Naciśnij dowolny klawisz, okna konsoli kontynuować, działa aplikacja przykładowa.  
  
7.  Jako przykład zakończy, zwróć uwagę, że klienta, które zostały utworzone za pomocą przeglądarki znajduje się na ostatniej liście klientów.  
  
8.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
