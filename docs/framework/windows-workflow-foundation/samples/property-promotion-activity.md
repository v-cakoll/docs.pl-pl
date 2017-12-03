---
title: "Właściwości działania podwyższania poziomu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e1237c0732b5422034db7c83c665c57c48486d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="property-promotion-activity"></a>Właściwości działania podwyższania poziomu
W tym przykładzie przedstawiono rozwiązanie end-to-end, która integruje się <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcja podwyższania poziomu bezpośrednio do tworzenia przepływu pracy. Podano w kolekcji elementów konfiguracji, działań przepływu pracy i rozszerzeń przepływu pracy, które ułatwiają korzystanie z funkcji podwyższania poziomu. Ponadto próbka zawiera proste przepływu pracy, który pokazuje, jak użyć tej kolekcji.  
  
> [!NOTE]
>  Przykłady są udostępniane tylko na potrzeby edukacyjne. Nie są przeznaczone dla środowiska produkcyjnego i nie zostały przetestowane w środowisku produkcyjnym. Firma Microsoft nie zapewnia pomoc techniczną dla tych przykładów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   Zainicjowana klasa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> bazy danych  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a>Przykładowych projektach  
  
-   **PropertyPromotionActivity** projekt zawiera pliki należące do elementów konfiguracji dotyczące podwyższania poziomu, działań przepływu pracy i rozszerzeń przepływu pracy.  
  
-   **CounterServiceApplication** projekt zawiera przykładowego przepływu pracy, który używa **SqlWorkflowInstanceStorePromotion** projektu.  
  
-   Skrypt SQL (PropertyPromotionActivitySQLSample.sql), które muszą być uruchamiane przed <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> bazy danych.  
  
-   Plik rozwiązania, które łączy dwa [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projektów (`PropertyPromotionActivity.sln`)  
  
## <a name="to-set-up-and-run-the-sample"></a>Aby skonfigurować i uruchomić przykładowy  
  
1.  Zainicjuj bazę danych trwałości przepływu pracy.  
  
    1.  Przejdź do katalogu próbki (\WF\Basic\Persistence\PropertyPromotionActivity), a następnie uruchom CreateInstanceStore.cmd.  
  
    2.  Jeśli uprawnienia administratora nie są dostępne, Utwórz dane logowania programu SQL Server. SQL Server Management Studio, przejdź do **zabezpieczeń**, **logowania**. Kliknij prawym przyciskiem myszy **logowania** i Utwórz nowe dane logowania. Dodaj listę kontroli dostępu użytkownika do roli SQL, otwierając **baz danych**, **InstanceStore**, **zabezpieczeń**. Kliknij prawym przyciskiem myszy **użytkowników** i wybierz **nowego użytkownika**. Ustaw **nazwa logowania** użytkownikowi utworzone powyżej. Dodaj użytkownika do członkostwo roli bazy danych System.Activities.DurableInstancing.InstanceStoreUsers (i inne). Należy pamiętać, że użytkownik może istnieć już (na przykład użytkownika dbo).  
  
2.  Otwórz plik rozwiązania PropertyPromotionActivity.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Jeśli w bazie danych innych niż lokalnej instalacji programu SQL Server Express został utworzony w magazynie wystąpień, należy zaktualizować parametry połączenia bazy danych. Zmiany w pliku App.config **CounterServiceApplication** przez ustawienie wartości `connectionString` atrybutu `sqlWorkflowInstanceStorePromotion` węzła tak, aby wskazywało do bazy danych trwałości, który został zainicjowany w kroku 1.  
  
4.  Tworzenie i uruchamianie rozwiązania. Spowoduje uruchomienie usługi WF licznik i automatyczne uruchamianie wystąpienia przepływu pracy.  
  
5.  Szybko zaznaczyć wszystkie wiersze w [dbo]. Widok [counterService] w bazie danych trwałości (w tym widoku został dodany przez uruchomienie CreateInstanceStore.cmd w kroku 1). Zostanie wyświetlony zestaw podobne do następujących wyników:  
  
    |Identyfikator wystąpienia|Równowartości|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302-929E-4C0D-8C25-768A3DA20CE5|12|2010-02-18 22:48:01.740|  
  
     Jak należy odświeżyć widok, można zauważyć, że równowartości i CounterValueLastUpdated zmienić co dwie sekundy. Jest to interwał, w którym licznik aktualizuje się samodzielnie. Równowartości i CounterValueLastUpdated reprezentują awansowanej właściwości dla tego przepływu pracy.  
  
## <a name="to-remove-the-sample"></a>Aby usunąć próbki  
  
-   Uruchom RemoveInstanceStore.cmd w katalogu próbki (\WF\Basic\Persistence\PropertyPromotionActivity).  
  
## <a name="understanding-this-sample"></a>Opis tego przykładu  
 Próbka zawiera dwa projekty i pliku SQL:  
  
-   **CounterServiceApplication** jest aplikacja konsolowa, która obsługuje prosty usługę WF licznika. Po otrzymaniu komunikat jednokierunkowy za pośrednictwem `Start` punktu końcowego, przepływu pracy liczby z zakresu od 0 do 29 wartości zmiennej licznika co dwie sekundy. Po każdym przyrost liczników przepływ pracy będzie się powtarzać, a awansowanej właściwości są aktualizowane w [dbo]. Widok [counterService]. Po uruchomieniu aplikacji konsoli, obsługuje usługę WF i wysyła komunikat do `Start` punktu końcowego, tworzenie wystąpienia licznika WF.  
  
-   **PropertyPromotionActivity** Biblioteka klasy, która zawiera elementy konfiguracji, działań przepływu pracy i przepływ pracy rozszerzenia który **CounterServiceApplication** używa.  
  
-   **PropertyPromotionActivitySQLSample.sql** tworzy i dodaje widoku [dbo]. [ CounterService] w bazie danych.  
  
### <a name="counterserviceapplication"></a>CounterServiceApplication  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a>Za pomocą SqlWorkflowInstanceStorePromotion elementu konfiguracji  
 `SqlWorkflowInstanceStorePromotion` Dziedziczy po elemencie konfiguracji `SqlWorkflowInstanceStore` element konfiguracji, ale dodaje element dodatkowe czynności konfiguracyjne o nazwie `promotionSets`. `promotionSets` Element umożliwia użytkownikowi określenie awansowanej właściwości konfiguracji. To jest plik konfiguracji, który jest używany przez próbki:  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 Sprawdź, czy definicja [dbo]. Widok [counterService].  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 Po wystąpienia przepływu pracy będzie się powtarzać, wiersza są wstawiane do `InstancePromotedProperties` wyświetlić dla każdego `PromotionSet` zdefiniowanych w konfiguracji. Ten wiersz zawiera wszystkie awansowanej właściwości `PromotionSet` (jeden poziom jest podwyższany właściwości dla kolumny). To `PromotionSet` jest klucze w postaci spójnej kolekcji: `InstanceId, PromotionName`. W tym przykładzie mamy jedną `PromotionSet` zdefiniowanych w konfiguracji, których atrybut name jest `CounterService`. Uwaga jak `PromotionName` wartość kolumny jest taki sam atrybut name elementu `PromotionSet` elementu.  
  
 Kolejność `promotedValue` elementy są powiązane z umieszczania awansowanej właściwości w `InstancePromotedProperties` widoku. `Count`jest to pierwszy `promotedValue` elementu. W związku z tym jest zamapowany na `Value1` kolumny w `InstancePromotedProperties` widoku. `LastIncrementedAt`jest to druga `promotedValue` elementu. W związku z tym jest zamapowany na `Value2` kolumny w `InstancePromotedProperties` widoku.  
  
#### <a name="using-the-promotevalue-activity"></a>Za pomocą działania PromoteValue  
 Zapoznaj się z plikiem CounterService.xamlx w [!INCLUDE[wf2](../../../../includes/wf2-md.md)] projektanta. Zwróć uwagę, że istnieją dwa specjalne działania w definicji WF: `PromoteValue<DateTime>` i `PromoteValue<Int32>`.  
  
 `PromoteValue<Int32>` Działanie ma jego `Name` zdefiniowany jako element członkowski `Count`. To jest zgodny z pierwszym `promotedValue` element w konfiguracji i jego `Value` zdefiniowany jako `Counter` zmiennej przepływu pracy. Gdy przepływ pracy będzie się powtarzać, `Counter` zmiennej przepływu pracy jest utrwalony jako awansowanej właściwości do `Value1` kolumny `InstancePromotedProperties` widoku.  
  
 `PromoteValue<DateTime>` Działanie ma jego `Name` zdefiniowany jako element członkowski `LastIncrementedAt`. To jest zgodny z drugą `promotedValue` element w konfiguracji i jego `Value` zdefiniowany jako `TimeLastIncremented` zmiennej przepływu pracy. Oznacza to, że gdy przepływ pracy będzie się powtarzać, wartość `TimeLastIncremented` zostaną utrwalone zmiennej przepływu pracy jako awansowanej właściwości do `Value2` kolumny `InstancePromotedProperties` widoku.  
  
 Należy pamiętać, że `PromotedValue` działanie ma również element członkowski logiczną o nazwie `ClearExistingPromotedData`. Jeśli ten element członkowski ma wartość `true`, czyści wszystkie wartości awansowanej właściwości do tego punktu w przepływie pracy. Na przykład jeśli nie zdefiniowano działania Sequence jako następująco:  
  
1.  PromoteValue {nazwa = "Count", wartość = 3}  
  
2.  PromoteValue {nazwa = "LastIncrementedAt", wartość = 1-1-2000}  
  
3.  Utrwalanie  
  
4.  PromoteValue {nazwa = "Count", wartość = 4, ClearExistingPromotedData = true}  
  
5.  Utrwalanie  
  
 Na drugim utrwalania, awansowana wartość `Count` będzie 4. Jednak wartość awansowana `LastIncrementedAt` będzie `NULL`. Jeśli `ClearExistingPromotedData` nie został ustawiony na `true` w kroku 4, następnie po drugim będzie nadal występować, awansowana wartość liczba będzie równa 4. W wyniku wartość awansowana `LastIncrementedAt` nadal będzie 1-1-2000.  
  
### <a name="propertypromotionactivity"></a>PropertyPromotionActivity  
 Ta biblioteka klasy zawiera następujące klasy publicznej ułatwiających korzystanie z <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcja podwyższania poziomu.  
  
#### <a name="promotevalue-class"></a>Klasa PromoteValue  
 Ta klasa zamienia jedną właściwość. Nazwa awansowanej właściwości powinny odpowiadać atrybut nazwy `promotedValue` element w konfiguracji. To działanie może być używane w Projektancie przepływów pracy. Zobacz CounterServiceApplication, na przykład użycia.  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 ClearExistingPromotedData (wartość logiczna)  
 Czyści wszystkie wartości, które zostały awansowane przed tego działania.  
  
 Nazwa (ciąg)  
 Nazwa, która reprezentuje tej właściwości. Atrybut name elementu powinna odpowiadać \<promotedValue > element w konfiguracji.  
  
 Wartość (InArgument\<T >)  
 Zmienna-wartość chcesz przechowywać w kolumnie.  
  
#### <a name="promotevalues-class"></a>Klasa PromoteValues  
 Zamienia wiele właściwości. Nazwy awansowanej właściwości powinny być zgodne wszystkie atrybuty nazwy w `promotedValue` elementów w konfiguracji. Użycie jest podobny do `PromoteValue` działania, z wyjątkiem fakt, że można podwyższyć wiele właściwości w tym samym czasie. Nie można użyć tego działania w Projektancie przepływów pracy.  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a>SqlWorkflowInstanceStorePromotionBehavior  
 Pochodną `SqlWorkflowInstanceStoreBehavior`. Ta klasa pochodna dodaje uczestnika trwałości niestandardowe (również jest częścią tej biblioteki) jako rozszerzenia przepływu pracy. Wykonanie poprzednich dwóch działań przepływu pracy zależy od tego uczestnika trwałości niestandardowych.  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 Biblioteka ta klasa zawiera także `ConfigurationElement` implementację `SqlWorkflowInstanceStorePromotionElement` i uczestnika trwałości niestandardowy używany przez poprzednie działania podwyższania poziomu.  
  
### <a name="propertypromotionactivitysqlsample"></a>PropertyPromotionActivitySQLSample  
 Ten plik SQL tworzy `[dbo].[CounterService]` wyświetlić oprócz `[InstancePromotedProperties]` widoku do wykonywania zapytań wszystkich wystąpień, które mają zestaw CounterService podwyższania poziomu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
