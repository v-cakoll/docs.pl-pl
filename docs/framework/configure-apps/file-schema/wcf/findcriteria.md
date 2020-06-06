---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855169"
---
# \<findCriteria>
Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania. Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|czas trwania|Wartość TimeSpan, która określa maksymalny czas oczekiwania na odpowiedzi z usług w sieci. Domyślny czas trwania wynosi 20 sekund.|  
|maxResults|Liczba całkowita określająca maksymalną liczbę odpowiedzi od usług w sieci lub Internetu. Jeśli zostaną odebrane maksymalne odpowiedzi przed upływem wartości określonej w `duration` atrybucie, kończy się operacja znajdowania.|  
|scopeMatchBy|Identyfikator URI, który określa zgodny algorytm do użycia podczas dopasowywania zakresów w komunikacie sondy z tym punktem końcowym.<br /><br /> Istnieją pięć obsługiwanych reguł dopasowania zakresu. Jeśli nie określisz reguły dopasowywania zakresu, `ScopeMatchByPrefix` jest używana. Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|Kolekcja elementów konfiguracji, które zawierają nazwy typów kontraktu usługi przepływu pracy.|  
|\<extensions> dla \<findCriteria>|Kolekcja obiektów elementu XML, które udostępniają rozszerzenia.|  
|[\<scopes>](scopes.md)|Kolekcja obiektów, które zawierają bezwzględne identyfikatory URI, które są używane podczas operacji znajdowania do lokalizowania określonej usługi lub usług.<br /><br /> Jeśli określona usługa zostanie znaleziona, nastąpi pomyślne dopasowanie między identyfikatorem URI usługi i identyfikatorem URI zakresu, czasami z pomocą reguł zakresu, które obsługują komplikacje dopasowywania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
