---
title: "Uczestników śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8159be53ed202be5e0338cbf671122661f0d814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="tracking-participants"></a>Uczestników śledzenia
Uczestników śledzenia są punktów rozszerzalności, zezwalających na dewelopera przepływu pracy, aby uzyskać dostęp do <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> obiektów i ich przetworzenia. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]obejmuje uczestnika standardowe śledzenia, który zapisuje rekordy śledzenia jako zdarzenia funkcji Śledzenie zdarzeń systemu Windows (). Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.  
  
## <a name="tracking-participants"></a>Uczestników śledzenia  
 Infrastruktura śledzenia umożliwia zastosowania filtru wychodzących rekordów śledzenia tak, aby uczestnika mogą subskrybować podzestaw rekordów. Mechanizm, aby zastosować filtr jest za pośrednictwem profilu śledzenia.  
  
 [!INCLUDE[wf](../../../includes/wf-md.md)]w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] zapewnia uczestnika śledzenia, który zapisuje rekordy śledzenia w sesji usługi ETW. Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji. Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń. Przykład zestawu SDK do śledzenia na podstawie ETW jest to dobry sposób na zapoznanie się z śledzenia WF przy użyciu uczestnika na podstawie ETW śledzenia.  
  
## <a name="etw-tracking-participant"></a>Uczestnik śledzenia funkcji ETW  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]obejmuje ETW śledzenia uczestnika, który zapisuje rekordy śledzenia w sesji usługi ETW. Jest to realizowane w bardzo wydajny sposób z minimalnym wpływem na wydajność aplikacji lub przepływność serwera. Zaletą używania standardowych uczestnika śledzenia zdarzeń systemu Windows jest rekordów śledzenia, który odbiera mogą być wyświetlane z innej aplikacji, a system dzienniki w Podglądzie zdarzeń systemu Windows.  
  
 Standardowa uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config, jak pokazano w poniższym przykładzie.  
  
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
>  Jeśli `trackingProfile` nie określono nazwy, takie jak właśnie `<etwTracking/>` lub `<etwTracking profileName=""/>`, a następnie domyślnie instalowane z profilu śledzenia [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w pliku Machine.config plik jest używany.  
  
 W pliku Machine.config domyślnego profilu śledzenia subskrybuje rekordów wystąpienia przepływu pracy i usterek.  
  
 W funkcji ETW zdarzenia są zapisywane w sesji usługi ETW za pomocą identyfikatora dostawcy. Dostawca identyfikator, który rejestruje ETW śledzenia uczestnika używana do pisania śledzenia do funkcji ETW jest zdefiniowany w sekcji Diagnostyka pliku Web.config (w obszarze `<system.serviceModel><diagnostics>`). Domyślnie uczestnika śledzenia zdarzeń systemu Windows używa domyślny identyfikator dostawcy podczas nie zostało określone, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 Na poniższej ilustracji przedstawiono przepływ danych za pośrednictwem uczestnika śledzenia funkcji ETW śledzenia. Gdy dane śledzenia osiągnie sesja funkcji ETW, jest dostępny na kilka sposobów. Jest jednym z najbardziej przydatnych sposobów dostęp do tych zdarzeń w Podglądzie zdarzeń, typowe narzędzia systemu Windows używane do wyświetlania dzienników i danych śledzenia z aplikacji i usług.  
  
 ![Przepływ śledzenia i dostawcy śledzenia zdarzeń systemu Windows](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")  
  
## <a name="tracking-participant-event-data"></a>Dane śledzenia zdarzeń uczestnika  
 Uczestnik śledzenia serializuje dane śledzonych zdarzeń w sesji usługi ETW w formacie jedno zdarzenie na rekord śledzenia.  Zdarzenie jest identyfikowane za pomocą Identyfikatora w zakresie od 100 do 199. Definicje zdarzeń śledzenia rekordy emitowane przez uczestnika śledzenia, zobacz [odwołanie śledzenia zdarzeń](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) tematu.  
  
 Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub przez maksymalną ładunku zdarzenia ETW, niezależnie od wartości jest mniejsza. Jeśli rozmiar zdarzenia przekracza jednej z tych limitów ETW, zdarzenie zostanie obcięta i jego zawartość usuwana w dowolny sposób. Zmienne, argumentów i adnotacje danych niestandardowych nie są selektywnie usunąć. W przypadku obcięcia wszystkie te są obcinane niezależnie od wartości, który spowodował rozmiar zdarzenia ETW limitu.  Usunięte dane są zastępowane `<item>..<item>`.  
  
 Złożone typy w zmiennych, argumentów i elementy niestandardowe dane są serializowane używa rekordu zdarzenia ETW [klasy NetDataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=177537). Ta klasa zawiera informacje o typie CLR w serializowanym strumień XML.  
  
 Może spowodować obcięcie ładunek danych z powodu ograniczeń ETW śledzenia zduplikowane rekordy są wysyłane do sesji ETW. Może to wystąpić, jeśli więcej niż jedna sesja nasłuchuje zdarzeń i sesje mają różne ładunku limity dla zdarzeń.  
  
 W sesji z dolnej granicy zdarzenie może zostać obcięty. Uczestnik śledzenia funkcji ETW nie ma żadnych wiedzy na temat liczby sesji nasłuchiwanie zdarzeń; Jeśli zdarzenie jest obcinana do sesji, a następnie ETW uczestnika ponawia próbę wysłania zdarzenia raz. W takim przypadku sesji, który jest skonfigurowany do akceptowania większy rozmiar ładunku wystąpi dwukrotnie zdarzeń (zdarzenie-obcięty i obcięte). Duplikowanie można zapobiec przez skonfigurowanie wszystkich sesji funkcji ETW z tym samym limity rozmiaru buforu.  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a>Uzyskiwanie dostępu do danych śledzenia od uczestnika ETW w Podglądzie zdarzeń  
 Zdarzenia, które są zapisywane w sesji usługi ETW za uczestnika śledzenia funkcji ETW są dostępne za pomocą Podglądu zdarzeń (w przypadku używania domyślny identyfikator dostawcy). Umożliwia to szybkie wyświetlanie śledzenia rekordów, które zostały wyemitowane przez przepływ pracy.  
  
> [!NOTE]
>  Śledzenie zdarzeń rekordów wysyłanego do ETW sesji Użyj identyfikatorów zdarzeń w zakresie od 100 do 199.  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a>Aby włączyć wyświetlanie w Podglądzie zdarzeń śledzenia rekordów  
  
1.  Uruchomienie podglądu zdarzeń (EVENTVWR. WYWOŁANIE PLIKU EXE)  
  
2.  Wybierz **Podgląd zdarzeń, dzienniki aplikacji i usług, aplikacji serwera firmy Microsoft, Windows, aplikacji**.  
  
3.  Kliknij prawym przyciskiem myszy i upewnij się, że **widoku, Pokaż dzienniki analityczne i debugowania** jest zaznaczone. Jeśli nie, zaznacz go, pojawi się znacznik wyboru obok niej. Spowoduje to wyświetlenie **analityczne**, **wydajności**, i **debugowania** dzienniki.  
  
4.  Kliknij prawym przyciskiem myszy **analityczne** logowania, a następnie wybierz **Włącz dziennik**. Dziennik będą istniały w pliku Server-Applications%4Analytic.etl %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application.  
  
## <a name="custom-tracking-participant"></a>Niestandardowe śledzenia uczestnika  
 Uczestnik śledzenia interfejsu API umożliwia rozszerzenie środowiska uruchomieniowego śledzenia z uczestnika śledzenia dostarczane przez użytkownika, który może obejmować niestandardowej logiki do obsługi rekordów śledzenia emitowane przez środowisko wykonawcze przepływu pracy. Aby napisać uczestnika śledzenia niestandardowych, deweloper musi implementować `Track` metoda <xref:System.Activities.Tracking.TrackingParticipant> klasy. Ta metoda jest wywoływana, gdy rekord śledzenia są emitowane przez środowisko uruchomieniowe przepływu pracy.  
  
 Uczestników śledzenia pochodzi od <xref:System.Activities.Tracking.TrackingParticipant> klasy. Dostarczane przez system <xref:System.Activities.Tracking.EtwTrackingParticipant> emituje zdarzenie zdarzenia śledzenia zdarzeń systemu Windows (ETW) dla każdego rekordu śledzenia odebrane. Aby utworzyć niestandardowe śledzenia uczestnika, klasa zostanie utworzony pochodną <xref:System.Activities.Tracking.TrackingParticipant>. Aby umożliwić korzystanie z funkcji śledzenia podstawowego, Przesłoń <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>jest wywoływane, gdy rekord śledzenia są wysyłane przez środowisko wykonawcze i mogą być przetwarzane w żądany sposób. W poniższym przykładzie klasa uczestnika śledzenia niestandardowych zdefiniowano który emituje wszystkie rekordy śledzenia w oknie konsoli. Można też wdrożyć <xref:System.Activities.Tracking.TrackingParticipant> rejestruje obiekt, który przetwarza dane śledzenia asynchronicznie za pomocą jego `BeginTrack` i `EndTrack` metody  
  
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
  
 Aby użyć uczestnika określonego śledzenia, należy go zarejestrować z wystąpieniem przepływu pracy, który chcesz śledzić, jak pokazano w poniższym przykładzie.  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 W poniższym przykładzie przepływ pracy składający się z <xref:System.Activities.Statements.Sequence> działania, który zawiera <xref:System.Activities.Statements.WriteLine> utworzeniu działania. `ConsoleTrackingParticipant` Zostanie dodany do rozszerzeń i przepływ pracy jest wywoływana.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
