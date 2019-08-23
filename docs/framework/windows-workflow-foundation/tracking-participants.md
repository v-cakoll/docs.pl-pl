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
# <a name="tracking-participants"></a><span data-ttu-id="61b5f-102">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="61b5f-102">Tracking Participants</span></span>
<span data-ttu-id="61b5f-103">Monitorowanie uczestników to punkty rozszerzalności, które umożliwiają deweloperom przepływu <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> pracy dostęp do obiektów i przetwarzanie ich.</span><span class="sxs-lookup"><span data-stu-id="61b5f-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="61b5f-104">zawiera standardowy Uczestnik śledzenia, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="61b5f-104">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="61b5f-105">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="61b5f-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="61b5f-106">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="61b5f-106">Tracking Participants</span></span>  
 <span data-ttu-id="61b5f-107">Infrastruktura śledzenia umożliwia stosowanie filtru dla wychodzących rekordów śledzenia, tak aby uczestnik mógł subskrybować podzestaw rekordów.</span><span class="sxs-lookup"><span data-stu-id="61b5f-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="61b5f-108">Mechanizm zastosowania filtru jest profilem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="61b5f-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="61b5f-109">Windows Workflow Foundation (WF) w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] programie udostępnia uczestnika śledzenia, który zapisuje rekordy śledzenia w sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="61b5f-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="61b5f-110">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="61b5f-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="61b5f-111">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="61b5f-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="61b5f-112">Przykład zestawu SDK na potrzeby śledzenia przy użyciu funkcji ETW jest dobrym sposobem na zapoznanie się ze śledzeniem WF za pomocą uczestnika śledzenia funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="61b5f-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="61b5f-113">Uczestnik śledzenia ETW</span><span class="sxs-lookup"><span data-stu-id="61b5f-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="61b5f-114">obejmuje uczestnika śledzenia funkcji ETW, który zapisuje rekordy śledzenia w sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="61b5f-114">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="61b5f-115">Jest to realizowane w bardzo wydajny sposób z minimalnym wpływem na wydajność aplikacji lub przepływności serwera.</span><span class="sxs-lookup"><span data-stu-id="61b5f-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="61b5f-116">Zaletą korzystania z standardowego uczestnika śledzenia ETW jest to, że otrzymane rekordy śledzenia mogą być wyświetlane z innymi dziennikami aplikacji i systemu w Podgląd zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="61b5f-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="61b5f-117">Uczestnik standardowego śledzenia ETW jest konfigurowany w pliku Web. config, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="61b5f-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="61b5f-118">Jeśli nazwa nie zostanie określona, na przykład tylko `<etwTracking/>` lub `<etwTracking profileName=""/>`, zostanie użyty domyślny profil śledzenia instalowany z [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w pliku Machine. config. `trackingProfile`</span><span class="sxs-lookup"><span data-stu-id="61b5f-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="61b5f-119">W pliku Machine. config domyślny profil śledzenia subskrybuje rekordy wystąpienia przepływu pracy i błędy.</span><span class="sxs-lookup"><span data-stu-id="61b5f-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="61b5f-120">W funkcji ETW zdarzenia są zapisywane w sesji ETW za pomocą identyfikatora dostawcy.</span><span class="sxs-lookup"><span data-stu-id="61b5f-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="61b5f-121">Identyfikator dostawcy, którego Uczestnik śledzenia funkcji ETW używa do zapisywania rekordów śledzenia w funkcji ETW, jest zdefiniowany w sekcji Diagnostyka w pliku Web. config (w obszarze `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="61b5f-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="61b5f-122">Domyślnie Uczestnik śledzenia ETW używa domyślnego identyfikatora dostawcy, gdy nie został określony, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="61b5f-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="61b5f-123">Na poniższej ilustracji przedstawiono przepływ danych śledzenia za pomocą uczestnika śledzenia funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="61b5f-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="61b5f-124">Po osiągnięciu przez dane śledzenia sesji ETW można uzyskać do niej dostęp na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="61b5f-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="61b5f-125">Jednym z najbardziej przydatnych sposobów uzyskiwania dostępu do tych zdarzeń jest Podgląd zdarzeń, typowe narzędzie systemu Windows służące do wyświetlania dzienników i śladów z aplikacji i usług.</span><span class="sxs-lookup"><span data-stu-id="61b5f-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 ![Przepływ danych śledzenia za pomocą dostawcy śledzenia ETW.](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="61b5f-127">Śledzenie danych zdarzeń uczestników</span><span class="sxs-lookup"><span data-stu-id="61b5f-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="61b5f-128">Uczestnik śledzenia serializować śledzone dane zdarzenia do sesji ETW w formacie jednego zdarzenia dla każdego rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="61b5f-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="61b5f-129">Zdarzenie jest identyfikowane przy użyciu identyfikatora z zakresu od 100 do 199.</span><span class="sxs-lookup"><span data-stu-id="61b5f-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="61b5f-130">Aby zapoznać się z definicjami rekordów zdarzeń śledzenia emitowanych przez uczestnika śledzenia, zobacz temat [Informacje o śledzeniu zdarzeń](tracking-events-reference.md) .</span><span class="sxs-lookup"><span data-stu-id="61b5f-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="61b5f-131">Rozmiar zdarzenia ETW jest ograniczony przez rozmiar buforu ETW lub przez maksymalny ładunek zdarzenia ETW, w zależności od tego, która wartość jest mniejsza.</span><span class="sxs-lookup"><span data-stu-id="61b5f-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="61b5f-132">Jeśli rozmiar zdarzenia przekracza jeden z tych limitów ETW, zdarzenie jest obcinane i jego zawartość została usunięta w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="61b5f-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="61b5f-133">Zmienne, argumenty, adnotacje i dane niestandardowe nie są selektywnie usuwane.</span><span class="sxs-lookup"><span data-stu-id="61b5f-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="61b5f-134">W przypadku obcinania wszystkie z nich są obcinane niezależnie od wartości, która spowodowała przekroczenie limitu ETW przez rozmiar zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="61b5f-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="61b5f-135">Usunięte dane zostaną zastąpione `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="61b5f-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="61b5f-136">Typy złożone w zmiennych, argumentach i niestandardowych elementach danych są serializowane do rekordu zdarzenia ETW przy użyciu [klasy NetDataContractSerializer](https://go.microsoft.com/fwlink/?LinkId=177537).</span><span class="sxs-lookup"><span data-stu-id="61b5f-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the [NetDataContractSerializer Class](https://go.microsoft.com/fwlink/?LinkId=177537).</span></span> <span data-ttu-id="61b5f-137">Ta klasa zawiera informacje o typie CLR w serializowanej parze XML.</span><span class="sxs-lookup"><span data-stu-id="61b5f-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="61b5f-138">Obcinanie danych ładunku ze względu na limity ETW może spowodować, że rekordy śledzenia zduplikowane są wysyłane do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="61b5f-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="61b5f-139">Taka sytuacja może wystąpić, jeśli więcej niż jedna sesja nasłuchuje zdarzeń, a sesje mają różne limity ładunku dla zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="61b5f-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="61b5f-140">Dla sesji o niższym limicie zdarzenie może zostać obcięte.</span><span class="sxs-lookup"><span data-stu-id="61b5f-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="61b5f-141">Uczestnik śledzenia ETW nie ma żadnej informacji o liczbie sesji nasłuchujących zdarzeń; Jeśli zdarzenie zostanie obcięte dla sesji, uczestnik ETW ponawia próbę wysłania zdarzenia raz.</span><span class="sxs-lookup"><span data-stu-id="61b5f-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="61b5f-142">W takim przypadku sesja, która jest skonfigurowana do akceptowania większego rozmiaru ładunku, spowoduje dwa razy zdarzenie (zdarzenie obcięte i obcięte).</span><span class="sxs-lookup"><span data-stu-id="61b5f-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="61b5f-143">Duplikowanie może być uniemożliwione przez skonfigurowanie wszystkich sesji ETW o tym samym limicie rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="61b5f-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="61b5f-144">Uzyskiwanie dostępu do śledzenia danych z uczestnika ETW w Podgląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="61b5f-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="61b5f-145">Do zdarzeń, które są zapisywane w sesji ETW przez uczestnika śledzenia ETW, można uzyskać dostęp za pośrednictwem Podgląd zdarzeń (przy użyciu domyślnego identyfikatora dostawcy).</span><span class="sxs-lookup"><span data-stu-id="61b5f-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="61b5f-146">Pozwala to na szybkie wyświetlanie rekordów śledzenia, które zostały wyemitowane przez przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="61b5f-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61b5f-147">Śledzone zdarzenia rejestrowania wyemitowane do sesji ETW używają identyfikatorów zdarzeń z zakresu od 100 do 199.</span><span class="sxs-lookup"><span data-stu-id="61b5f-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="61b5f-148">Aby włączyć wyświetlanie rekordów śledzenia w Podgląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="61b5f-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1. <span data-ttu-id="61b5f-149">Uruchom Podgląd zdarzeń (EVENTVWR. EXE</span><span class="sxs-lookup"><span data-stu-id="61b5f-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2. <span data-ttu-id="61b5f-150">Wybierz **Podgląd zdarzeń, Dzienniki aplikacji i usług, Microsoft, Windows, serwer aplikacji-aplikacje**.</span><span class="sxs-lookup"><span data-stu-id="61b5f-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3. <span data-ttu-id="61b5f-151">Kliknij prawym przyciskiem myszy i sprawdź, czy wybrano opcję **Widok, Pokaż dzienniki analityczne i debugowania** .</span><span class="sxs-lookup"><span data-stu-id="61b5f-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="61b5f-152">Jeśli nie, zaznacz ją, aby znacznik wyboru pojawił się obok niego.</span><span class="sxs-lookup"><span data-stu-id="61b5f-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="61b5f-153">Spowoduje to wyświetlenie dzienników **analitycznych**, **wydajności**i **debugowania** .</span><span class="sxs-lookup"><span data-stu-id="61b5f-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4. <span data-ttu-id="61b5f-154">Kliknij prawym przyciskiem myszy dziennik analityczny, a następnie wybierz pozycję **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="61b5f-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="61b5f-155">Dziennik będzie istnieć w pliku%SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications% 4 A nalytic. etl.</span><span class="sxs-lookup"><span data-stu-id="61b5f-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="61b5f-156">Uczestnik śledzenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="61b5f-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="61b5f-157">Interfejs API uczestnika śledzenia umożliwia rozszerzenie środowiska uruchomieniowego śledzenia z uczestnikiem śledzenia dostarczonym przez użytkownika, który może zawierać logikę niestandardową do obsługi rekordów śledzenia emitowanych przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="61b5f-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="61b5f-158">Aby napisać niestandardowego uczestnika śledzenia, Deweloper musi zaimplementować `Track` metodę <xref:System.Activities.Tracking.TrackingParticipant> w klasie.</span><span class="sxs-lookup"><span data-stu-id="61b5f-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="61b5f-159">Ta metoda jest wywoływana, gdy rekord śledzenia jest emitowany przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="61b5f-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="61b5f-160">Śledzenie uczestników pochodzi od <xref:System.Activities.Tracking.TrackingParticipant> klasy.</span><span class="sxs-lookup"><span data-stu-id="61b5f-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="61b5f-161">Dostarczone <xref:System.Activities.Tracking.EtwTrackingParticipant> przez system, emituje zdarzenie śledzenia zdarzeń dla systemu Windows (ETW) dla każdego odebranego rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="61b5f-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="61b5f-162">Aby utworzyć niestandardowego uczestnika śledzenia, tworzona jest Klasa, która pochodzi od <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="61b5f-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="61b5f-163">Aby zapewnić podstawowe funkcje śledzenia, Przesłoń <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="61b5f-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="61b5f-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A>jest wywoływana, gdy rekord śledzenia jest wysyłany przez środowisko uruchomieniowe i może być przetwarzany w odpowiedni sposób.</span><span class="sxs-lookup"><span data-stu-id="61b5f-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="61b5f-165">W poniższym przykładzie zdefiniowano klasę niestandardowego uczestnika śledzenia, która emituje wszystkie rekordy śledzenia do okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="61b5f-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="61b5f-166">Można również zaimplementować <xref:System.Activities.Tracking.TrackingParticipant> obiekt, który przetwarza rekordy śledzenia asynchronicznie `BeginTrack` przy użyciu metod i `EndTrack`</span><span class="sxs-lookup"><span data-stu-id="61b5f-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
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
  
 <span data-ttu-id="61b5f-167">Aby użyć określonego uczestnika śledzenia, zarejestruj go przy użyciu wystąpienia przepływu pracy, które chcesz śledzić, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="61b5f-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="61b5f-168">W poniższym przykładzie zostanie utworzony przepływ pracy, który obejmuje <xref:System.Activities.Statements.Sequence> działanie <xref:System.Activities.Statements.WriteLine> zawierające działanie.</span><span class="sxs-lookup"><span data-stu-id="61b5f-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="61b5f-169">`ConsoleTrackingParticipant` Zostanie dodany do rozszerzeń, a przepływ pracy jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="61b5f-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="61b5f-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61b5f-170">See also</span></span>

- [<span data-ttu-id="61b5f-171">Monitorowanie aplikacji sieci szkieletowej systemu Windows Server</span><span class="sxs-lookup"><span data-stu-id="61b5f-171">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="61b5f-172">Monitorowanie aplikacji przy użyciu sieci szkieletowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="61b5f-172">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
