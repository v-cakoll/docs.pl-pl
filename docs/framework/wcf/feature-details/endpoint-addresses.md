---
title: Adresy punktów końcowych
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: 71358ed1c16c3c9b490a41f74dd6319af8eb2e7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593532"
---
# <a name="endpoint-addresses"></a>Adresy punktów końcowych
Z każdym punktem końcowym jest skojarzony adres, który jest używany do lokalizowania i identyfikowania punktu końcowego. Ten adres składa się głównie z Uniform Resource Identifier (URI), który określa lokalizację punktu końcowego. Adres punktu końcowego jest reprezentowany w modelu programowania Windows Communication Foundation (WCF) przez <xref:System.ServiceModel.EndpointAddress> klasę, która zawiera opcjonalną właściwość, <xref:System.ServiceModel.EndpointAddress.Identity%2A> która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, które wymieniają z nim wiadomości, oraz zestaw opcjonalnych <xref:System.ServiceModel.EndpointAddress.Headers%2A> właściwości, które definiują wszystkie inne nagłówki protokołu SOAP wymagane do uzyskania dostępu do usługi. Opcjonalne nagłówki zapewniają dodatkowe i bardziej szczegółowe informacje dotyczące adresowania w celu identyfikowania punktu końcowego usługi lub korzystania z niego. Adres punktu końcowego jest reprezentowany w sieci jako odwołanie WS-Addressing punktu końcowego (EPR).  
  
## <a name="uri-structure-of-an-address"></a>Struktura identyfikatora URI adresu  
 Identyfikator URI adresu dla większości transportów ma cztery części. Na przykład cztery części identyfikatora URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` mogą być wyszczególnione w następujący sposób:  
  
- Równaniu`http:`
  
- Maszynie`www.fabrikam.com`  
  
- obowiązkowe Port: 322  
  
- Ścieżka:/mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Definiowanie adresu dla usługi  
 Adres punktu końcowego dla usługi można określić za pomocą kodu lub deklaratywnie za pośrednictwem konfiguracji. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi. Ogólnie rzecz biorąc, bardziej praktyczne jest zdefiniowanie punktów końcowych usługi przy użyciu konfiguracji zamiast kodu. Przechowywanie informacji o powiązaniach i adresowaniu poza kodem pozwala im zmieniać bez konieczności ponownego kompilowania lub wdrażania aplikacji.  
  
### <a name="defining-an-address-in-configuration"></a>Definiowanie adresu w konfiguracji  
 Aby zdefiniować punkt końcowy w pliku konfiguracji, użyj [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) elementu. Aby uzyskać szczegółowe informacje i przykład, zobacz [Określanie adresu punktu końcowego](../specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Definiowanie adresu w kodzie  
 Adres punktu końcowego można utworzyć w kodzie z <xref:System.ServiceModel.EndpointAddress> klasą. Aby uzyskać szczegółowe informacje i przykład, zobacz [Określanie adresu punktu końcowego](../specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>Punkty końcowe w języku WSDL  
 Adres punktu końcowego może być również reprezentowany w języku WSDL jako element EPR WS-Addressing wewnątrz odpowiedniego elementu punktu końcowego `wsdl:port` . EPR zawiera adres punktu końcowego, a także wszystkie właściwości adresu. Aby uzyskać szczegółowe informacje i przykład, zobacz [Określanie adresu punktu końcowego](../specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Obsługa wielu powiązań usług IIS w .NET Framework 3,5  
 Dostawcy usług internetowych często obsługują wiele aplikacji na tym samym serwerze i w każdej lokacji, aby zwiększyć gęstość lokacji i obniżyć całkowity koszt posiadania. Te aplikacje są zwykle powiązane z różnymi adresami podstawowymi. Witryna sieci Web programu Internet Information Services (IIS) może zawierać wiele aplikacji. Dostęp do aplikacji w lokacji można uzyskać za pomocą co najmniej jednego powiązania usług IIS.  
  
 Powiązania usług IIS udostępniają dwie informacje: Protokół powiązania i informacje o powiązaniu. Protokół powiązania definiuje schemat, w którym odbywa się komunikacja, a informacje o powiązaniu są informacjami używanymi do uzyskiwania dostępu do witryny.  
  
 W poniższym przykładzie przedstawiono składniki, które mogą być obecne w powiązaniu IIS:  
  
- Protokół powiązania: HTTP  
  
- Informacje o powiązaniu: adres IP, port, nagłówek hosta  
  
 Usługi IIS mogą określić wiele powiązań dla każdej lokacji, co skutkuje wieloma adresami podstawowymi dla każdego schematu. Przed .NET Framework 3,5 funkcja WCF nie obsługiwała wielu adresów schematu i, jeśli zostały określone, wywołała <xref:System.ArgumentException> podczas aktywacji.  
  
 .NET Framework 3,5 umożliwia dostawcom usług internetowych hostowanie wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.  
  
 Na przykład lokacja może zawierać następujące adresy podstawowe:  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 W .NET Framework 3,5 należy określić filtr prefiksu na poziomie domeny w pliku konfiguracji. Można to zrobić za pomocą [\<baseAddressPrefixFilters>](../../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) elementu, który zawiera listę prefiksów. Przychodzące adresy podstawowe, dostarczane przez usługi IIS, są filtrowane na podstawie opcjonalnej listy prefiksów. Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przesyłane przez. Określenie prefiksu spowoduje przekazanie tylko pasującego adresu podstawowego dla tego schematu.  
  
 Poniżej znajduje się przykładowy kod konfiguracji, który używa filtrów prefiksu.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 W poprzednim przykładzie `net.tcp://payroll.myorg.com:8000` i `http://shipping.myorg.com:8000` są jedynymi adresami podstawowymi dla odpowiednich schematów, które są przenoszone przez.  
  
 Program nie `baseAddressPrefixFilter` obsługuje symboli wieloznacznych.  
  
 Adresy podstawowe podane przez usługi IIS mogą mieć adresy powiązane z innymi schematami nieobecnymi na `baseAddressPrefixFilters` liście. Te adresy nie są odfiltrowane.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Obsługa wielu powiązań usług IIS w .NET Framework 4 i nowszych  
 Począwszy od platformy .NET 4, można włączyć obsługę wielu powiązań w usługach IIS bez konieczności wybierania pojedynczego adresu podstawowego przez ustawienie ustawienia <xref:System.ServiceModel.ServiceHostingEnvironment> <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> na wartość true. Ta obsługa jest ograniczona do schematów protokołu HTTP.  
  
 Poniżej znajduje się przykładowy kod konfiguracji, który używa multipleSiteBindingsEnabled na [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) .  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Wszystkie ustawienia baseAddressPrefixFilters są ignorowane dla protokołów HTTP i innych niż HTTP, gdy w ramach tego ustawienia włączono wiele powiązań witryny.  
  
 Aby uzyskać szczegółowe informacje i przykłady, zobacz [Obsługa wielu powiązań witryny usług IIS](supporting-multiple-iis-site-bindings.md) i <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> .  
  
## <a name="extending-addressing-in-wcf-services"></a>Rozszerzanie adresów w usługach WCF  
 Domyślny model adresowania usług WCF używa identyfikatora URI adresu punktu końcowego w następujących celach:  
  
- Aby określić adres nasłuchiwania usługi, lokalizacja, w której punkt końcowy nasłuchuje komunikatów,  
  
- Aby określić filtr adresów protokołu SOAP, adres punktu końcowego jest oczekiwany jako nagłówek protokołu SOAP.  
  
 Wartości dla każdego z tych celów można określić oddzielnie, zezwalając na kilka rozszerzeń adresów, które obejmują przydatne scenariusze:  
  
- Pośrednik protokołu SOAP: komunikat wysyłany przez klienta przechodzi przez jedną lub więcej dodatkowych usług, które przetwarzają komunikat, zanim osiągnie on ostateczną lokalizację docelową. Pośrednicy protokołu SOAP mogą wykonywać różne zadania, takie jak buforowanie, routing, równoważenie obciążenia lub sprawdzanie poprawności schematu dla komunikatów. Ten scenariusz jest realizowany przez wysyłanie komunikatów do oddzielnego adresu fizycznego ( `via` ), który jest przeznaczony dla pośredników, a nie tylko do adresu logicznego ( `wsa:To` ), który jest przeznaczony dla ostatecznej lokalizacji docelowej.  
  
- Adres nasłuchiwania punktu końcowego jest prywatnym identyfikatorem URI i ma ustawioną inną wartość niż jego `listenURI` Właściwość.  
  
 Adres transportu określony przez program `via` to lokalizacja, do której należy początkowo wysłać komunikat w sposób do innego adresu zdalnego określonego przez `to` parametr, w którym znajduje się usługa. W większości scenariuszy internetowych `via` Identyfikator URI jest taki sam jak <xref:System.ServiceModel.EndpointAddress.Uri%2A> Właściwość końcowego `to` adresu usługi. Rozróżniane są tylko te dwa adresy, gdy konieczne jest ręczne rozsyłanie.  
  
### <a name="addressing-headers"></a>Nagłówki adresów  
 Punkt końcowy może być rozkierowany przy użyciu co najmniej jednego nagłówka SOAP oprócz podstawowego identyfikatora URI. Jednym z zestawów scenariuszy, w których jest to przydatne, jest zestaw scenariuszy pośrednich protokołu SOAP, w których punkt końcowy wymaga od klientów tego punktu końcowego dołączenia nagłówków protokołu SOAP przeznaczonych dla pośredników.  
  
 Niestandardowe nagłówki adresów można definiować na dwa sposoby — przy użyciu kodu lub konfiguracji:  
  
- W obszarze kod Utwórz niestandardowe nagłówki adresów przy użyciu <xref:System.ServiceModel.Channels.AddressHeader> klasy, a następnie używane w konstruowaniu obiektu <xref:System.ServiceModel.EndpointAddress> .  
  
- W obszarze Konfiguracja niestandardowe [\<headers>](../../configure-apps/file-schema/wcf/headers.md) są określone jako elementy podrzędne [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu.  
  
 Konfiguracja jest zwykle preferowana w kodzie, ponieważ pozwala na zmianę nagłówków po wdrożeniu.  
  
### <a name="custom-listening-addresses"></a>Niestandardowe adresy nasłuchiwania  
 Adres nasłuchiwania można ustawić na inną wartość niż identyfikator URI punktu końcowego. Jest to przydatne w scenariuszach pośrednich, w których adres protokołu SOAP, który ma być narażony, jest publicznym pośrednikiem protokołu SOAP, natomiast adres, na który faktycznie nasłuchuje punkt końcowy, jest prywatnym adresem sieciowym.  
  
 Możesz określić niestandardowy adres nasłuchiwania przy użyciu kodu lub konfiguracji:  
  
- W polu kod Określ niestandardowy adres nasłuchiwania poprzez dodanie <xref:System.ServiceModel.Description.ClientViaBehavior> klasy do kolekcji zachowań punktu końcowego.  
  
- W obszarze Konfiguracja Określ niestandardowy adres nasłuchiwania z `ListenUri` atrybutem elementu usługi [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) .  
  
### <a name="custom-soap-address-filter"></a>Niestandardowy filtr adresów SOAP  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A>Jest używany w połączeniu z dowolną <xref:System.ServiceModel.EndpointAddress.Headers%2A> właściwością do definiowania filtru adresów protokołu SOAP punktu końcowego ( <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ). Domyślnie ten filtr sprawdza, czy komunikat przychodzący ma `To` nagłówek komunikatu, który odpowiada identyfikatorowi URI punktu końcowego i czy wszystkie wymagane nagłówki punktów końcowych znajdują się w komunikacie.  
  
 W niektórych scenariuszach punkt końcowy odbiera wszystkie komunikaty, które docierają do podstawowego transportu, a nie tylko te z odpowiednim `To` nagłówkiem. Aby włączyć tę funkcję, użytkownik może użyć <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> klasy.  
  
## <a name="see-also"></a>Zobacz też

- [Określanie adresu punktu końcowego](../specifying-an-endpoint-address.md)
- [Uwierzytelnianie i tożsamość usług](service-identity-and-authentication.md)
