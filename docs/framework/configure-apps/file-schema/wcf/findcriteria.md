---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eb8ff3905f7696f4c71a79e31db1b8f82c9f0d3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925585"
---
# <a name="findcriteria"></a>\<findCriteria>
Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania. Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).  
  
 \<system.ServiceModel>  
\<standardEndpoints >  
  
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
|maxResults|Liczba całkowita określająca maksymalną liczbę odpowiedzi od usług w sieci lub Internetu. Jeśli zostaną odebrane maksymalne odpowiedzi przed upływem wartości określonej `duration` w atrybucie, kończy się operacja znajdowania.|  
|scopeMatchBy|Identyfikator URI, który określa zgodny algorytm do użycia podczas dopasowywania zakresów w komunikacie sondy z tym punktem końcowym.<br /><br /> Istnieją pięć obsługiwanych reguł dopasowania zakresu. Jeśli nie określisz reguły dopasowywania zakresu, `ScopeMatchByPrefix` jest używana. Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|Kolekcja elementów konfiguracji, które zawierają nazwy typów kontraktu usługi przepływu pracy.|  
|\<rozszerzenia > \<kryteria znajdowania >|Kolekcja obiektów elementu XML, które udostępniają rozszerzenia.|  
|[\<zakresy >](scopes.md)|Kolekcja obiektów, które zawierają bezwzględne identyfikatory URI, które są używane podczas operacji znajdowania do lokalizowania określonej usługi lub usług.<br /><br /> Jeśli określona usługa zostanie znaleziona, nastąpi pomyślne dopasowanie między identyfikatorem URI usługi i identyfikatorem URI zakresu, czasami z pomocą reguł zakresu, które obsługują komplikacje dopasowywania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](standardendpoints.md)|Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
