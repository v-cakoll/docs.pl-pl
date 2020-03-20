---
title: Filtry niestandardowe
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ae020173544372c3ce097c8ac57e53f3fde37514
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185210"
---
# <a name="custom-filters"></a>Filtry niestandardowe
Filtry niestandardowe umożliwiają definiowanie pasującej logiki, której nie można wykonać za pomocą filtrów wiadomości dostarczonych przez system. Na przykład można utworzyć filtr niestandardowy, który skróty określonego elementu wiadomości, a następnie sprawdza wartość, aby ustalić, czy filtr powinien zwracać true lub false.  
  
## <a name="implementation"></a>Wdrażanie  
 Filtr niestandardowy jest implementacją abstrakcyjnej <xref:System.ServiceModel.Dispatcher.MessageFilter> klasy podstawowej. Podczas implementowania filtru niestandardowego konstruktora można opcjonalnie zaakceptować parametr pojedynczego ciągu. Ten parametr zawiera informacje o konfiguracji, który jest przekazywany do konstruktora MessageFilter w celu zapewnienia wszelkich wartości lub konfiguracji, które filtr potrzebuje w czasie wykonywania w celu wykonywania dopasowań. Na przykład może to służyć do zapewnienia wartości, która szuka filtru w ramach wiadomości są oceniane. W poniższym przykładzie pokazano podstawową implementację niestandardowego filtru wiadomości, który akceptuje parametr ciągu:  
  
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
> W rzeczywistej implementacji Match metody zawiera logikę, która zbada komunikat, aby ustalić, czy ten filtr wiadomości powinien zwracać **true** lub **false**.  
  
### <a name="performance"></a>Wydajność  
 Podczas implementowania filtru niestandardowego, należy wziąć pod uwagę maksymalny czas wymagany dla filtru, aby zakończyć ocenę wiadomości. Ponieważ komunikat może być oceniany względem wielu filtrów przed znalezieniem dopasowania, ważne jest, aby upewnić się, że żądanie klienta nie limit czasu przed wszystkie filtry mogą być oceniane. W związku z tym filtr niestandardowy powinien zawierać tylko kod niezbędny do oceny zawartości lub atrybutów wiadomości w celu ustalenia, czy spełnia kryteria filtrowania.  
  
 Ogólnie rzecz biorąc należy unikać następujących czynności podczas implementowania filtru niestandardowego:  
  
- We/Wy, takie jak zapisywanie danych na dysku lub w bazie danych.  
  
- Niepotrzebne przetwarzanie, takie jak zapętlanie wielu rekordów w dokumencie.  
  
- Blokowanie operacji, takich jak wywołania, które obejmują uzyskanie blokady zasobów udostępnionych lub wykonywanie odnośeń w bazie danych.  
  
 Przed użyciem filtru niestandardowego w środowisku produkcyjnym należy uruchomić testy wydajności, aby określić średni czas potrzebny filtrowi do oceny wiadomości. W połączeniu ze średnim czasem przetwarzania innych filtrów używanych w tabeli filtrów, pozwoli to dokładnie określić maksymalną wartość limitu czasu, który powinien być określony przez aplikację kliencką.  
  
## <a name="usage"></a>Sposób użycia  
 Aby użyć filtru niestandardowego z usługą routingu, należy dodać go do tabeli filtrów, określając nowy wpis filtru typu "Niestandardowy", w pełni kwalifikowaną nazwę typu filtru wiadomości i nazwę zestawu.  Podobnie jak w przypadku innych MessageFilters, można określić filterdata ciąg, który zostanie przekazany do konstruktora filtru niestandardowego.  
  
 Poniższe przykłady demonstrują przy użyciu filtru niestandardowego z usługą routingu:  
  
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
