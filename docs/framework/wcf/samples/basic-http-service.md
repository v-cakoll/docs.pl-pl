---
title: Podstawowa usługa HTTP
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 8dfcd5a751bcef6aa24b5cb4a200c8820c43fe81
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716102"
---
# <a name="basic-http-service"></a>Podstawowa usługa HTTP

W tym przykładzie pokazano, jak zaimplementować usługę opartą na protokole HTTP, która jest nazywana "POX" (zwykła stara usługa XML), korzystając z modelu programowania REST programu Windows Communication Foundation (WCF). Ten przykład składa się z dwóch składników: samodzielnej usługi HTTP WCF (Service.cs) i aplikacji konsolowej (Program.cs), która tworzy usługę i wysyła do niej wywołania.

## <a name="sample-details"></a>Przykładowe szczegóły

Usługa WCF uwidacznia 2 operacje, `EchoWithGet` i `EchoWithPost`, która zwraca ciąg, który został przekazano jako dane wejściowe.

`EchoWithGet` operacji jest adnotacja z <xref:System.ServiceModel.Web.WebGetAttribute>, co oznacza, że operacja przetwarza żądania HTTP `GET`. Ponieważ <xref:System.ServiceModel.Web.WebGetAttribute> nie określa jawnie <xref:System.UriTemplate>, Operacja oczekuje, że ciąg wejściowy zostanie przesłany przy użyciu parametru ciągu zapytania o nazwie `s`. Należy pamiętać, że format identyfikatora URI, którego oczekuje usługa, można dostosować za pomocą właściwości <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A>.

`EchoWithPost` operacji jest adnotacja z <xref:System.ServiceModel.Web.WebInvokeAttribute>, co oznacza, że nie jest to operacja `GET` (ma efekty uboczne). Ponieważ <xref:System.ServiceModel.Web.WebInvokeAttribute> nie określa jawnie `Method`, operacja przetwarza żądania `POST` HTTP, które zawierają ciąg w treści żądania (w formacie XML, na przykład). Należy pamiętać, że metoda HTTP i format identyfikatora URI dla żądania można dostosować odpowiednio przy użyciu właściwości <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> i <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate>.

Plik App. config konfiguruje usługę WCF przy użyciu domyślnej <xref:System.ServiceModel.Description.WebHttpEndpoint>, która ma właściwość <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> ustawioną na `true`. W efekcie Infrastruktura WCF tworzy stronę pomocy w języku HTML na `http://localhost:8000/Customers/help`, która zawiera informacje na temat sposobu konstruowania żądań HTTP do usługi i korzystania z odpowiedzi HTTP usługi.

Program.cs demonstruje, jak fabryka kanałów WCF może służyć do wykonywania wywołań do usługi i przetwarzania odpowiedzi. Należy pamiętać, że jest to tylko jeden sposób na dostęp do usługi WCF. Istnieje również możliwość uzyskiwania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak <xref:System.Net.HttpWebRequest> i <xref:System.Net.WebClient>.

Przykład składa się z samodzielnej usługi i klienta uruchamianego w aplikacji konsolowej. Gdy aplikacja konsolowa zostanie uruchomiona, klient wysyła żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi do okna konsoli.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Otwórz rozwiązanie dla przykładu podstawowej usługi http. Podczas uruchamiania programu Visual Studio 2012 należy uruchomić jako administrator, aby przykład mógł zostać pomyślnie wykonany. W tym celu kliknij prawym przyciskiem myszy ikonę programu Visual Studio 2012 i wybierz polecenie **Uruchom jako administrator** z menu kontekstowego.

2. Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie, a następnie naciśnij klawisze CTRL + F5, aby uruchomić aplikację konsolową bez debugowania. Zostanie wyświetlone okno konsoli z identyfikatorem URI uruchomionej usługi oraz identyfikatorem URI strony pomocy HTML dla działającej usługi. W dowolnym momencie możesz wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce. W miarę uruchamiania przykładu klient zapisuje stan bieżącego działania.

3. Naciśnij dowolny klawisz, aby zakończyć próbkę.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
