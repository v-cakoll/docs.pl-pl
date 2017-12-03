---
title: "Adresy punktów końcowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3231e5b043dd0e65c09f25eed56341e660bf1f87
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-addresses"></a>Adresy punktów końcowych
Każdy punkt końcowy ma adres skojarzony z, która jest używana do lokalizowania i identyfikowania punktu końcowego. Ten adres składa się przede wszystkim z zasobów identyfikator URI (Uniform), który określa położenie punktu końcowego. Adres punktu końcowego jest reprezentowana w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] model programowania przez <xref:System.ServiceModel.EndpointAddress> klasy, która zawiera opcjonalny <xref:System.ServiceModel.EndpointAddress.Identity%2A> właściwość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, które wymiany wiadomości, a opcjonalny zestaw <xref:System.ServiceModel.EndpointAddress.Headers%2A> właściwości, które opisują inne nagłówki SOAP, wymagane w celu dotarcia do usługi. Opcjonalne nagłówki zawierają dodatkowe i bardziej szczegółowych informacji o adresach do identyfikacji użytkownika lub interakcji z punktem końcowym usługi. Adres punktu końcowego jest reprezentowana w sieci jako usługi WS-Addressing odwołaniu do punktu końcowego (EPR).  
  
## <a name="uri-structure-of-an-address"></a>Struktura adresu URI  
 Adres URI dla transportu większości ma cztery części. Na przykład czterech części identyfikatora URI http://www.fabrikam.com:322/mathservice.svc/secureEndpoint można wyszczególnione w następujący sposób:  
  
-   Schemat: http:  
  
-   Maszyny: www.fabrikam.com  
  
-   (opcjonalnie) Port: 322  
  
-   Ścieżka: /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Definiowanie adresu dla usługi  
 Adres punktu końcowego usługi można określić albo imperatively za pomocą kodu lub deklaratywnie za pomocą konfiguracji. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie opracowywane. Ogólnie rzecz biorąc lepiej jest punkty końcowe usługi przy użyciu konfiguracji zamiast kodu. Utrzymywanie powiązania i adresowanie poza kod pozwala na zmianę bez konieczności ponowne skompilowanie lub ponownego wdrażania aplikacji.  
  
### <a name="defining-an-address-in-configuration"></a>Definiowanie adresu w konfiguracji  
 Aby zdefiniować punkt końcowy w pliku konfiguracji, należy użyć [ \<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu. Szczegółowe informacje i przykładem, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Definiowanie adresu w kodzie  
 Adres punktu końcowego można tworzyć w kodzie z <xref:System.ServiceModel.EndpointAddress> klasy. Szczegółowe informacje i przykładem, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>Punkty końcowe w języku WSDL  
 Adres punktu końcowego również może być reprezentowana w języku WSDL jako elementu WS-Addressing EPR wewnątrz odpowiedniego punktu końcowego `wsdl:port` elementu. EPR zawiera adres punktu końcowego, a także wszystkie właściwości adresu. Szczegółowe informacje i przykładem, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Wiele usług IIS powiązanie pomocy technicznej dla programu .NET Framework 3.5  
 Usługodawcy internetowi często hostować wiele aplikacji na ten sam serwer i lokacji w celu zwiększenia gęstości lokacji i niższy całkowity koszt posiadania. Te aplikacje są zwykle powiązane z różnymi adresami podstawowej. Witryny sieci Web usług Internet Information Services (IIS) może zawierać wiele aplikacji. Aplikacje w lokacji są dostępne za pośrednictwem co najmniej jednego powiązania usługi IIS.  
  
 Informacje Podaj powiązania usługi IIS: Protokół powiązania i informacje o wiązaniu. Protokół powiązania definiuje schemat, przez który dane są przesyłane, a informacje o wiązaniu są to informacje używane do uzyskania dostępu do witryny.  
  
 W poniższym przykładzie przedstawiono składniki, które mogą być obecne w powiązaniu usługi IIS:  
  
-   Protokół powiązania: HTTP  
  
-   Informacje o powiązaniu: Adres IP, portu i nagłówka hosta  
  
 Usługi IIS można określić wiele powiązań dla każdej lokacji, co prowadzi do wielu adresu podstawowego dla każdego schematu. Przed [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie obsługuje wielu adresów dla schematu i, jeśli zostały one określone, zgłosił <xref:System.ArgumentException> podczas aktywacji.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Umożliwia dostawcy usług internetowych hostować wiele aplikacji o różnych adresu podstawowego dla tego samego schematu w tej samej lokacji.  
  
 Na przykład lokacji może zawierać następujący adres podstawowy:  
  
-   http://Payroll.myorg.com/Service.svc  
  
-   http://Shipping.myorg.com/Service.svc  
  
 Z [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], należy określić filtr prefiks na poziomie elementu AppDomain w pliku konfiguracji. W tym z [ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) element, który zawiera listę prefiksów. Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane w oparciu o liście opcjonalny prefiks. Domyślnie jeśli nie określono prefiksu, wszystkie adresy są przekazywane. Określenie prefiksu wyniki w tylko pasujących adres podstawowy schemat przekazywane.  
  
 Oto przykładowy kod konfiguracji, który używa filtrów prefiks.  
  
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
  
 Adres podstawowy dostarczonych przez usługi IIS może być adresy powiązany z innych systemów, które nie znajduje się w `baseAddressPrefixFilters` listy. Tych adresów nie są odfiltrowywane.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Usługi IIS powiązanie obsługi wielu w .NET Framework 4 i nowsze  
 Począwszy od platformy .NET 4, zostanie włączona obsługa wielu powiązań w usługach IIS bez konieczności pobrania jeden adres podstawowy, ustawiając <xref:System.ServiceModel.ServiceHostingEnvironment>w <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> ustawienie na wartość true. Ta obsługa jest ograniczona do schematy protokołu HTTP.  
  
 Poniżej przedstawiono przykładowy kod konfiguracji, który używa multipleSiteBindingsEnabled na [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Wszystkie ustawienia baseAddressPrefixFilters są ignorowane, dla obu protokołów HTTP i innych niż HTTP, gdy wiele powiązań witryny są włączone, za pomocą tego ustawienia.  
  
 Aby uzyskać szczegółowe informacje i przykłady, zobacz [Obsługa wielu wiązań witryny usług IIS](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) i <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.  
  
## <a name="extending-addressing-in-wcf-services"></a>Rozszerzanie adresowania w usługach WCF  
 Domyślne adresowania model [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi używa adres URI punktu końcowego w następujących celach:  
  
-   Aby określić adres nasłuchiwania usługi lokalizacji, jaką punktu końcowego nasłuchuje wiadomości,  
  
-   Aby określić filtr adresów SOAP, adres punktu końcowego oczekuje jako nagłówka SOAP.  
  
 Wartości dla każdego z tych celów, można określić oddzielnie, umożliwiając kilka rozszerzeń adresowania tego obejmują użyteczne scenariusze:  
  
-   Pośredników SOAP: wiadomości wysłane przez klienta są przesyłane za pośrednictwem jednego lub więcej dodatkowych usług, które przetworzyć komunikatu przed jego ostatecznego miejsca przeznaczenia. Pośredników SOAP można wykonywać różne zadania, takie jak buforowanie, routingu, równoważenia obciążenia lub schemat sprawdzania poprawności dla wiadomości. W tym scenariuszu odbywa się przez wysyłanie komunikatów do oddzielnych adresów fizycznych (`via`) który dotyczy pośredniczącej, a nie tylko na adres logiczny (`wsa:To`) który celem ostatecznego miejsca przeznaczenia.  
  
-   Nasłuchiwania adres punktu końcowego jest prywatny identyfikator URI i ma ustawioną wartość inną niż jego `listenURI` właściwości.  
  
 Transport adresu, który `via` Określa lokalizację, do której wiadomość początkowo mają być wysyłane w drodze do zdalnego adresu określonym przez `to` parametru, w której znajduje się usługa. W większości przypadków Internet `via` identyfikatora URI jest taka sama jak <xref:System.ServiceModel.EndpointAddress.Uri%2A> właściwości końcowych `to` adresu usługi. Tylko rozróżnienia między tymi dwoma adresami po wykonaniu musi ręcznie routingu.  
  
### <a name="addressing-headers"></a>Nagłówki adresów  
 Punkt końcowy może zostać zlikwidowane przez co najmniej jeden nagłówek SOAP oprócz jego podstawowego identyfikatora URI. Jeden zestaw scenariuszy, w których jest to przydatne to zestaw SOAP scenariuszy pośredniczącego w przypadku gdy punkt końcowy wymaga klientom tego punktu końcowego obejmują celem pośredników nagłówki SOAP.  
  
 Można zdefiniować nagłówki niestandardowy adres na dwa sposoby — za pomocą kodu lub konfiguracji:  
  
-   W kodzie, należy utworzyć niestandardowy adres nagłówki za pomocą <xref:System.ServiceModel.Channels.AddressHeader> klasy, a następnie używany do budowy <xref:System.ServiceModel.EndpointAddress>.  
  
-   W konfiguracji, niestandardowe [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) są określone jako elementy podrzędne [ \<punktu końcowego >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
 Konfiguracja jest zazwyczaj kodu, jako umożliwia zmienianie nagłówków po wdrożeniu.  
  
### <a name="custom-listening-addresses"></a>Niestandardowe nasłuchiwania adresów  
 Adres nasłuchiwania można ustawić na wartość inną niż identyfikator URI punktu końcowego. Jest to przydatne w pośredniczące zastosowaniach adres SOAP uwidocznienia które publicznego pośredniczącej, protokołu SOAP, adres, gdy punkt końcowy faktycznie nasłuchuje jest adresu w sieci prywatnej.  
  
 Możesz określić niestandardowy adres nasłuchiwania przy użyciu kodu lub konfiguracji:  
  
-   W kodzie, określ niestandardowy adres nasłuchiwania przez dodanie <xref:System.ServiceModel.Description.ClientViaBehavior> klasy do kolekcji zachowania punktu końcowego.  
  
-   W konfiguracji, określ niestandardowy adres nasłuchiwania z `ListenUri` atrybut usługi [ \<punktu końcowego >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
### <a name="custom-soap-address-filter"></a>Filtr adresów SOAP niestandardowych  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A> Jest używany w połączeniu ze wszystkimi <xref:System.ServiceModel.EndpointAddress.Headers%2A> właściwości, aby zdefiniować filtr adresu punktu końcowego protokołu SOAP (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>). Domyślnie ten filtr sprawdza, czy komunikat przychodzący ma `To` nagłówek komunikatu, odpowiadającą punktowi końcowemu przez identyfikator URI i czy wszystkie nagłówków wymaganego punktu końcowego są obecne w komunikacie.  
  
 W niektórych scenariuszach punkt końcowy odbiera wszystkie komunikaty przychodzące do transportu źródłowego, a nie tylko te z odpowiednią `To` nagłówka. Aby je włączyć, użytkownik może użyć <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 [Uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
