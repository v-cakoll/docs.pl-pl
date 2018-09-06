---
title: Działanie promocji właściwości
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 6e059a0d344e6c62833feaa890c459c141a49673
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870087"
---
# <a name="property-promotion-activity"></a>Działanie promocji właściwości
W tym przykładzie zapewnia rozwiązania end-to-end, która integruje się <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcja podwyższania poziomu bezpośrednio do tworzenia przepływu pracy. Kolekcja elementów konfiguracji, działania przepływu pracy i rozszerzeń przepływu pracy, które upraszczają korzystanie z funkcji podwyższania poziomu są dostarczane. Ponadto przykład zawiera prostego przepływu pracy, który demonstruje sposób skorzystania z tej kolekcji.  
  
> [!NOTE]
>  Przykłady są udostępniane wyłącznie w celach edukacyjnych. Nie są przeznaczone dla środowiska produkcyjnego i nie zostały przetestowane w środowisku produkcyjnym. Firma Microsoft zapewnia pomoc techniczną tych przykładów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   Zainicjowana klasa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> bazy danych  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a>Przykładowe projekty  
  
-   **PropertyPromotionActivity** projekt zawiera pliki odnoszących się do elementów konfiguracji specyficznej dla podwyższania poziomu, działania przepływu pracy i rozszerzenia przepływu pracy.  
  
-   **CounterServiceApplication** projekt zawiera przykładowy przepływ pracy, który używa **SqlWorkflowInstanceStorePromotion** projektu.  
  
-   Skrypt SQL (PropertyPromotionActivitySQLSample.sql), które muszą być uruchamiane względem <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> bazy danych.  
  
-   Plik rozwiązania, który łączy dwie [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projektów (`PropertyPromotionActivity.sln`)  
  
## <a name="to-set-up-and-run-the-sample"></a>Aby skonfigurować i uruchomić przykład  
  
1.  Inicjowanie bazy danych trwałości przepływu pracy.  
  
    1.  Przejdź do katalogu próbki (\WF\Basic\Persistence\PropertyPromotionActivity), a następnie uruchom CreateInstanceStore.cmd.  
  
    2.  Jeśli uprawnienia administratora nie są dostępne, należy utworzyć identyfikator logowania programu SQL Server. SQL Server Management Studio, przejdź do **zabezpieczeń**, **logowania**. Kliknij prawym przyciskiem myszy **logowania** i Utwórz nową nazwę logowania. Dodaj użytkownika listy ACL do roli programu SQL, otwierając **baz danych**, **objekt InstanceStore**, **zabezpieczeń**. Kliknij prawym przyciskiem myszy **użytkowników** i wybierz **nowego użytkownika**. Ustaw **nazwa logowania** użytkownika utworzonego powyżej. Dodaj użytkownika do członkostwo roli bazy danych System.Activities.DurableInstancing.InstanceStoreUsers (i inne). Należy pamiętać, że użytkownik może istnieć już (na przykład użytkownik dbo).  
  
2.  Otwórz plik rozwiązania PropertyPromotionActivity.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Jeśli utworzono magazyn wystąpienia w bazie danych innych niż lokalna instalacja programu SQL Server Express, należy zaktualizować parametry połączenia bazy danych. Instrukcja ALTER pliku App.config, w obszarze **CounterServiceApplication** , ustawiając wartość `connectionString` atrybutu na `sqlWorkflowInstanceStorePromotion` węzła, które wskazuje do bazy danych trwałości, który został zainicjowany w kroku 1.  
  
4.  Skompiluj i uruchom rozwiązanie. Spowoduje to uruchomienie usługi programu WF licznika i automatyczne uruchamianie wystąpienia przepływu pracy.  
  
5.  Szybko wybrać wszystkie wiersze, w [dbo]. Widok [counterService] w bazie danych trwałości (ten widok został dodany, uruchamiając CreateInstanceStore.cmd w kroku 1). Zostanie wyświetlony zestaw podobne do następujących wyników:  
  
    |Identyfikator wystąpienia|CounterValue|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302-929E-4C0D-8C25-768A3DA20CE5|12|2010-02-18 22:48:01.740|  
  
     Jak zachować odświeżyć widok, można zauważyć, że CounterValue i CounterValueLastUpdated zmienić co 2 sekundy. Jest to interwał, w którym licznik aktualizuje się samodzielnie. CounterValue i właściwości reprezentują promowane CounterValueLastUpdated dla tego przepływu pracy.  
  
## <a name="to-remove-the-sample"></a>Aby usunąć próbki  
  
-   Uruchom RemoveInstanceStore.cmd w katalogu próbki (\WF\Basic\Persistence\PropertyPromotionActivity).  
  
## <a name="understanding-this-sample"></a>Opis tego przykładu  
 Przykład zawiera dwa projekty i plik SQL:  
  
-   **CounterServiceApplication** to aplikacja konsoli, która udostępnia prostą usługę WF licznika. Po odebraniu komunikatu jednokierunkowe za pośrednictwem `Start` punktu końcowego, przepływ pracy liczby z zakresu od 0 do 29, zwiększając zmiennej licznika co 2 sekundy. Po co zwiększenie licznika przepływ pracy będzie się powtarzać, a podwyższone właściwości są aktualizowane w [dbo]. Widok [counterService]. Po uruchomieniu aplikacji konsoli hostuje usługę WF i wysyła komunikat do `Start` punktu końcowego, tworząc wystąpienie licznika WF.  
  
-   **PropertyPromotionActivity** to biblioteka klasy, która zawiera elementy konfiguracji, działania przepływu pracy i rozszerzenia przepływu pracy, **CounterServiceApplication** używa.  
  
-   **PropertyPromotionActivitySQLSample.sql** tworzy i dodaje widok [dbo]. [ CounterService] w bazie danych.  
  
### <a name="counterserviceapplication"></a>CounterServiceApplication  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a>Za pomocą SqlWorkflowInstanceStorePromotion elementu konfiguracji  
 `SqlWorkflowInstanceStorePromotion` Dziedziczy po elemencie konfiguracji `SqlWorkflowInstanceStore` element konfiguracji, ale dodaje element dodatkowe czynności konfiguracyjne o nazwie `promotionSets`. `promotionSets` Element umożliwia użytkownikowi określenie właściwości o podwyższonym poziomie konfiguracji. Jest to plik konfiguracyjny, który jest używany przez przykładowy:  
  
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
  
 Sprawdź definicję [dbo]. Widok [counterService].  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 Gdy wystąpienie przepływu pracy będzie się powtarzać, zostanie wstawiona do `InstancePromotedProperties` Wyświetl dla każdego `PromotionSet` zdefiniowane w konfiguracji. Ten wiersz zawiera wszystkie o podwyższonym poziomie właściwości `PromotionSet` (podwyższony jedną właściwość w kolumnie). To `PromotionSet` jest kluczach krotki: `InstanceId, PromotionName`. W tym przykładzie mamy jeden `PromotionSet` zdefiniowane w konfiguracji, których atrybut name jest `CounterService`. Uwaga jak `PromotionName` wartość kolumny jest równa atrybut name elementu `PromotionSet` elementu.  
  
 Kolejność `promotedValue` elementy mają związek z położenie o podwyższonym poziomie właściwości w `InstancePromotedProperties` widoku. `Count` jest to pierwszy `promotedValue` elementu. W rezultacie jest mapowany na `Value1` kolumny w `InstancePromotedProperties` widoku. `LastIncrementedAt` jest to druga `promotedValue` elementu. W rezultacie jest mapowany na `Value2` kolumny w `InstancePromotedProperties` widoku.  
  
#### <a name="using-the-promotevalue-activity"></a>Przy użyciu działania PromoteValue  
 Zapoznaj się z plikiem CounterService.xamlx w Projektancie Windows Workflow Foundation. Zwróć uwagę, że istnieją dwa specjalne działania w definicji WF: `PromoteValue<DateTime>` i `PromoteValue<Int32>`.  
  
 `PromoteValue<Int32>` Działanie ma jego `Name` zdefiniowany jako element członkowski `Count`. To jest zgodny z pierwszym `promotedValue` element w konfiguracji i ma jego `Value` zdefiniowany jako `Counter` zmiennej przepływu pracy. Gdy przepływ pracy będzie się powtarzać, `Counter` zmiennej przepływu pracy jest trwały jako właściwości z podwyższonym poziomem do `Value1` kolumny `InstancePromotedProperties` widoku.  
  
 `PromoteValue<DateTime>` Działanie ma jego `Name` zdefiniowany jako element członkowski `LastIncrementedAt`. Odpowiada to drugi `promotedValue` element w konfiguracji i jego `Value` zdefiniowany jako `TimeLastIncremented` zmiennej przepływu pracy. Oznacza to, że gdy przepływ pracy będzie się powtarzać, wartość `TimeLastIncremented` zmiennej przepływu pracy zostaną utrwalone jako właściwości z podwyższonym poziomem do `Value2` kolumny `InstancePromotedProperties` widoku.  
  
 Należy pamiętać, że `PromotedValue` działanie ma również logiczna składową o nazwie `ClearExistingPromotedData`. Gdy ten element członkowski jest ustawiona na `true`, czyści wszystkie wartości właściwości z podwyższonym poziomem do tego punktu w przepływie pracy. Na przykład jeśli działanie sekwencji jest zdefiniowany jako następująco:  
  
1.  PromoteValue {nazwa = "Count", wartość = 3}  
  
2.  PromoteValue {nazwa = "LastIncrementedAt", wartość = 1-1-2000}  
  
3.  Utrwalanie  
  
4.  PromoteValue {nazwa = "Count", wartość = 4, ClearExistingPromotedData = true}  
  
5.  Utrwalanie  
  
 Na drugiej utrwalanie, wartość o podwyższonym poziomie `Count` będzie równa 4. Jednak wartość o podwyższonym poziomie `LastIncrementedAt` będzie `NULL`. Jeśli `ClearExistingPromotedData` nie został ustawiony na `true` w kroku 4, po drugim utrwalanie, o podwyższonym poziomie wartość licznika będzie 4. W wyniku wartość o podwyższonym poziomie `LastIncrementedAt` nadal będzie 1-1-2000.  
  
### <a name="propertypromotionactivity"></a>PropertyPromotionActivity  
 Ta biblioteka klas zawiera następujące klasy publiczne można uproszczenie użytkowania <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcja podwyższania poziomu.  
  
#### <a name="promotevalue-class"></a>Klasa PromoteValue  
 Ta klasa promuje jedną właściwość. Nazwa właściwości z podwyższonym poziomem powinny odpowiadać nazwa atrybutu `promotedValue` element w konfiguracji. To działanie może być używane w Projektancie przepływu pracy. Zobacz CounterServiceApplication, na przykład użycia.  
  
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
 Czyści wszystkie wartości, które były promowane przed tym działaniem.  
  
 Nazwa (ciąg)  
 Nazwa która reprezentuje tej właściwości. Powinien on odpowiadać atrybut name elementu \<promotedValue > element w konfiguracji.  
  
 Wartość (InArgument\<T >)  
 Zmienna / wartość, że chcesz przechowywać w kolumnie.  
  
#### <a name="promotevalues-class"></a>Klasa PromoteValues  
 Wspiera wiele właściwości. Nazwy właściwości o podwyższonym poziomie powinny odpowiadać wszystkie atrybuty nazwy w `promotedValue` elementów w konfiguracji. Użycie jest podobny do `PromoteValue` działań, z wyjątkiem fakt, że wiele właściwości atrybutu może być podwyższony, w tym samym czasie. To działanie nie może być używane w Projektancie przepływu pracy.  
  
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
 Pochodzi od klasy `SqlWorkflowInstanceStoreBehavior`. Ta klasa pochodna dodaje niestandardowego uczestnika stanów trwałych (również część z tej biblioteki) jako rozszerzenia przepływu pracy. Implementacja poprzednich dwóch działań przepływu pracy, zależy od tego niestandardowego uczestnika stanów trwałych.  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 Ta biblioteka klas zawiera także `ConfigurationElement` implementację `SqlWorkflowInstanceStorePromotionElement` i niestandardowego uczestnika stanów trwałych używany przez poprzednie działania podwyższania poziomu.  
  
### <a name="propertypromotionactivitysqlsample"></a>PropertyPromotionActivitySQLSample  
 Ten plik SQL tworzy `[dbo].[CounterService]` wyświetlanie oprócz `[InstancePromotedProperties]` widoku dla zapytań, wszystkie wystąpienia, które mają zestaw CounterService podwyższania poziomu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
