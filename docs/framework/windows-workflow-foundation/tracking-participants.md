---
title: Uczestnicy śledzenia
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 45a92c3ab710fc9bc86fbf269a4672f1d34737cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963673"
---
# <a name="tracking-participants"></a>Uczestnicy śledzenia
Monitorowanie uczestników to punkty rozszerzalności, które umożliwiają deweloperom przepływu <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> pracy dostęp do obiektów i przetwarzanie ich. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]zawiera standardowy Uczestnik śledzenia, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń systemu Windows (ETW). Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.  
  
## <a name="tracking-participants"></a>Uczestnicy śledzenia  
 Infrastruktura śledzenia umożliwia stosowanie filtru dla wychodzących rekordów śledzenia, tak aby uczestnik mógł subskrybować podzestaw rekordów. Mechanizm zastosowania filtru jest profilem śledzenia.  
  
 Windows Workflow Foundation (WF) w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] programie udostępnia uczestnika śledzenia, który zapisuje rekordy śledzenia w sesji ETW. Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji. Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń. Przykład zestawu SDK na potrzeby śledzenia przy użyciu funkcji ETW jest dobrym sposobem na zapoznanie się ze śledzeniem WF za pomocą uczestnika śledzenia funkcji ETW.  
  
## <a name="etw-tracking-participant"></a>Uczestnik śledzenia ETW  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]obejmuje uczestnika śledzenia funkcji ETW, który zapisuje rekordy śledzenia w sesji ETW. Jest to realizowane w bardzo wydajny sposób z minimalnym wpływem na wydajność aplikacji lub przepływności serwera. Zaletą korzystania z standardowego uczestnika śledzenia ETW jest to, że otrzymane rekordy śledzenia mogą być wyświetlane z innymi dziennikami aplikacji i systemu w Podgląd zdarzeń systemu Windows.  
  
 Uczestnik standardowego śledzenia ETW jest konfigurowany w pliku Web. config, jak pokazano w poniższym przykładzie.  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Jeśli nazwa nie zostanie określona, na przykład tylko `<etwTracking/>` lub `<etwTracking profileName=""/>`, zostanie użyty domyślny profil śledzenia instalowany z [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w pliku Machine. config. `trackingProfile`  
  
 W pliku Machine. config domyślny profil śledzenia subskrybuje rekordy wystąpienia przepływu pracy i błędy.  
  
 W funkcji ETW zdarzenia są zapisywane w sesji ETW za pomocą identyfikatora dostawcy. Identyfikator dostawcy, którego Uczestnik śledzenia funkcji ETW używa do zapisywania rekordów śledzenia w funkcji ETW, jest zdefiniowany w sekcji Diagnostyka w pliku Web. config (w obszarze `<system.serviceModel><diagnostics>`). Domyślnie Uczestnik śledzenia ETW używa domyślnego identyfikatora dostawcy, gdy nie został określony, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 Na poniższej ilustracji przedstawiono przepływ danych śledzenia za pomocą uczestnika śledzenia funkcji ETW. Po osiągnięciu przez dane śledzenia sesji ETW można uzyskać do niej dostęp na wiele sposobów. Jednym z najbardziej przydatnych sposobów uzyskiwania dostępu do tych zdarzeń jest Podgląd zdarzeń, typowe narzędzie systemu Windows służące do wyświetlania dzienników i śladów z aplikacji i usług.  
  
 ![Przepływ danych śledzenia za pomocą dostawcy śledzenia ETW.](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a>Śledzenie danych zdarzeń uczestników  
 Uczestnik śledzenia serializować śledzone dane zdarzenia do sesji ETW w formacie jednego zdarzenia dla każdego rekordu śledzenia.  Zdarzenie jest identyfikowane przy użyciu identyfikatora z zakresu od 100 do 199. Aby zapoznać się z definicjami rekordów zdarzeń śledzenia emitowanych przez uczestnika śledzenia, zobacz temat [Informacje o śledzeniu zdarzeń](tracking-events-reference.md) .  
  
 Rozmiar zdarzenia ETW jest ograniczony przez rozmiar buforu ETW lub przez maksymalny ładunek zdarzenia ETW, w zależności od tego, która wartość jest mniejsza. Jeśli rozmiar zdarzenia przekracza jeden z tych limitów ETW, zdarzenie jest obcinane i jego zawartość została usunięta w dowolny sposób. Zmienne, argumenty, adnotacje i dane niestandardowe nie są selektywnie usuwane. W przypadku obcinania wszystkie z nich są obcinane niezależnie od wartości, która spowodowała przekroczenie limitu ETW przez rozmiar zdarzenia.  Usunięte dane zostaną zastąpione `<item>..<item>`.  
  
 Typy złożone w zmiennych, argumentach i niestandardowych elementach danych są serializowane do rekordu zdarzenia ETW przy użyciu [klasy NetDataContractSerializer](https://go.microsoft.com/fwlink/?LinkId=177537). Ta klasa zawiera informacje o typie CLR w serializowanej parze XML.  
  
 Obcinanie danych ładunku ze względu na limity ETW może spowodować, że rekordy śledzenia zduplikowane są wysyłane do sesji ETW. Taka sytuacja może wystąpić, jeśli więcej niż jedna sesja nasłuchuje zdarzeń, a sesje mają różne limity ładunku dla zdarzeń.  
  
 Dla sesji o niższym limicie zdarzenie może zostać obcięte. Uczestnik śledzenia ETW nie ma żadnej informacji o liczbie sesji nasłuchujących zdarzeń; Jeśli zdarzenie zostanie obcięte dla sesji, uczestnik ETW ponawia próbę wysłania zdarzenia raz. W takim przypadku sesja, która jest skonfigurowana do akceptowania większego rozmiaru ładunku, spowoduje dwa razy zdarzenie (zdarzenie obcięte i obcięte). Duplikowanie może być uniemożliwione przez skonfigurowanie wszystkich sesji ETW o tym samym limicie rozmiaru buforu.  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a>Uzyskiwanie dostępu do śledzenia danych z uczestnika ETW w Podgląd zdarzeń  
 Do zdarzeń, które są zapisywane w sesji ETW przez uczestnika śledzenia ETW, można uzyskać dostęp za pośrednictwem Podgląd zdarzeń (przy użyciu domyślnego identyfikatora dostawcy). Pozwala to na szybkie wyświetlanie rekordów śledzenia, które zostały wyemitowane przez przepływ pracy.  
  
> [!NOTE]
> Śledzone zdarzenia rejestrowania wyemitowane do sesji ETW używają identyfikatorów zdarzeń z zakresu od 100 do 199.  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a>Aby włączyć wyświetlanie rekordów śledzenia w Podgląd zdarzeń  
  
1. Uruchom Podgląd zdarzeń (EVENTVWR. EXE  
  
2. Wybierz **Podgląd zdarzeń, Dzienniki aplikacji i usług, Microsoft, Windows, serwer aplikacji-aplikacje**.  
  
3. Kliknij prawym przyciskiem myszy i sprawdź, czy wybrano opcję **Widok, Pokaż dzienniki analityczne i debugowania** . Jeśli nie, zaznacz ją, aby znacznik wyboru pojawił się obok niego. Spowoduje to wyświetlenie dzienników **analitycznych**, **wydajności**i **debugowania** .  
  
4. Kliknij prawym przyciskiem myszy dziennik analityczny, a następnie wybierz pozycję **Włącz dziennik**. Dziennik będzie istnieć w pliku%SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications% 4 A nalytic. etl.  
  
## <a name="custom-tracking-participant"></a>Uczestnik śledzenia niestandardowego  
 Interfejs API uczestnika śledzenia umożliwia rozszerzenie środowiska uruchomieniowego śledzenia z uczestnikiem śledzenia dostarczonym przez użytkownika, który może zawierać logikę niestandardową do obsługi rekordów śledzenia emitowanych przez środowisko uruchomieniowe przepływu pracy. Aby napisać niestandardowego uczestnika śledzenia, Deweloper musi zaimplementować `Track` metodę <xref:System.Activities.Tracking.TrackingParticipant> w klasie. Ta metoda jest wywoływana, gdy rekord śledzenia jest emitowany przez środowisko uruchomieniowe przepływu pracy.  
  
 Śledzenie uczestników pochodzi od <xref:System.Activities.Tracking.TrackingParticipant> klasy. Dostarczone <xref:System.Activities.Tracking.EtwTrackingParticipant> przez system, emituje zdarzenie śledzenia zdarzeń dla systemu Windows (ETW) dla każdego odebranego rekordu śledzenia. Aby utworzyć niestandardowego uczestnika śledzenia, tworzona jest Klasa, która pochodzi od <xref:System.Activities.Tracking.TrackingParticipant>. Aby zapewnić podstawowe funkcje śledzenia, Przesłoń <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>jest wywoływana, gdy rekord śledzenia jest wysyłany przez środowisko uruchomieniowe i może być przetwarzany w odpowiedni sposób. W poniższym przykładzie zdefiniowano klasę niestandardowego uczestnika śledzenia, która emituje wszystkie rekordy śledzenia do okna konsoli. Można również zaimplementować <xref:System.Activities.Tracking.TrackingParticipant> obiekt, który przetwarza rekordy śledzenia asynchronicznie `BeginTrack` przy użyciu metod i `EndTrack`  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 Aby użyć określonego uczestnika śledzenia, zarejestruj go przy użyciu wystąpienia przepływu pracy, które chcesz śledzić, jak pokazano w poniższym przykładzie.  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 W poniższym przykładzie zostanie utworzony przepływ pracy, który obejmuje <xref:System.Activities.Statements.Sequence> działanie <xref:System.Activities.Statements.WriteLine> zawierające działanie. `ConsoleTrackingParticipant` Zostanie dodany do rozszerzeń, a przepływ pracy jest wywoływany.  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a>Zobacz także

- [Monitorowanie aplikacji sieci szkieletowej systemu Windows Server](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorowanie aplikacji przy użyciu sieci szkieletowej aplikacji](https://go.microsoft.com/fwlink/?LinkId=201275)
