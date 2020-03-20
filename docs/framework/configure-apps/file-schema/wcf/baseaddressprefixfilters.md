---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 0673507b72690c3a5c7dcc35442c05e378dba43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153038"
---
# <a name="baseaddressprefixfilters"></a>\<baseAddressPrefixFilters>
Reprezentuje kolekcję elementów konfiguracji, które określają przechodzą przez filtry, które zapewniają mechanizm, aby wybrać odpowiednie powiązania internetowych usług informacyjnych (IIS) podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.  
  
> [!WARNING]
> \<baseAddressPrefixFilters> nie rozpoznaje "localhost"; zamiast tego użyj w pełni kwalifikowanej nazwy maszyny.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serwisHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**  
  
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
|[\<dodaj>](add-of-baseaddressprefixfilter.md)|Dodaje element konfiguracji, który określa filtr prefiksu dla adresów podstawowych używanych przez hosta usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serwisHostingEnvironment>](servicehostingenvironment.md)|Definiuje typ wystąpienia środowiska hostingu usługi dla określonego transportu.|  
  
## <a name="remarks"></a>Uwagi  
 Filtr prefiksu umożliwia dostawcom hostingu współużytkowania określenie identyfikatorów URI, które mają być używane przez usługę. Umożliwia współużytkowane hosty do obsługi wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.  
  
 Witryny sieci Web usług IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogi wirtualne. Dostęp do aplikacji w lokacji można uzyskać za pośrednictwem co najmniej jednego powiązania usług IIS. Powiązania usługi IIS zawierają dwie informacje: protokół wiązania i wiążące informacje. Protokół powiązania (na przykład HTTP) definiuje schemat, za pośrednictwem którego następuje komunikacja, a informacje o powiązaniach (na przykład adres IP, port, hostheader) zawierają dane używane do uzyskiwania dostępu do witryny.  
  
 Usługi IIS obsługują określanie wielu powiązań IIS dla każdej lokacji, co powoduje wiele adresów podstawowych dla każdego schematu. Ponieważ usługa WCF hostowana w witrynie umożliwia powiązanie tylko jednego adresu podstawowego dla każdego schematu, można użyć funkcji filtru prefiksów, aby wybrać wymagany adres podstawowy usługi hostowanego. Przychodzące adresy podstawowe dostarczane przez usługi IIS są filtrowane na podstawie opcjonalnego filtru listy prefiksów.  
  
 Na przykład witryna może zawierać następujące adresy podstawowe:
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Za pomocą następującego pliku konfiguracyjnego można określić filtr prefiksu na poziomie domeny aplikacji.  
  
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
  
 W tym `net.tcp://test1.fabrikam.com:8000` przykładzie i `http://test2.fabrikam.com:9000` są jedynymi adresami podstawowymi dla ich odpowiednich systemów, które mogą być przekazywane.  
  
 Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przekazywane przez. Określenie prefiksu umożliwia tylko pasujące adres podstawowy dla tego schematu, które mają być przekazywane przez.  
  
> [!NOTE]
> Filtr nie obsługuje żadnych symboli wieloznacznych. Ponadto adresy podstawowe dostarczone przez usługi IIS mogą mieć adresy powiązane `baseAddressPrefixFilters` z innymi systemami, które nie są obecne w wykazie. Adresy te nie są odfiltrowywały.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hosting](../../../wcf/feature-details/hosting.md)
