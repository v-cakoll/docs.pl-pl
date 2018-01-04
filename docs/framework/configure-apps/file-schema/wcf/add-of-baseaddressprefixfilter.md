---
title: '&lt;add&gt; w &lt;baseAddressPrefixFilter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad6ad6f71ef015ad97a2688a7334e8a0c6e5af44
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a>&lt;add&gt; w &lt;baseAddressPrefixFilter&gt;
Reprezentuje element konfiguracji, który określa przekazujące filtr, który zapewnia mechanizm wyboru odpowiednich powiązań usług Internet Information Services (IIS), odnośnie do hostowania [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikacji w usługach IIS.  
  
 \<System. ServiceModel >  
\<ServiceHostingEnvironment >  
\<baseAddressPrefixFilters >  
\<Dodaj >  
  
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
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Prefiks|Identyfikator URI, który jest używany do dopasowywania część adresu podstawowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Kolekcja elementów konfiguracji, filtrami przekazujące, które zapewniają mechanizm wyboru odpowiednich powiązań internetowych usług informacyjnych odnośnie do hostowania [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikacji w usługach IIS.|  
  
## <a name="remarks"></a>Uwagi  
 Filtr prefiks umożliwia udostępnionego dostawcy hostingu określić, które identyfikatory URI są używane przez usługę. Umożliwia on udostępniony hostów do obsługi wielu aplikacji za pomocą innego adresu podstawowego dla tego samego schematu w tej samej lokacji.  
  
 Witryn sieci Web IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogów wirtualnych. Za pomocą co najmniej jednego powiązania usługi IIS można uzyskać dostępu do aplikacji w lokacji. Informacje Podaj powiązania usługi IIS: Protokół powiązania i informacje o wiązaniu. Powiązanie protokół (na przykład HTTP) definiuje schemat, przez który dane są przesyłane i powiązanie informacji (na przykład adres IP, portu, nagłówka hosta) zawiera dane używane do uzyskania dostępu do witryny.  
  
 Usługi IIS obsługują określania wielokrotne powiązania usługi IIS dla każdej lokacji, co prowadzi do wielu adresu podstawowego dla każdego schematu. Ponieważ [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi hostowanej przez witrynę umożliwia powiązanie tylko jeden adres podstawowy dla każdego schematu, możesz użyć funkcji filtrowania prefiks wybierz wymagany adres podstawowy usługi hostowanej. Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane z filtru listy opcjonalny prefiks.  
  
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
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)
