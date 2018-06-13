---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 9ac0c756f611c877ca689f12e5fe365026924f1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358544"
---
# <a name="ltbaseaddressprefixfiltersgt"></a>&lt;baseAddressPrefixFilters&gt;
Reprezentuje kolekcję elementów, które określają przechodzą przez filtry, które zawierają mechanizm wyboru odpowiednich powiązań usług Internet Information Services (IIS), odnośnie do hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS konfiguracji.  
  
> [!WARNING]
>  \<baseAddressPrefixFilters > nie rozpoznano "localhost", zamiast tego użyj nazwy FQDN komputera.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|Dodaje element konfiguracji, który określa filtr prefiks dla adres podstawowy używany przez hosta usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.|  
  
## <a name="remarks"></a>Uwagi  
 Filtr prefiks umożliwia udostępnionego dostawcy hostingu określić, które identyfikatory URI są używane przez usługę. Umożliwia on udostępniony hostów do obsługi wielu aplikacji za pomocą innego adresu podstawowego dla tego samego schematu w tej samej lokacji.  
  
 Witryn sieci Web IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogów wirtualnych. Za pomocą co najmniej jednego powiązania usługi IIS można uzyskać dostępu do aplikacji w lokacji. Informacje Podaj powiązania usługi IIS: Protokół powiązania i informacje o wiązaniu. Powiązanie protokół (na przykład HTTP) definiuje schemat, przez który dane są przesyłane i powiązanie informacji (na przykład adres IP, portu, nagłówka hosta) zawiera dane używane do uzyskania dostępu do witryny.  
  
 Usługi IIS obsługują określania wielokrotne powiązania usługi IIS dla każdej lokacji, co prowadzi do wielu adresu podstawowego dla każdego schematu. Ponieważ usługi WCF hostowanej przez witrynę umożliwia powiązanie tylko jeden adres podstawowy dla każdego schematu, można użyć funkcji filtrowania prefiks wybierz wymagany adres podstawowy usługi hostowanej. Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane z filtru listy opcjonalny prefiks.  
  
 Na przykład witryna może zawierać następujący adres podstawowy.  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Można użyć następującego pliku konfiguracji do określenia filtru prefiks na poziomie elementu appdomain.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są tylko podstawowy adres ich systemów, które mogą być przekazywane.  
  
 Domyślnie jeśli nie określono prefiksu, wszystkie adresy są przekazywane. Określenie prefiksu umożliwia tylko pasujących adres podstawowy schemat przekazywane.  
  
> [!NOTE]
>  Filtr nie obsługuje żadnych symboli wieloznacznych. Ponadto baseAddresses dostarczonych przez usługi IIS może być adresy powiązany z innych systemów, które nie znajduje się w `baseAddressPrefixFilters` listy. Tych adresów nie są odfiltrowywane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)
