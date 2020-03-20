---
title: <add> dla <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 8fdae02b558708a9b3f4535123752dce12dd5cf5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153143"
---
# <a name="add-of-baseaddressprefixfilter"></a>\<dodaj> baseAddressPrefixFilter \<>
Reprezentuje element konfiguracji, który określa filtr przekazywania, który zapewnia mechanizm, aby wybrać odpowiednie powiązania internetowych usług informacyjnych (IIS) podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serwisHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**  
  
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
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Prefiks|Identyfikator URI, który jest używany do dopasowania części adresu podstawowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|Kolekcja elementów konfiguracji, które określają filtry przekazywania, które zapewniają mechanizm, aby wybrać odpowiednie powiązania usług IIS podczas hostowania aplikacji Programu Windows Communication Foundation (WCF) w usługach IIS.|  
  
## <a name="remarks"></a>Uwagi  
 Filtr prefiksu umożliwia dostawcom hostingu współużytkowania określenie identyfikatorów URI, które mają być używane przez usługę. Umożliwia współużytkowane hosty do obsługi wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.  
  
 Witryny sieci Web usług IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogi wirtualne. Dostęp do aplikacji w lokacji można uzyskać za pośrednictwem jednego lub więcej powiązań usług IIS. Powiązania usługi IIS zawierają dwie informacje: protokół wiązania i wiążące informacje. Protokół powiązania (na przykład HTTP) definiuje schemat, za pośrednictwem którego następuje komunikacja, a informacje o powiązaniach (na przykład adres IP, port, hostheader) zawierają dane używane do uzyskiwania dostępu do witryny.  
  
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
  
 W tym `net.tcp://test1.fabrikam.com:8000` przykładzie są `http://test2.fabrikam.com:9000` jedynymi adresami podstawowymi dla ich odpowiednich systemów, które mogą być przekazywane.  
  
 Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przekazywane przez. Określenie prefiksu umożliwia tylko pasujące adres podstawowy dla tego schematu, które mają być przekazywane przez.  
  
> [!NOTE]
> Filtr nie obsługuje żadnych symboli wieloznacznych. Ponadto adresy podstawowe dostarczone przez usługi IIS mogą mieć adresy powiązane `baseAddressPrefixFilters` z innymi systemami, które nie są obecne w wykazie. Adresy te nie są odfiltrowywały.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hosting](../../../wcf/feature-details/hosting.md)
