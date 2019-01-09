---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 04579980201b397e7ed92f55ffcb19e54de18aaa
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149231"
---
# <a name="ltbaseaddressprefixfiltersgt"></a>&lt;baseAddressPrefixFilters&gt;
Reprezentuje kolekcję konfiguracji, które elementy, które określają przechodzą przez filtry, które zapewniają mechanizm wyboru odpowiednich powiązań usług Internet Information Services (IIS) w przypadku hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.  
  
> [!WARNING]
>  \<baseAddressPrefixFilters > nie rozpoznaje "localhost", zamiast tego użyj w pełni kwalifikowanej nazwy komputera.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
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
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|Dodaje element konfiguracji, który określa filtr prefiksu adres podstawowy, używany przez hosta usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.|  
  
## <a name="remarks"></a>Uwagi  
 Filtr prefiksu umożliwia udostępniony dostawcy hostingu określić, które identyfikatory URI, które mają być używane przez usługę. Dzięki temu hosty udostępnione do hostowania wielu aplikacji przy użyciu różnych adresami podstawowymi dla tego samego schematu w tej samej lokacji.  
  
 Witryn sieci Web IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogów wirtualnych. Aplikacja w lokacji jest możliwy za pośrednictwem jednego lub więcej powiązań usług IIS. Powiązania usługi IIS zapewniają dwóch rodzajów informacji: Protokół powiązania i informacje o powiązaniu. Powiązanie protokołu (na przykład HTTP) definiuje schemat, przez który dane są przesyłane i informacje (na przykład adres IP, portu, nagłówka hosta) zawiera dane używane do uzyskiwania dostępu do witryny.  
  
 Program IIS obsługuje Określanie wielu powiązań usług IIS dla każdej lokacji, co skutkuje z wieloma adresami podstawowymi dla każdego schematu. Ponieważ usługi WCF hostowanej przez witrynę pozwala na powiązanie tylko jeden adres podstawowy dla każdego schematu, można użyć funkcji filtrowania prefiksu i wybierz wymagany adres podstawowy usługi hostowanej. Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane w oparciu o filtr list opcjonalny prefiks.  
  
 Na przykład witryna może zawierać następujące adresy podstawowy.  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Następujący plik konfiguracji służy do określania prefiksu filtr na poziomie domeny aplikacji.  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są tylko podstawowy adres ich systemów, które mogą być przekazywane.  
  
 Domyślnie jeśli nie określono prefiksu, wszystkie adresy są przekazywane. Umożliwia określenie prefiksu tylko pasujących adres podstawowy dla tego schematu, które zostaną przekazane za pośrednictwem.  
  
> [!NOTE]
>  Filtr nie obsługuje żadnych symboli wieloznacznych. Ponadto baseAddresses dostarczane przez usługi IIS wiążące adresy powiązany z innych systemów, które nie znajduje się w `baseAddressPrefixFilters` listy. Te adresy nie są odfiltrowywane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)
