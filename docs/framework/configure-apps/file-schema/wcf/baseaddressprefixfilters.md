---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 55ffcfb5c0c84d68033d082cbe451696bd3c9dc2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988354"
---
# <a name="baseaddressprefixfilters"></a>\<baseAddressPrefixFilters>
Reprezentuje kolekcję elementów konfiguracji, które określają filtry przekazywania, które zapewniają mechanizm wybierania odpowiednich powiązań Internet Information Services (IIS) podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.  
  
> [!WARNING]
> \<baseAddressPrefixFilters > nie rozpoznaje "localhost", zamiast tego użyj w pełni kwalifikowanej nazwy komputera.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment >  
  
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
|[\<add>](add-of-baseaddressprefixfilter.md)|Dodaje element konfiguracji, który określa filtr prefiksu dla adresów bazowych używanych przez hosta usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.|  
  
## <a name="remarks"></a>Uwagi  
 Filtr prefiksów umożliwia dostawcom hostingu współużytkowanie Określanie identyfikatorów URI, które mają być używane przez usługę. Umożliwia hostom udostępnionym hostowanie wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.  
  
 Witryny sieci Web usług IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogi wirtualne. Dostęp do aplikacji w lokacji można uzyskać za pomocą co najmniej jednego powiązania usług IIS. Powiązania usług IIS udostępniają dwie informacje: powiązania protokołu i powiązania. Protokół powiązania (na przykład HTTP) definiuje schemat, w którym odbywa się komunikacja, a informacje o powiązaniu (na przykład adres IP, port, nagłówek hosta) zawierają dane używane do uzyskiwania dostępu do witryny.  
  
 Usługi IIS obsługują Określanie wielu powiązań usług IIS dla każdej lokacji, co daje w wyniku wiele adresów bazowych dla każdego schematu. Ponieważ usługa WCF hostowana w lokacji umożliwia powiązanie tylko z jednym adresem podstawowym dla każdego schematu, można użyć funkcji filtru prefiksu, aby wybrać wymagany podstawowy adres usługi hostowanej. Przychodzące adresy podstawowe, dostarczane przez usługi IIS, są filtrowane na podstawie opcjonalnego filtru listy prefiksów.  
  
 Na przykład witryna może zawierać następujące adresy podstawowe.  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Możesz użyć poniższego pliku konfiguracji, aby określić filtr prefiksu na poziomie elementu AppDomain.  
  
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
  
 W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są jedynymi adresami podstawowymi dla odpowiednich schematów, które mogą być przesyłane przez program.  
  
 Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przesyłane przez. Określenie prefiksu zezwala tylko na przekazanie zgodnego adresu podstawowego dla tego schematu.  
  
> [!NOTE]
> Filtr nie obsługuje żadnych symboli wieloznacznych. Ponadto baseAddresses dostarczone przez usługi IIS mogą mieć adresy powiązane z innymi schematami nieobecnymi na `baseAddressPrefixFilters` liście. Te adresy nie są odfiltrowane.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hosting](../../../wcf/feature-details/hosting.md)
