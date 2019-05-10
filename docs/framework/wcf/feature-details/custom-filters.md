---
title: Filtry niestandardowe
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 9ef94d95737fb743af56f411bcc0f39ceea679a0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912688"
---
# <a name="custom-filters"></a>Filtry niestandardowe
Filtry niestandardowe umożliwiają zdefiniowanie pasującego logiki, która nie da się osiągnąć przy użyciu filtrów dostarczane przez system komunikatu. Na przykład utworzyć filtr niestandardowy, który wyznacza wartość skrótu elementu określoną wiadomość, a następnie sprawdza, czy wartość do określenia, czy filtr ma zwracać wartość PRAWDA lub FAŁSZ.  
  
## <a name="implementation"></a>Implementacja  
 Filtr niestandardowy jest implementacją <xref:System.ServiceModel.Dispatcher.MessageFilter> abstrakcyjna klasa bazowa. Podczas implementowania niestandardowego filtru, Konstruktor opcjonalnie może akceptować jeden ciąg znaków. Ten parametr zawiera informacje o konfiguracji, który jest przekazywany do konstruktora MessageFilter w celu zapewnienia, że odpowiada wartości lub konfigurację filtru musi mieć w czasie wykonywania w celu wykonania. Na przykład to może służyć do Podaj wartość filtru szuka wiadomości oceniane. Poniższy przykład pokazuje podstawową implementację filtr niestandardowy komunikat, który przyjmuje parametr ciąg:  
  
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
>  W rzeczywistej implementacji metody dopasowania zawiera logikę, która zbada komunikatu, aby określić, jeśli ten filtr komunikatu powinna zwrócić **true** lub **false**.  
  
### <a name="performance"></a>Wydajność  
 Podczas implementowania niestandardowego filtru, należy wziąć pod uwagę maksymalnego czasu wymaganego do filtru w celu oceny wiadomości. Ponieważ komunikat może zostać obliczone dla wielu filtrów, zanim zostanie znalezione dopasowanie, jest ważne, aby upewnić się, że żądanie klienta nie podlega limitowi czasu zanim wszystkie filtry, które mogą być obliczane. W związku z tym filtr niestandardowy może zawierać tylko kod niezbędnych do oceny zawartości lub atrybutów wiadomości w celu ustalenia, jeśli jest on zgodny kryteria filtrowania.  
  
 Ogólnie rzecz biorąc należy unikać następujące podczas implementowania niestandardowego filtru:  
  
- We/Wy, takich jak zapisywanie danych na dysku lub z bazą danych.  
  
- Niepotrzebna przetwarzania, takich jak odtwarzanie w pętli za pośrednictwem wielu rekordów w dokumencie.  
  
- Blokowanie operacji, takich jak wywołania, które obejmują uzyskania blokady ze współużytkowanych zasobów lub przeprowadzania wyszukiwań względem bazy danych.  
  
 Przed użyciem niestandardowego filtru w środowisku produkcyjnym, należy uruchomić testy wydajności w celu ustalenia średnia długość czasu, przez jaki filtr potrzebuje do oceny wiadomość. W połączeniu z Średni czas przetwarzania filtrów, używane w tabeli filtru, temu będzie można dokładnie określić maksymalną wartość limitu czasu, który powinien być określony przez aplikację klienta.  
  
## <a name="usage"></a>Użycie  
 Aby można było używać niestandardowego filtru z usługą routingu, należy dodać go do tabeli filtru, określając nowy wpis filtru typu niestandardowego"," w pełni kwalifikowana nazwa typu filtru komunikatów i nazwy zestawu.  Podobnie jak w przypadku innych MessageFilters można określić danych parametrów filtru, który zostanie przekazany do konstruktora niestandardowego filtru.  
  
 W poniższych przykładach pokazano, przy użyciu niestandardowego filtru z usługą routingu:  
  
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
