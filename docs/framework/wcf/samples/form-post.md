---
title: "Przesłanie formularza"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe1be9177f3e811a3037377360f46f42904d5af3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="form-post"></a>Przesłanie formularza
W tym przykładzie pokazano, jak rozszerzyć WCF modelu programowania INTERFEJSU REST do obsługi nowych formatów żądania przychodzące. Przykład obejmuje również implementacja element formatujący może zdeserializować żądania post formularza HTML do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu. Ponadto próbki używa szablonu T4, aby powrócić do strony HTML, który zapewnia formularza HTML, który użytkownicy mogą post do usługi WCF REST.  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Rozszerzanie obsługa formatów żądania przychodzące.  
  
-   Integrowanie szablony T4.  
  
## <a name="discussion"></a>Omówienie  
 Ten przykład zawiera dwa projekty. Jeden projekt jest biblioteki HtmlFormProcessing, która zawiera elementu formatującego żądanie niestandardowego, który może deserializować wpisów formularza HTML do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów. Drugi projekt jest aplikacja konsolowa, która rozszerza próbki podstawowej usługi zasobów do użycia programu formatującego żądanie niestandardowe biblioteki HtmlFormProcessing.  
  
 Niestandardowy element formatujący, który może deserializować wpisów formularza HTML (HtmlFormRequestDispatchFormatter) akceptuje zarówno [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, które można przekonwertować ciągu używającego <xref:System.ServiceModel.Dispatcher.QueryStringConverter> i typów oznaczonych <xref:System.Runtime.Serialization.DataContractAttribute> mieć tylko elementy członkowskie, które mogą być przekonwertowany z ciągu przy użyciu QueryStringConverter.  
  
 Abstrakcyjna klasa podstawowa zawiera również projektu biblioteki HtmlFormProcessing `RequestBodyDispatchFormatter`, które mogą służyć do tworzenia innych żądanie niestandardowe elementy formatujące. Wyprowadzanie z `RequestBodyDispatchFormatter` umożliwia deweloperom skoncentrować się na logice deserializacji treści żądania, dzięki czemu klasy podstawowej do mapowania parametrów szablonu URI parametry metody wykonać operację. Również w bibliotece HtmlFormProcessing projektu jest `HtmlFormProcessingBehavior` klasy, która ilustruje sposób pochodzi od <xref:System.ServiceModel.Description.WebHttpBehavior> należy zastąpić domyślny element formatujący żądania elementu formatującego żądanie niestandardowe.  
  
 Ten projekt aplikacji konsoli rozszerza [podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbki. Przykład podstawowe usługi zasobów pokazano, jak udostępnianie zasobów w taki sposób, który używa modelu programowania INTERFEJSU REST usługi WCF. Na przykład podstawowe usługi zasobów zasobu kolekcji klienta jest uwidoczniony tak, aby klienci w kolekcji można tworzyć, pobrać, aktualizowane i usuwane. Przykład podstawowe usługi zasobów używa tylko dwa natywnie obsługiwane przychodzące żądanie formaty, XML i JSON.  
  
 Niestandardowy element formatujący w bibliotece HtmlFormProcessing, co pozwala użytkownikom na tworzenie klientów, wysyłając żądanie post formularza HTML za pomocą przeglądarki sieci korzysta z aplikacji konsoli w tym przykładzie Post formularza. Dodano również operację, która zwraca stronę HTML, w tym formularzu do ponownego zaksięgowania usługi. Ta strona HTML jest generowany przy użyciu wstępnie przetworzonych szablonu T4, który składa się z plikiem .TT — i plik CS wygenerowany automatycznie. Plik .TT — umożliwia deweloperom zapisu odpowiedzi w formularzu szablonu, który zawiera zmienne i kontrolowanie struktury. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]T4, zobacz [generowania artefaktów przez przy użyciu szablonów tekstowych](http://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie przykładowej Post formularza. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator, aby pomyślnie wykonać próbki. To zrobić, klikając prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonę i wybierając polecenie "Uruchom jako Administrator" z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B Skompiluj rozwiązanie, a następnie naciśnij klawisz CTRL + F5, aby uruchomić projekt FormPost aplikacji konsoli.  
  
3.  W oknie konsoli zostanie wyświetlony i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi.  
  
4.  Podczas działania próbki, klient zapisuje stan bieżącego działania czy jego dodawane klienta i aktualizacji klienta, usunięcie klienta lub pobrania listy bieżącego klientów z usługi w oknie konsoli.  
  
5.  Monit następnie przejdź do identyfikatora URI w postaci klienta. Otwórz przeglądarkę i przejdź do danego identyfikatora URI. Wpisz nazwę i adres dla tego klienta i kliknij przycisk **przesyłania** przycisku.  
  
6.  Naciśnij dowolny klawisz okna konsoli kontynuować wykonywanie przykładowej.  
  
7.  Jako przykład zakończeniu Zwróć uwagę, że klienta, które zostały utworzone za pomocą przeglądarki jest uwzględniony na liście końcowego klientów.  
  
8.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
