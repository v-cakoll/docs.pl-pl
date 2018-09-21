---
title: Uczestnicy śledzenia
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: e346e0df3417f6ac83854bd96d6e64dcf103ea93
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46518808"
---
# <a name="tracking-participants"></a>Uczestnicy śledzenia
Śledzenie uczestników są punkty rozszerzeń, zezwalających na dewelopera przepływu pracy, aby uzyskać dostęp do <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> obiektów i ich przetwarzania. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] zawiera standardowe śledzenia uczestnika, który zapisuje rekordy śledzenia jako zdarzenia śledzenie zdarzeń dla Windows (ETW). Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.  
  
## <a name="tracking-participants"></a>Uczestnicy śledzenia  
 Infrastruktura śledzenia umożliwia stosowanie filtru na wychodzące rekordów śledzenia tak, aby uczestnika, który może być subskrybowana przez podzestaw rekordów. Mechanizm, aby zastosować filtr jest za pośrednictwem profilu śledzenia.  
  
 Windows Workflow Foundation (WF) w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] zapewnia śledzenia uczestnika, który zapisuje rekordy śledzenia sesji funkcji ETW. Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji. Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń. Przykładowy zestaw SDK dla opartych na funkcji ETW śledzenia jest dobrym sposobem na zapoznanie się z WF śledzenia przy użyciu opartych na funkcji ETW śledzenia uczestnika śledzenia.  
  
## <a name="etw-tracking-participant"></a>Uczestnika śledzenia zdarzeń systemu Windows  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] obejmuje ETW śledzenia uczestnika, który zapisuje rekordy śledzenia sesji funkcji ETW. Odbywa się to w bardzo wydajny sposób z minimalnym wpływem na wydajność aplikacji lub przepływność serwera. Zaletą standardowe uczestnika śledzenia zdarzeń systemu Windows jest, czy rekordy śledzenia, który odbiera mogą być wyświetlane z innych aplikacji i systemem dzienniki w Podglądzie zdarzeń Windows.  
  
 Standardowe uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config, jak pokazano w poniższym przykładzie.  
  
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
>  Jeśli `trackingProfile` nie określono nazwy, takie jak właśnie `<etwTracking/>` lub `<etwTracking profileName=""/>`, a następnie domyślną śledzenia profil jest zainstalowany za pomocą [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w pliku Machine.config plik jest używany.  
  
 W pliku Machine.config domyślny profil śledzenia subskrybuje rekordów wystąpienia przepływu pracy i usterek.  
  
 W funkcji ETW zdarzenia są zapisywane w sesji ETW za pomocą identyfikatora dostawcy. Dostawca identyfikator, który ETW śledzenia uczestnika używa do tworzenia śledzenia rekordów zdarzeń systemu Windows jest zdefiniowany w sekcji Diagnostyka pliku Web.config (w obszarze `<system.serviceModel><diagnostics>`). Domyślnie uczestnika śledzenia zdarzeń systemu Windows używa domyślny identyfikator dostawcy podczas nie zostało określone, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 Poniższa ilustracja przedstawia przepływ danych za pomocą funkcji ETW śledzenia uczestnika śledzenia. Gdy dane śledzenia osiągnie sesja funkcji ETW, możliwy jest wiele sposobów. Jest jednym z najbardziej przydatnych sposobów uzyskać dostęp do tych zdarzeń za pomocą Podglądu zdarzeń, popularnego narzędzia Windows używane do wyświetlania dzienników i ślady z aplikacji i usług.  
  
 ![Przepływ śledzenia i dostawcy śledzenia funkcji ETW](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")  
  
## <a name="tracking-participant-event-data"></a>Dane zdarzeń uczestników śledzenia  
 Śledzenia uczestnika, który serializuje dane zdarzeń rejestrowanych w formacie jedno zdarzenie na rekord śledzenia sesji funkcji ETW.  Zdarzenie jest identyfikowane za pomocą Identyfikatora w zakresie od 100 do 199. Dla definicji zdarzeń śledzenia rekordów emitowane przez uczestnika śledzenia, zobacz [śledzenia informacje o zdarzeniach](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) tematu.  
  
 Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW, lub przez maksymalne ładunek zdarzenia ETW, niezależnie od wartości jest mniejsza. Jeśli rozmiar zdarzenia przekracza jedną z tych limitów ETW, zostanie obcięta zdarzenia i jego zawartość usunięta w dowolny sposób. Zmienne, argumenty, adnotacji i danych niestandardowych nie są selektywnie usunąć. W przypadku obcinania wszystkie te są obcinane niezależnie od wartości, który spowodował rozmiar zdarzenia przekracza ETW limit.  Usunięto dane są zastępowane `<item>..<item>`.  
  
 Złożone typy w zmiennych argumentów, a elementy niestandardowe dane są szeregowane do ETW zdarzenia rekordu przy użyciu [klasy NetDataContractSerializer](https://go.microsoft.com/fwlink/?LinkId=177537). Ta klasa zawiera informacje o typie CLR w Zserializowany strumień XML.  
  
 Obcięcie danych ładunku z powodu ograniczeń ETW może spowodować zduplikowane śledzenia rekordów, które są wysyłane do sesji funkcji ETW. Może to wystąpić, jeśli więcej niż jedna sesja nasłuchuje zdarzeń i sesje mają różne ładunku limity dla zdarzeń.  
  
 W sesji z dolną granicę zdarzenia mogą być obcinane. Uczestnika śledzenia zdarzeń systemu Windows nie ma żadnej wiedzy liczbę sesji nasłuchiwanie zdarzeń; Jeśli zdarzenie jest tutaj obcięto je dla sesji, a następnie ETW uczestnika ponawia próbę wysłania zdarzenia jeden raz. W tym przypadku sesji który jest skonfigurowany do akceptowania większy rozmiar ładunku otrzyma dwukrotnie zdarzeń (zdarzenie-obcięty i obcięte). Duplikowanie można zapobiec, konfigurując wszystkie sesje ETW za pomocą tych samych ograniczeń rozmiaru buforu.  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a>Uzyskiwanie dostępu do danych śledzenia z uczestnika zdarzeń systemu Windows w Podglądzie zdarzeń  
 Zdarzenia, które są zapisywane w sesji funkcji ETW przez uczestnika śledzenia zdarzeń systemu Windows są dostępne za pomocą Podglądu zdarzeń (w przypadku używania domyślny identyfikator dostawcy). Pozwala to na szybkie przeglądanie śledzenia rekordów, które zostały wyemitowane przez przepływ pracy.  
  
> [!NOTE]
>  Śledzenie zdarzeń rekordów emitowany do ETW sesji Użyj identyfikatorów zdarzeń z zakresu od 100 do 199.  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a>Aby umożliwić wyświetlanie rekordów śledzenia w Podglądzie zdarzeń  
  
1.  Uruchomienie podglądu zdarzeń (EVENTVWR. Z ROZSZERZENIEM EXE)  
  
2.  Wybierz **Podgląd zdarzeń, dzienniki aplikacji i usług, aplikacji serwera firmy Microsoft, Windows, aplikacji**.  
  
3.  Kliknij prawym przyciskiem myszy i upewnij się, że **widoku, Pokaż dzienniki analityczne i debugowania** jest zaznaczone. Jeśli nie, wybierz ją, dzięki czemu pojawi się znacznik wyboru obok niego. Spowoduje to wyświetlenie **analityczne**, **wydajności**, i **debugowania** dzienniki.  
  
4.  Kliknij prawym przyciskiem myszy **analityczne** logowania, a następnie wybierz pozycję **Włącz dziennik**. Dziennik będzie istnieć w pliku Server-Applications%4Analytic.etl %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application.  
  
## <a name="custom-tracking-participant"></a>Niestandardowego uczestnika śledzenia  
 Uczestnika śledzenia interfejsu API umożliwia rozszerzenie środowiska uruchomieniowego śledzenia przy użyciu podanego przez użytkownika śledzenia uczestnika, który może zawierać niestandardowej logiki do obsługi rekordów śledzenia emitowane przez środowisko wykonawcze przepływów pracy. Aby napisać uczestnikiem niestandardowe śledzenia, deweloper musi implementować `Track` metody <xref:System.Activities.Tracking.TrackingParticipant> klasy. Ta metoda jest wywoływana, gdy rekord śledzenia jest emitowane przez środowisko wykonawcze przepływów pracy.  
  
 Uczestnicy śledzenia pochodzić od <xref:System.Activities.Tracking.TrackingParticipant> klasy. Dostarczane przez system <xref:System.Activities.Tracking.EtwTrackingParticipant> emituje zdarzenia zdarzeń śledzenia dla Windows (ETW) dla każdego rekordu śledzenia, która została odebrana. Aby utworzyć niestandardowego uczestnika śledzenia, klasa jest tworzona, jest pochodną <xref:System.Activities.Tracking.TrackingParticipant>. Aby zapewnić funkcjonalność śledzenia podstawowego, należy zastąpić <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> jest wywoływana, gdy rekord śledzenia są wysyłane przez środowisko uruchomieniowe i mogą być przetwarzane w żądany sposób. W poniższym przykładzie zdefiniowano klasę uczestnika śledzenia niestandardowego, który emituje wszystkich rekordów śledzenia w oknie konsoli. Możesz również wdrożyć <xref:System.Activities.Tracking.TrackingParticipant> obiektu, który przetwarza dane śledzenia rekordów, asynchronicznie przy użyciu jego `BeginTrack` i `EndTrack` metody  
  
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
  
 Aby użyć konkretnego śledzenia uczestnika, należy go zarejestrować z wystąpieniem przepływu pracy, który chcesz śledzić, jak pokazano w poniższym przykładzie.  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 W poniższym przykładzie przepływ pracy składający się z <xref:System.Activities.Statements.Sequence> działania, który zawiera <xref:System.Activities.Statements.WriteLine> utworzeniu działania. `ConsoleTrackingParticipant` Jest dodawany do rozszerzeń i przepływ pracy jest wywoływana.  
  
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
 [Windows Server AppFabric monitorowania](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=201275)
