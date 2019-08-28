---
title: Podstawowa usługa HTTP
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: ec716b41efb3dde6e5afdb386d797e402d924b56
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045159"
---
# <a name="basic-http-service"></a>Podstawowa usługa HTTP

W tym przykładzie pokazano, jak zaimplementować usługę opartą na protokole HTTP, która jest nazywana "POX" (zwykła stara usługa XML), korzystając z modelu programowania REST programu Windows Communication Foundation (WCF). Ten przykład składa się z dwóch składników: samodzielnej usługi HTTP WCF (Service.cs) i aplikacji konsolowej (Program.cs), która tworzy usługę i wysyła do niej wywołania.

## <a name="sample-details"></a>Przykładowe szczegóły

Usługa WCF ujawnia dwie operacje `EchoWithGet` i `EchoWithPost`, która zwraca ciąg, który został przekazano jako dane wejściowe.

Operacja jest oznaczona adnotacją <xref:System.ServiceModel.Web.WebGetAttribute>, co oznacza, że operacja przetwarza żądania HTTP `GET`. `EchoWithGet` Ponieważ nie określa jawnie, Operacja oczekuje, że ciąg wejściowy zostanie przekazana przy użyciu parametru ciągu zapytania o nazwie `s`. <xref:System.UriTemplate> <xref:System.ServiceModel.Web.WebGetAttribute> Należy pamiętać, że format identyfikatora URI, którego oczekuje usługa, można dostosować przy użyciu <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> właściwości.

Operacja jest oznaczona adnotacją <xref:System.ServiceModel.Web.WebInvokeAttribute>, co `GET` oznacza, że nie jest operacją (ma efekty uboczne). `EchoWithPost` Ponieważ nie określa jawnie, operacja przetwarza żądania HTTP `POST` , które zawierają ciąg w treści żądania (na przykład w formacie XML. `Method` <xref:System.ServiceModel.Web.WebInvokeAttribute> Należy pamiętać, że metoda HTTP i format identyfikatora URI dla żądania można dostosować odpowiednio przy użyciu <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości i. <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate>

Plik App. config konfiguruje usługę WCF z wartością domyślną <xref:System.ServiceModel.Description.WebHttpEndpoint> , która <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> ma ustawioną `true`właściwość. W efekcie Infrastruktura WCF tworzy automatycznie opartą na języku HTML stronę `http://localhost:8000/Customers/help` pomocy, która zawiera informacje na temat sposobu konstruowania żądań HTTP do usługi i korzystania z odpowiedzi HTTP usługi.

Program.cs demonstruje, jak fabryka kanałów WCF może służyć do wykonywania wywołań do usługi i przetwarzania odpowiedzi. Należy pamiętać, że jest to tylko jeden sposób na dostęp do usługi WCF. Istnieje również możliwość uzyskiwania dostępu do usługi przy użyciu innych klas .NET Framework, <xref:System.Net.HttpWebRequest> takich <xref:System.Net.WebClient>jak i.

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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
