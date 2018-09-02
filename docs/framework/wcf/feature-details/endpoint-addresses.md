---
title: Adresy punktów końcowych
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: cc81e7ad45c308f5ecf476641dfd65fe47b36098
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404570"
---
# <a name="endpoint-addresses"></a>Adresy punktów końcowych
Każdy punkt końcowy ma adres skojarzony z nim, który jest używany, aby zlokalizować i zidentyfikować punkt końcowy. Ten adres składa się przede wszystkim z zasobów identyfikator URI (Uniform), który określa położenie punktu końcowego. Adres punktu końcowego jest reprezentowana w modelu programowania Windows Communication Foundation (WCF) przez <xref:System.ServiceModel.EndpointAddress> klasy, która zawiera opcjonalny <xref:System.ServiceModel.EndpointAddress.Identity%2A> właściwość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiany wiadomości z nim i zestaw opcjonalne <xref:System.ServiceModel.EndpointAddress.Headers%2A> właściwości, które definiują innych nagłówków protokołu SOAP, wymagane w celu dotarcia do usługi. Opcjonalne nagłówki zapewnić dodatkowe i bardziej szczegółowe informacje dotyczące adresowania do identyfikacji lub interakcji z punktu końcowego usługi. Adres punktu końcowego jest reprezentowany w sieci jako odwołanie WS-Addressing punktu końcowego (EPR).  
  
## <a name="uri-structure-of-an-address"></a>Identyfikator URI struktury adresu  
 Adres URI dla większości transportu ma cztery części. Na przykład czterech części identyfikatora URI http://www.fabrikam.com:322/mathservice.svc/secureEndpoint może być wyszczególnione w następujący sposób:  
  
-   Schemat: http:  
  
-   Maszyny: `www.fabrikam.com`  
  
-   (opcjonalnie) Port: 322  
  
-   Path: /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Definiowanie adres usługi  
 Adres punktu końcowego usługi można określić obowiązkowo za pomocą kodu lub deklaratywne za pomocą konfiguracji. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie sporządzana. Ogólnie rzecz biorąc lepiej jest punkty końcowe usługi przy użyciu konfiguracji zamiast kodu. Zachowanie powiązania i adresowanie z kodu pozwala zmienić bez konieczności ponownego kompilowania lub ponownego wdrażania aplikacji.  
  
### <a name="defining-an-address-in-configuration"></a>Definiowanie adresu w konfiguracji  
 Aby zdefiniować punkt końcowy w pliku konfiguracji, należy użyć [ \<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu. Aby uzyskać szczegółowe informacje i obejrzeć przykład, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Definiowanie adresu w kodzie  
 Adres punktu końcowego można utworzyć w kodzie za pomocą <xref:System.ServiceModel.EndpointAddress> klasy. Aby uzyskać szczegółowe informacje i obejrzeć przykład, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>Punkty końcowe w formacie WSDL  
 Adres punktu końcowego również może być reprezentowany w języku WSDL jako elementu WS-Addressing EPR wewnątrz odpowiedni punkt końcowy `wsdl:port` elementu. EPR zawiera adres punktu końcowego oraz wszelkie właściwości adresu. Aby uzyskać szczegółowe informacje i obejrzeć przykład, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Wiele usług IIS, powiązanie pomocy technicznej w programie .NET Framework 3.5  
 Usługodawcy internetowi często hostować wiele aplikacji na tym samym serwerze i lokacji zwiększenie gęstości lokacji i niższy całkowity koszt posiadania. Te aplikacje zwykle są powiązane z różnymi adresami podstawowej. Witrynę sieci Web usług Internet Information Services (IIS) może zawierać wiele aplikacji. Aplikacje w lokacji jest możliwy za pośrednictwem jednego lub więcej powiązań usług IIS.  
  
 Powiązania usługi IIS zapewniają dwóch rodzajów informacji: Protokół powiązania, a informacje o powiązaniu. Protokół powiązania definiuje schemat, przez który dane są przesyłane, a informacje o powiązaniu informacji używanych do uzyskiwania dostępu do witryny.  
  
 Poniższy przykład przedstawia składniki, które mogą być obecne w powiązaniu usługi IIS:  
  
-   Protokół powiązania: HTTP  
  
-   Informacje o powiązaniu: Adres IP, portu i nagłówka hosta  
  
 Usługi IIS można określić wiele powiązań dla każdej lokacji, co skutkuje z wieloma adresami podstawowymi dla każdego schematu. Przed [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], WCF nie obsługują wielu adresów dla schematu i, jeśli zostały określone, zgłosił <xref:System.ArgumentException> podczas aktywacji.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Umożliwia usługodawców internetowych do hostowania wielu aplikacji przy użyciu różnych adresami podstawowymi dla tego samego schematu w tej samej lokacji.  
  
 Na przykład lokacji może zawierać następujące adresy podstawowy:  
  
-   http://payroll.myorg.com/Service.svc  
  
-   http://shipping.myorg.com/Service.svc  
  
 Za pomocą [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], określić filtr prefiksu na poziomie elementu AppDomain w pliku konfiguracji. W tym z [ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) element, który zawiera listę prefiksów. Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane w oparciu o listę prefiksów opcjonalne. Domyślnie jeśli prefiks, który nie jest określony, wszystkie adresy są przekazywane za pośrednictwem. Określenie prefiksu wyniki w tylko pasujących adres podstawowy dla tego schematu, które zostaną przekazane za pośrednictwem.  
  
 Oto przykład kodu konfiguracji, który używa filtry prefiks.  
  
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
  
 W powyższym przykładzie net.tcp://payroll.myorg.com: 8000 i http://shipping.myorg.com:8000 są tylko podstawowy adres, ich systemów, które są przekazywane.  
  
 `baseAddressPrefixFilter` Nie obsługuje symboli wieloznacznych.  
  
 Adres podstawowy, dostarczone przez usługi IIS wiążące adresy powiązany z innych systemów, które nie znajduje się w `baseAddressPrefixFilters` listy. Te adresy nie są odfiltrowywane.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Usługi IIS powiązanie obsługi wielu w programie .NET Framework 4 lub nowszy  
 Począwszy od .NET 4, zostanie włączona obsługa wielu powiązań w usługach IIS bez konieczności pobrania pojedynczy adres podstawowy, ustawiając <xref:System.ServiceModel.ServiceHostingEnvironment>firmy <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> ustawienie na wartość true. Ta obsługa jest ograniczona do schematy protokołu HTTP.  
  
 Oto przykład kodu konfiguracji, który używa multipleSiteBindingsEnabled na [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Wszystkie ustawienia baseAddressPrefixFilters są ignorowane, zarówno dla protokołu HTTP i protokołów innych niż HTTP, po włączeniu wielu powiązań witryny przy użyciu tego ustawienia.  
  
 Aby uzyskać szczegółowe informacje i przykłady, zobacz [Obsługa wielu powiązań witryny usług IIS](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) i <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.  
  
## <a name="extending-addressing-in-wcf-services"></a>Rozszerzanie adresowania w usługach WCF  
 Domyślne adresowania modelu usług WCF używa adres URI punktu końcowego w następujących celach:  
  
-   Aby określić usługi adresu nasłuchiwania, lokalizacji, w jakim punkt końcowy będzie nasłuchiwać pod kątem wiadomości,  
  
-   Aby określić filtr adresu protokołu SOAP, adres punktu końcowego oczekuje jako nagłówek SOAP.  
  
 Wartości dla każdej z tych celów można określić osobno, dzięki czemu kilka rozszerzeń adresowania tego obejmują scenariusze przydatne:  
  
-   Pośredników SOAP: wiadomości wysłane przez klienta przechodzi przez jeden lub więcej dodatkowych usług, które przetworzyć komunikatu przed osiągnięciem przez nią miejsca przeznaczenia. Pośredników SOAP można wykonywać różne zadania, takie jak weryfikacja buforowania, routingu, równoważenia obciążenia lub schemat dla wiadomości. W tym scenariuszu odbywa się przez wysyłanie komunikatów do osobnych adresów fizycznych (`via`) który jest przeznaczony dla pośrednie, a nie po prostu adres logiczny (`wsa:To`) który jest przeznaczony dla docelowego ultimate.  
  
-   Nasłuchiwania adres punktu końcowego jest prywatny identyfikator URI i jest ustawiona na wartość inną niż jego `listenURI` właściwości.  
  
 Transport adresu, który `via` Określa lokalizację, do którego wiadomość początkowo powinny być wysyłane na drodze do zdalny adres określoną przez `to` parametru, w której znajduje się usługa. W większości scenariuszy Internetu `via` identyfikatora URI jest taka sama jak <xref:System.ServiceModel.EndpointAddress.Uri%2A> właściwość końcowe `to` adres usługi. Rozróżnienie tylko te dwa adresy, gdy należy wykonać ręczne trasowanie.  
  
### <a name="addressing-headers"></a>Nagłówki adresów  
 Punkt końcowy może zostać zlikwidowane przez jeden lub więcej nagłówków protokołu SOAP, oprócz jego podstawowego identyfikatora URI. Jeden zestaw scenariuszy, w których jest to przydatne to zestaw scenariuszy pośrednie protokołu SOAP, gdzie punktu końcowego wymaga od klientów zawiera nagłówków protokołu SOAP, przeznaczona dla pośredników tego punktu końcowego.  
  
 Można zdefiniować nagłówki niestandardowe adresów na dwa sposoby — przy użyciu kodu lub konfiguracji:  
  
-   W kodzie, należy utworzyć niestandardowy adres nagłówki przy użyciu <xref:System.ServiceModel.Channels.AddressHeader> klasy, a następnie używany do budowy <xref:System.ServiceModel.EndpointAddress>.  
  
-   W konfiguracji niestandardowej [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) są określane jako elementy podrzędne [ \<punktu końcowego >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
 Konfiguracja jest zazwyczaj kod, jako umożliwia zmienianie nagłówków po wdrożeniu.  
  
### <a name="custom-listening-addresses"></a>Niestandardowe adresy do nasłuchiwania  
 Można ustawić adresu nasłuchiwania na wartość inną niż identyfikator URI punktu końcowego. Jest to przydatne w scenariuszach pośrednie, gdzie adres protokołu SOAP ujawnianie jest, które publiczny protokołu SOAP, pośrednie, adres, gdzie faktycznie nasłuchuje punkt końcowy jest adresem sieci prywatnej.  
  
 Można określić niestandardowego adresu nasłuchiwania, za pomocą kodu lub konfiguracji:  
  
-   W kodzie, należy określić niestandardowe adresu nasłuchiwania, dodając <xref:System.ServiceModel.Description.ClientViaBehavior> klasy kolekcji zachowanie punktu końcowego.  
  
-   W konfiguracji, należy określić niestandardowe adresu nasłuchiwania z `ListenUri` atrybut usługi [ \<punktu końcowego >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
### <a name="custom-soap-address-filter"></a>Filtr adresów niestandardowego protokołu SOAP  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A> Jest używany w połączeniu ze wszystkimi <xref:System.ServiceModel.EndpointAddress.Headers%2A> właściwości, aby zdefiniować punkt końcowy protokołu SOAP adres filtru (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>). Domyślnie ten filtr sprawdza, czy wiadomości przychodzące ma `To` nagłówka wiadomości, odpowiadającą punktowi przez identyfikator URI i czy wszystkie nagłówki wymaganego punktu końcowego w wiadomości.  
  
 W niektórych scenariuszach punktu końcowego odbiera wszystkie komunikaty przychodzące do transportu źródłowego i nie tylko te z odpowiednią `To` nagłówka. Aby je włączyć, użytkownik może użyć <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 [Uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
