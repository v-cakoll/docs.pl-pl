---
title: Filtry niestandardowe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: c9d0c81d715b2e876fe8144d4cff198f3321a22e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-filters"></a>Filtry niestandardowe
Filtry niestandardowe umożliwiają definiowanie pasującego logikę, która nie może być wykonywane przy użyciu filtrów dostarczane przez system komunikatu. Na przykład możesz utworzyć niestandardowy filtr, który tworzy skrót elementu określonego komunikatu, a następnie sprawdza, czy wartość, aby ustalić, czy filtr powinien zwrócić wartość true lub false.  
  
## <a name="implementation"></a>Implementacja  
 Filtr niestandardowy jest implementacją <xref:System.ServiceModel.Dispatcher.MessageFilter> abstrakcyjnej klasy podstawowej. Podczas implementowania niestandardowych filtru, konstruktora opcjonalnie może akceptować parametr będący pojedynczym ciągiem. Ten parametr zawiera informacje o konfiguracji, który jest przekazany do konstruktora MessageFilter w celu zapewnienia wszystkie wartości lub konfiguracji, który wymaga filtr w czasie wykonywania, aby wykonać jest zgodny. Na przykład to może służyć do zapewnienia wartość filtru wyszukuje w komunikacie oceniane. W poniższym przykładzie pokazano Podstawowa implementacja filtr niestandardowy komunikat, który akceptuje parametr typu string:  
  
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
>  W rzeczywistych implementacji metody dopasowania zawiera logikę, która zbada komunikatu, aby określić, czy ten filtr komunikatu powinien zwrócić **true** lub **false**.  
  
### <a name="performance"></a>Wydajność  
 Podczas implementowania niestandardowego filtru, należy wziąć pod uwagę maksymalnego czasu wymaganego do filtr, aby ukończyć obliczania komunikatu. Ponieważ komunikat może zostać oceniona pod kątem wielu filtrów, zanim zostanie znaleziony odpowiednik, jest ważne upewnić się, czy żądanie klienta jest nie upłynął limit czasu, zanim wszystkie filtry, które może przyjąć. W związku z tym niestandardowego filtru powinien zawierać tylko kod niezbędnych do oceny zawartości lub atrybutów komunikatu w celu określenia, czy jego kryteria filtru.  
  
 Ogólnie rzecz biorąc należy unikać następujące podczas implementowania niestandardowego filtru:  
  
-   We/Wy, takich jak zapisywania danych na dysku lub z bazą danych.  
  
-   Niepotrzebny przetwarzania, takich jak pętli wielu rekordów w dokumencie.  
  
-   Blokowanie operacji, takich jak wywołania, które wymagają uzyskania blokady na udostępnionych zasobów lub wykonywania wyszukiwania w bazie danych.  
  
 Aby można było używać niestandardowego filtru w środowisku produkcyjnym, należy uruchomić testy wydajności w celu ustalenia średnią długość czasu, który przyjmuje filtr do oceny wiadomości. W połączeniu z Średni czas przetwarzania inne filtry w tabeli filtrów, to umożliwi dokładnie określić wartości maksymalny limit czasu, który powinien być określony przez aplikację klienta.  
  
## <a name="usage"></a>Użycie  
 Aby można było używać niestandardowego filtru z usługą routingu, należy dodać go do tabeli filtrów, określając nowy wpis filtru typu "Niestandardowy" pełni kwalifikowana nazwa typu filtru komunikatów, a nazwa z zestawu.  Podobnie jak w przypadku innych MessageFilters można określić danych ciąg filtru, który zostanie przekazany do konstruktora filtru niestandardowego.  
  
 W poniższych przykładach pokazano, w usłudze Routing przy użyciu niestandardowego filtru:  
  
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
