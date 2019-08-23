---
title: Filtry niestandardowe
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ade387524c9ca6c8ef337ccf6a5b3453b7df976b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945378"
---
# <a name="custom-filters"></a>Filtry niestandardowe
Filtry niestandardowe umożliwiają zdefiniowanie dopasowania logiki, której nie można wykonać za pomocą filtrów komunikatów dostarczonych przez system. Na przykład można utworzyć filtr niestandardowy, który miesza określony element komunikatu, a następnie analizuje wartość, aby określić, czy filtr powinien zwrócić wartość true lub false.  
  
## <a name="implementation"></a>Implementacja  
 Filtr niestandardowy jest implementacją <xref:System.ServiceModel.Dispatcher.MessageFilter> abstrakcyjnej klasy podstawowej. Podczas implementowania niestandardowego filtru Konstruktor może opcjonalnie zaakceptować pojedynczy parametr ciągu. Ten parametr zawiera informacje o konfiguracji, które są przesyłane do konstruktora MessageFilter w celu zapewnienia dowolnych wartości lub konfiguracji wymaganych przez filtr w czasie wykonywania w celu wykonania dopasowań. Na przykład może to służyć do podania wartości, która będzie wyglądała w filtrze w analizowanym komunikacie. Poniższy przykład ilustruje podstawową implementację niestandardowego filtru komunikatów, który akceptuje parametr ciągu:  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> W rzeczywistej implementacji metody dopasowania zawierają logikę, która będzie analizować komunikat, aby określić, czy ten filtr komunikatów powinien zwrócić **wartość true** lub **false**.  
  
### <a name="performance"></a>Wydajność  
 Podczas implementowania filtru niestandardowego należy wziąć pod uwagę maksymalny czas wymagany do przeprowadzenia obliczeń przez filtr. Ponieważ komunikat można ocenić względem wielu filtrów przed znalezieniem dopasowania, należy się upewnić, że żądanie klienta nie przekroczy limitu czasu, zanim będzie można ocenić wszystkie filtry. W związku z tym filtr niestandardowy powinien zawierać tylko kod niezbędny do oszacowania zawartości lub atrybutów komunikatu w celu ustalenia, czy pasuje do kryteriów filtrowania.  
  
 Ogólnie rzecz biorąc, podczas implementowania filtra niestandardowego należy unikać następujących czynności:  
  
- We/wy, takie jak zapisywanie danych na dysku lub w bazie danych.  
  
- Niepotrzebne przetwarzanie, takie jak pętla dla wielu rekordów w dokumencie.  
  
- Operacje blokowania, takie jak wywołania, które wymagają uzyskania blokady zasobów udostępnionych lub wykonywania wyszukiwania względem bazy danych.  
  
 Przed użyciem filtru niestandardowego w środowisku produkcyjnym należy uruchomić testy wydajnościowe, aby określić średni czas wymagany przez filtr w celu oceny komunikatu. W połączeniu z średnim czasem przetwarzania innych filtrów używanych w tabeli filtrów umożliwi to dokładne określenie maksymalnej wartości limitu czasu, która powinna być określona przez aplikację kliencką.  
  
## <a name="usage"></a>Użycie  
 Aby można było użyć niestandardowego filtru z usługą routingu, należy dodać go do tabeli filtrów przez określenie nowego wpisu filtru typu "Custom", w pełni kwalifikowanej nazwy typu filtru komunikatów i nazwy zestawu.  Podobnie jak w przypadku innych MessageFilters można określić ciąg danych filtru, który zostanie przesłany do konstruktora filtru niestandardowego.  
  
 W poniższych przykładach pokazano, jak za pomocą filtru niestandardowego korzystać z usługi routingu:  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"   
            customType="CustomAssembly.MyMessageFilter,   
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
