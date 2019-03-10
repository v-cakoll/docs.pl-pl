---
title: Uczestnicy śledzenia
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 934c49aaa48ecb319d55fa997aaac4eec93b54c3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711970"
---
# <a name="tracking-participants"></a><span data-ttu-id="0498b-102">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="0498b-102">Tracking Participants</span></span>
<span data-ttu-id="0498b-103">Śledzenie uczestników są punkty rozszerzeń, zezwalających na dewelopera przepływu pracy, aby uzyskać dostęp do <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> obiektów i ich przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="0498b-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="0498b-104">zawiera standardowe śledzenia uczestnika, który zapisuje rekordy śledzenia jako zdarzenia śledzenie zdarzeń dla Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="0498b-104">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="0498b-105">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0498b-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="0498b-106">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="0498b-106">Tracking Participants</span></span>  
 <span data-ttu-id="0498b-107">Infrastruktura śledzenia umożliwia stosowanie filtru na wychodzące rekordów śledzenia tak, aby uczestnika, który może być subskrybowana przez podzestaw rekordów.</span><span class="sxs-lookup"><span data-stu-id="0498b-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="0498b-108">Mechanizm, aby zastosować filtr jest za pośrednictwem profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0498b-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="0498b-109">Windows Workflow Foundation (WF) w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] zapewnia śledzenia uczestnika, który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="0498b-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="0498b-110">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0498b-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="0498b-111">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0498b-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="0498b-112">Przykładowy zestaw SDK dla opartych na funkcji ETW śledzenia jest dobrym sposobem na zapoznanie się z WF śledzenia przy użyciu opartych na funkcji ETW śledzenia uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0498b-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="0498b-113">Uczestnika śledzenia zdarzeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0498b-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="0498b-114">obejmuje ETW śledzenia uczestnika, który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="0498b-114">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="0498b-115">Odbywa się to w bardzo wydajny sposób z minimalnym wpływem na wydajność aplikacji lub przepływność serwera.</span><span class="sxs-lookup"><span data-stu-id="0498b-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="0498b-116">Zaletą standardowe uczestnika śledzenia zdarzeń systemu Windows jest, czy rekordy śledzenia, który odbiera mogą być wyświetlane z innych aplikacji i systemem dzienniki w Podglądzie zdarzeń Windows.</span><span class="sxs-lookup"><span data-stu-id="0498b-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="0498b-117">Standardowe uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0498b-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="0498b-118">Jeśli `trackingProfile` nie określono nazwy, takie jak właśnie `<etwTracking/>` lub `<etwTracking profileName=""/>`, a następnie domyślną śledzenia profil jest zainstalowany za pomocą [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w pliku Machine.config plik jest używany.</span><span class="sxs-lookup"><span data-stu-id="0498b-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="0498b-119">W pliku Machine.config domyślny profil śledzenia subskrybuje rekordów wystąpienia przepływu pracy i usterek.</span><span class="sxs-lookup"><span data-stu-id="0498b-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="0498b-120">W funkcji ETW zdarzenia są zapisywane w sesji ETW za pomocą identyfikatora dostawcy.</span><span class="sxs-lookup"><span data-stu-id="0498b-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="0498b-121">Dostawca identyfikator, który ETW śledzenia uczestnika używa do tworzenia śledzenia rekordów zdarzeń systemu Windows jest zdefiniowany w sekcji Diagnostyka pliku Web.config (w obszarze `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="0498b-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="0498b-122">Domyślnie uczestnika śledzenia zdarzeń systemu Windows używa domyślny identyfikator dostawcy podczas nie zostało określone, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0498b-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="0498b-123">Poniższa ilustracja przedstawia przepływ danych za pomocą funkcji ETW śledzenia uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0498b-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="0498b-124">Gdy dane śledzenia osiągnie sesja funkcji ETW, możliwy jest wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="0498b-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="0498b-125">Jest jednym z najbardziej przydatnych sposobów uzyskać dostęp do tych zdarzeń za pomocą Podglądu zdarzeń, popularnego narzędzia Windows używane do wyświetlania dzienników i ślady z aplikacji i usług.</span><span class="sxs-lookup"><span data-stu-id="0498b-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 <span data-ttu-id="0498b-126">![Przepływ śledzenia i dostawcy śledzenia funkcji ETW](./media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span><span class="sxs-lookup"><span data-stu-id="0498b-126">![The flow of Tracking and ETW Tracking Provider](./media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span></span>  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="0498b-127">Dane zdarzeń uczestników śledzenia</span><span class="sxs-lookup"><span data-stu-id="0498b-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="0498b-128">Śledzenia uczestnika, który serializuje dane zdarzeń rejestrowanych w formacie jedno zdarzenie na rekord śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="0498b-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="0498b-129">Zdarzenie jest identyfikowane za pomocą Identyfikatora w zakresie od 100 do 199.</span><span class="sxs-lookup"><span data-stu-id="0498b-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="0498b-130">Dla definicji zdarzeń śledzenia rekordów emitowane przez uczestnika śledzenia, zobacz [śledzenia informacje o zdarzeniach](tracking-events-reference.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="0498b-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="0498b-131">Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW, lub przez maksymalne ładunek zdarzenia ETW, niezależnie od wartości jest mniejsza.</span><span class="sxs-lookup"><span data-stu-id="0498b-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="0498b-132">Jeśli rozmiar zdarzenia przekracza jedną z tych limitów ETW, zostanie obcięta zdarzenia i jego zawartość usunięta w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="0498b-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="0498b-133">Zmienne, argumenty, adnotacji i danych niestandardowych nie są selektywnie usunąć.</span><span class="sxs-lookup"><span data-stu-id="0498b-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="0498b-134">W przypadku obcinania wszystkie te są obcinane niezależnie od wartości, który spowodował rozmiar zdarzenia przekracza ETW limit.</span><span class="sxs-lookup"><span data-stu-id="0498b-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="0498b-135">Usunięto dane są zastępowane `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="0498b-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="0498b-136">Złożone typy w zmiennych argumentów, a elementy niestandardowe dane są szeregowane do ETW zdarzenia rekordu przy użyciu [klasy NetDataContractSerializer](https://go.microsoft.com/fwlink/?LinkId=177537).</span><span class="sxs-lookup"><span data-stu-id="0498b-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the [NetDataContractSerializer Class](https://go.microsoft.com/fwlink/?LinkId=177537).</span></span> <span data-ttu-id="0498b-137">Ta klasa zawiera informacje o typie CLR w Zserializowany strumień XML.</span><span class="sxs-lookup"><span data-stu-id="0498b-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="0498b-138">Obcięcie danych ładunku z powodu ograniczeń ETW może spowodować zduplikowane śledzenia rekordów, które są wysyłane do sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="0498b-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="0498b-139">Może to wystąpić, jeśli więcej niż jedna sesja nasłuchuje zdarzeń i sesje mają różne ładunku limity dla zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0498b-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="0498b-140">W sesji z dolną granicę zdarzenia mogą być obcinane.</span><span class="sxs-lookup"><span data-stu-id="0498b-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="0498b-141">Uczestnika śledzenia zdarzeń systemu Windows nie ma żadnej wiedzy liczbę sesji nasłuchiwanie zdarzeń; Jeśli zdarzenie jest tutaj obcięto je dla sesji, a następnie ETW uczestnika ponawia próbę wysłania zdarzenia jeden raz.</span><span class="sxs-lookup"><span data-stu-id="0498b-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="0498b-142">W tym przypadku sesji który jest skonfigurowany do akceptowania większy rozmiar ładunku otrzyma dwukrotnie zdarzeń (zdarzenie-obcięty i obcięte).</span><span class="sxs-lookup"><span data-stu-id="0498b-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="0498b-143">Duplikowanie można zapobiec, konfigurując wszystkie sesje ETW za pomocą tych samych ograniczeń rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="0498b-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="0498b-144">Uzyskiwanie dostępu do danych śledzenia z uczestnika zdarzeń systemu Windows w Podglądzie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="0498b-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="0498b-145">Zdarzenia, które są zapisywane w sesji funkcji ETW przez uczestnika śledzenia zdarzeń systemu Windows są dostępne za pomocą Podglądu zdarzeń (w przypadku używania domyślny identyfikator dostawcy).</span><span class="sxs-lookup"><span data-stu-id="0498b-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="0498b-146">Pozwala to na szybkie przeglądanie śledzenia rekordów, które zostały wyemitowane przez przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="0498b-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0498b-147">Śledzenie zdarzeń rekordów emitowany do ETW sesji Użyj identyfikatorów zdarzeń z zakresu od 100 do 199.</span><span class="sxs-lookup"><span data-stu-id="0498b-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="0498b-148">Aby umożliwić wyświetlanie rekordów śledzenia w Podglądzie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="0498b-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1.  <span data-ttu-id="0498b-149">Uruchomienie podglądu zdarzeń (EVENTVWR. Z ROZSZERZENIEM EXE)</span><span class="sxs-lookup"><span data-stu-id="0498b-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2.  <span data-ttu-id="0498b-150">Wybierz **Podgląd zdarzeń, dzienniki aplikacji i usług, aplikacji serwera firmy Microsoft, Windows, aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="0498b-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3.  <span data-ttu-id="0498b-151">Kliknij prawym przyciskiem myszy i upewnij się, że **widoku, Pokaż dzienniki analityczne i debugowania** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="0498b-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="0498b-152">Jeśli nie, wybierz ją, dzięki czemu pojawi się znacznik wyboru obok niego.</span><span class="sxs-lookup"><span data-stu-id="0498b-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="0498b-153">Spowoduje to wyświetlenie **analityczne**, **wydajności**, i **debugowania** dzienniki.</span><span class="sxs-lookup"><span data-stu-id="0498b-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4.  <span data-ttu-id="0498b-154">Kliknij prawym przyciskiem myszy **analityczne** logowania, a następnie wybierz pozycję **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="0498b-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="0498b-155">Dziennik będzie istnieć w pliku Server-Applications%4Analytic.etl %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application.</span><span class="sxs-lookup"><span data-stu-id="0498b-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="0498b-156">Niestandardowego uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="0498b-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="0498b-157">Uczestnika śledzenia interfejsu API umożliwia rozszerzenie środowiska uruchomieniowego śledzenia przy użyciu podanego przez użytkownika śledzenia uczestnika, który może zawierać niestandardowej logiki do obsługi rekordów śledzenia emitowane przez środowisko wykonawcze przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="0498b-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="0498b-158">Aby napisać uczestnikiem niestandardowe śledzenia, deweloper musi implementować `Track` metody <xref:System.Activities.Tracking.TrackingParticipant> klasy.</span><span class="sxs-lookup"><span data-stu-id="0498b-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="0498b-159">Ta metoda jest wywoływana, gdy rekord śledzenia jest emitowane przez środowisko wykonawcze przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="0498b-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="0498b-160">Uczestnicy śledzenia pochodzić od <xref:System.Activities.Tracking.TrackingParticipant> klasy.</span><span class="sxs-lookup"><span data-stu-id="0498b-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="0498b-161">Dostarczane przez system <xref:System.Activities.Tracking.EtwTrackingParticipant> emituje zdarzenia zdarzeń śledzenia dla Windows (ETW) dla każdego rekordu śledzenia, która została odebrana.</span><span class="sxs-lookup"><span data-stu-id="0498b-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="0498b-162">Aby utworzyć niestandardowego uczestnika śledzenia, klasa jest tworzona, jest pochodną <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="0498b-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="0498b-163">Aby zapewnić funkcjonalność śledzenia podstawowego, należy zastąpić <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="0498b-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="0498b-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> jest wywoływana, gdy rekord śledzenia są wysyłane przez środowisko uruchomieniowe i mogą być przetwarzane w żądany sposób.</span><span class="sxs-lookup"><span data-stu-id="0498b-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="0498b-165">W poniższym przykładzie zdefiniowano klasę uczestnika śledzenia niestandardowego, który emituje wszystkich rekordów śledzenia w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="0498b-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="0498b-166">Możesz również wdrożyć <xref:System.Activities.Tracking.TrackingParticipant> obiektu, który przetwarza dane śledzenia rekordów, asynchronicznie przy użyciu jego `BeginTrack` i `EndTrack` metody</span><span class="sxs-lookup"><span data-stu-id="0498b-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
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
  
 <span data-ttu-id="0498b-167">Aby użyć konkretnego śledzenia uczestnika, należy go zarejestrować z wystąpieniem przepływu pracy, który chcesz śledzić, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0498b-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="0498b-168">W poniższym przykładzie przepływ pracy składający się z <xref:System.Activities.Statements.Sequence> działania, który zawiera <xref:System.Activities.Statements.WriteLine> utworzeniu działania.</span><span class="sxs-lookup"><span data-stu-id="0498b-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="0498b-169">`ConsoleTrackingParticipant` Jest dodawany do rozszerzeń i przepływ pracy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="0498b-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0498b-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0498b-170">See also</span></span>
- [<span data-ttu-id="0498b-171">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="0498b-171">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="0498b-172">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="0498b-172">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
