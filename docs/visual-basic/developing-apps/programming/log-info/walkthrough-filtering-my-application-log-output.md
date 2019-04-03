---
title: Filtrowanie danych wyjściowych My.Application.Log (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f38217a5385b9d736eaa744a73024f210eb8f553
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829392"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="8f598-102">Przewodnik: Filtrowanie danych wyjściowych My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f598-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>
<span data-ttu-id="8f598-103">W tym instruktażu pokazano, jak zmienić domyślny dziennik filtrowanie `My.Application.Log` obiektu, aby kontrolować, jakie informacje są przekazywane z `Log` obiekt do odbiorników i jakie informacje są zapisywane przez odbiorniki.</span><span class="sxs-lookup"><span data-stu-id="8f598-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="8f598-104">Możesz zmienić sposób rejestrowania, nawet po zakończeniu tworzenia aplikacji, ponieważ informacje o konfiguracji są przechowywane w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f598-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="8f598-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8f598-105">Getting Started</span></span>  
 <span data-ttu-id="8f598-106">Każdy komunikat, który `My.Application.Log` zapisów ma poziom ważności skojarzone, który mechanizmy filtrowania użyć, aby kontrolować dane wyjściowe dziennika.</span><span class="sxs-lookup"><span data-stu-id="8f598-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="8f598-107">Ta przykładowa aplikacja używa `My.Application.Log` metod można zapisać kilka rejestrowania komunikatów za pomocą różne poziomy ważności.</span><span class="sxs-lookup"><span data-stu-id="8f598-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>  
  
#### <a name="to-build-the-sample-application"></a><span data-ttu-id="8f598-108">Do tworzenia przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="8f598-108">To build the sample application</span></span>  
  
1.  <span data-ttu-id="8f598-109">Otwórz nowy projekt aplikacji Windows Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8f598-109">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="8f598-110">Dodaj przycisk o nazwie Button1 do formularza Form1.</span><span class="sxs-lookup"><span data-stu-id="8f598-110">Add a button named Button1 to Form1.</span></span>  
  
3.  <span data-ttu-id="8f598-111">W <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla Button1, Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="8f598-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]  
  
4.  <span data-ttu-id="8f598-112">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="8f598-112">Run the application in the debugger.</span></span>  
  
5.  <span data-ttu-id="8f598-113">Naciśnij klawisz **Button1**.</span><span class="sxs-lookup"><span data-stu-id="8f598-113">Press **Button1**.</span></span>  
  
     <span data-ttu-id="8f598-114">Aplikacja zapisuje następujące informacje do pliku danych wyjściowych i dzienników debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f598-114">The application writes the following information to the application's debug output and log file.</span></span>  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  <span data-ttu-id="8f598-115">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="8f598-115">Close the application.</span></span>  
  
     <span data-ttu-id="8f598-116">Aby uzyskać informacje o sposobie wyświetlania okna danych wyjściowych debugowania aplikacji, zobacz [okno danych wyjściowych](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="8f598-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="8f598-117">Aby uzyskać informacje o lokalizacji pliku dziennika aplikacji, zobacz [instruktażu: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="8f598-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f598-118">Domyślnie aplikacja czyści dane wyjściowe pliku dziennika, po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f598-118">By default, the application flushes the log-file output when the application closes.</span></span>  
  
     <span data-ttu-id="8f598-119">W przykładzie powyżej, drugie wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> metody i wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> generuje dane wyjściowe dziennika podczas wywołania imię i nazwisko `WriteEntry` metody nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="8f598-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="8f598-120">Jest to spowodowane poziomy ważności `WriteEntry` i `WriteException` "Informacje" i "Error", które są dozwolone przez `My.Application.Log` obiektu domyślne filtrowanie dziennika.</span><span class="sxs-lookup"><span data-stu-id="8f598-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="8f598-121">Jednak zdarzeń za pomocą "Start" i "Zatrzymaj" poziomy ważności nie generuje danych wyjściowych dzienników.</span><span class="sxs-lookup"><span data-stu-id="8f598-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="8f598-122">Filtrowanie wszystkich odbiorników My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="8f598-122">Filtering for All My.Application.Log Listeners</span></span>  
 <span data-ttu-id="8f598-123">`My.Application.Log` Obiektu używa <xref:System.Diagnostics.SourceSwitch> o nazwie `DefaultSwitch` kontrolowanie komunikaty go — dostęp próbny od `WriteEntry` i `WriteException` metody odbiorniki logu.</span><span class="sxs-lookup"><span data-stu-id="8f598-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="8f598-124">Można skonfigurować `DefaultSwitch` w pliku konfiguracyjnym aplikacji, ustawiając jej wartość na jedną z <xref:System.Diagnostics.SourceLevels> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8f598-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="8f598-125">Domyślna wartość to "Informacje".</span><span class="sxs-lookup"><span data-stu-id="8f598-125">By default, its value is "Information".</span></span>  
  
 <span data-ttu-id="8f598-126">W poniższej tabeli przedstawiono poziom ważności, wymaganych do dziennika zapisać komunikat do odbiorników, biorąc pod uwagę określonego `DefaultSwitch` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="8f598-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>  
  
|<span data-ttu-id="8f598-127">Wartość DefaultSwitch</span><span class="sxs-lookup"><span data-stu-id="8f598-127">DefaultSwitch Value</span></span>|<span data-ttu-id="8f598-128">Ważność wiadomości wymagane dla danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="8f598-128">Message severity required for output</span></span>|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|<span data-ttu-id="8f598-129">`Critical` lub `Error`</span><span class="sxs-lookup"><span data-stu-id="8f598-129">`Critical` or `Error`</span></span>|  
|`Warning`|<span data-ttu-id="8f598-130">`Critical`, `Error`, lub `Warning`</span><span class="sxs-lookup"><span data-stu-id="8f598-130">`Critical`, `Error`, or `Warning`</span></span>|  
|`Information`|<span data-ttu-id="8f598-131">`Critical`, `Error`, `Warning`, lub `Information`</span><span class="sxs-lookup"><span data-stu-id="8f598-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|  
|`Verbose`|<span data-ttu-id="8f598-132">`Critical`, `Error`, `Warning`, `Information`, lub `Verbose`</span><span class="sxs-lookup"><span data-stu-id="8f598-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|  
|`ActivityTracing`|<span data-ttu-id="8f598-133">`Start`, `Stop`, `Suspend`, `Resume`, lub `Transfer`</span><span class="sxs-lookup"><span data-stu-id="8f598-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|  
|`All`|<span data-ttu-id="8f598-134">Wszystkie komunikaty są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="8f598-134">All messages are allowed.</span></span>|  
|`Off`|<span data-ttu-id="8f598-135">Wszystkie komunikaty są blokowane.</span><span class="sxs-lookup"><span data-stu-id="8f598-135">All messages are blocked.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8f598-136">`WriteEntry` i `WriteException` metody mają przeciążenia, które nie określa poziom ważności.</span><span class="sxs-lookup"><span data-stu-id="8f598-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="8f598-137">Poziom ważności niejawne `WriteEntry` przeciążenie jest "Informacje", a poziom ważności niejawne `WriteException` przeciążenie to "Error".</span><span class="sxs-lookup"><span data-stu-id="8f598-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>  
  
 <span data-ttu-id="8f598-138">W następującej tabeli opisano w poprzednim przykładzie dane wyjściowe dziennika: przy użyciu domyślnego `DefaultSwitch` ustawienie "Informacje", tylko drugie wywołanie `WriteEntry` metody i wywołanie `WriteException` dane wyjściowe dziennika produktu metody.</span><span class="sxs-lookup"><span data-stu-id="8f598-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="8f598-139">Aby rejestrować zdarzenia śledzenia tylko działania</span><span class="sxs-lookup"><span data-stu-id="8f598-139">To log only activity tracing events</span></span>  
  
1.  <span data-ttu-id="8f598-140">Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="8f598-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>  
  
     <span data-ttu-id="8f598-141">—lub—</span><span class="sxs-lookup"><span data-stu-id="8f598-141">-or-</span></span>  
  
     <span data-ttu-id="8f598-142">Jeśli nie ma żadnego pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="8f598-142">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="8f598-143">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="8f598-143">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="8f598-144">Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="8f598-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="8f598-145">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8f598-145">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="8f598-146">Znajdź `<switches>` sekcji, która znajduje się w `<system.diagnostics>` sekcji, która znajduje się w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="8f598-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="8f598-147">Znajdź element, który dodaje `DefaultSwitch` w kolekcji parametrów.</span><span class="sxs-lookup"><span data-stu-id="8f598-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="8f598-148">Powinny one wyglądać podobnie do tego elementu:</span><span class="sxs-lookup"><span data-stu-id="8f598-148">It should look similar to this element:</span></span>  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  <span data-ttu-id="8f598-149">Zmień wartość właściwości `value` atrybutu "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="8f598-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>  
  
5.  <span data-ttu-id="8f598-150">Zawartość pliku app.config powinien wyglądać podobnie jak następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="8f598-150">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="ActivityTracing" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
6.  <span data-ttu-id="8f598-151">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="8f598-151">Run the application in the debugger.</span></span>  
  
7.  <span data-ttu-id="8f598-152">Naciśnij klawisz **Button1**.</span><span class="sxs-lookup"><span data-stu-id="8f598-152">Press **Button1**.</span></span>  
  
     <span data-ttu-id="8f598-153">Aplikacja zapisuje następujące informacje do pliku danych wyjściowych i dzienników debugowania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8f598-153">The application writes the following information to the application's debug output and log file:</span></span>  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  <span data-ttu-id="8f598-154">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="8f598-154">Close the application.</span></span>  
  
9. <span data-ttu-id="8f598-155">Zmień wartość właściwości `value` atrybutu "Informacje".</span><span class="sxs-lookup"><span data-stu-id="8f598-155">Change the value of the `value` attribute back to "Information".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f598-156">`DefaultSwitch` Przełącz ustawienie określa `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="8f598-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="8f598-157">Nie zmienia sposób, w jaki [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> i <xref:System.Diagnostics.Debug?displayProperty=nameWithType> zachowują się klasy.</span><span class="sxs-lookup"><span data-stu-id="8f598-157">It does not change how the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="8f598-158">Osoba filtrowanie odbiorników My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="8f598-158">Individual Filtering For My.Application.Log Listeners</span></span>  
 <span data-ttu-id="8f598-159">Poprzedni przykład pokazuje, jak zmienić ustawienia filtrowania dla wszystkich `My.Application.Log` danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8f598-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="8f598-160">W tym przykładzie pokazano, jak filtrować odbiornik osobny dziennik.</span><span class="sxs-lookup"><span data-stu-id="8f598-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="8f598-161">Domyślnie aplikacja ma dwa odbiorniki ten zapis w danych wyjściowych debugowania aplikacji i plik dziennika.</span><span class="sxs-lookup"><span data-stu-id="8f598-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>  
  
 <span data-ttu-id="8f598-162">Plik konfiguracyjny steruje zachowaniem odbiorniki logu, umożliwiając każdej z nich ma filtr, który jest podobny do przełącznika dla `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="8f598-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="8f598-163">Odbiornik dziennika wiadomość wyjściową, tylko wtedy, gdy ważność komunikatu jest dozwolony w obu dziennika `DefaultSwitch` i Filtruj odbiornika dziennika.</span><span class="sxs-lookup"><span data-stu-id="8f598-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>  
  
 <span data-ttu-id="8f598-164">W tym przykładzie pokazano, jak skonfigurować filtrowanie, aby uzyskać nowy odbiornik debugowania i dodać go do `Log` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f598-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="8f598-165">Odbiornik debugowania domyślne powinny zostać usunięte z `Log` obiektu, dzięki czemu jest jasne, że komunikaty debugowania pochodzą z nowy odbiornik debugowania.</span><span class="sxs-lookup"><span data-stu-id="8f598-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="8f598-166">Aby rejestrować tylko zdarzenia śledzenie aktywności</span><span class="sxs-lookup"><span data-stu-id="8f598-166">To log only activity-tracing events</span></span>  
  
1.  <span data-ttu-id="8f598-167">Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="8f598-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="8f598-168">—lub—</span><span class="sxs-lookup"><span data-stu-id="8f598-168">-or-</span></span>  
  
     <span data-ttu-id="8f598-169">Jeśli nie ma żadnego pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="8f598-169">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="8f598-170">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="8f598-170">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="8f598-171">Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="8f598-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="8f598-172">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8f598-172">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="8f598-173">Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="8f598-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="8f598-174">Wybierz **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="8f598-174">Choose **Open**.</span></span>  
  
3.  <span data-ttu-id="8f598-175">Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource", która jest w trakcie `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="8f598-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="8f598-176">`<sources>` Znajduje się w sekcji `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="8f598-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
4.  <span data-ttu-id="8f598-177">Dodaj ten element, aby `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="8f598-177">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  <span data-ttu-id="8f598-178">Znajdź `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="8f598-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="8f598-179">Dodaj ten element, do którego `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="8f598-179">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="NewDefault"   
         type="System.Diagnostics.DefaultTraceListener,   
               System, Version=2.0.0.0, Culture=neutral,   
               PublicKeyToken=b77a5c561934e089,   
               processorArchitecture=MSIL">  
        <filter type="System.Diagnostics.EventTypeFilter"   
                initializeData="Error" />  
    </add>  
    ```  
  
     <span data-ttu-id="8f598-180"><xref:System.Diagnostics.EventTypeFilter> Filtr ma jedną z <xref:System.Diagnostics.SourceLevels> wyliczenia wartości zgodnie z jego `initializeData` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8f598-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>  
  
7.  <span data-ttu-id="8f598-181">Zawartość pliku app.config powinien wyglądać podobnie jak następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="8f598-181">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Remove the default debug listener. -->  
              <remove name="Default"/>  
              <!-- Add a filterable debug listener. -->  
              <add name="NewDefault"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
          <add name="NewDefault"   
               type="System.Diagnostics.DefaultTraceListener,   
                     System, Version=2.0.0.0, Culture=neutral,   
                     PublicKeyToken=b77a5c561934e089,   
                     processorArchitecture=MSIL">  
            <filter type="System.Diagnostics.EventTypeFilter"   
                    initializeData="Error" />  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
8.  <span data-ttu-id="8f598-182">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="8f598-182">Run the application in the debugger.</span></span>  
  
9. <span data-ttu-id="8f598-183">Naciśnij klawisz **Button1**.</span><span class="sxs-lookup"><span data-stu-id="8f598-183">Press **Button1**.</span></span>  
  
     <span data-ttu-id="8f598-184">Aplikacja zapisuje następujące informacje w pliku dziennika aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8f598-184">The application writes the following information to the application's log file:</span></span>  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     <span data-ttu-id="8f598-185">Aplikacja zapisuje mniej informacji debugowania aplikacji w danych wyjściowych ze względu na bardziej restrykcyjne filtrowania.</span><span class="sxs-lookup"><span data-stu-id="8f598-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>  
  
     `Default Error   2   Error`  
  
10. <span data-ttu-id="8f598-186">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="8f598-186">Close the application.</span></span>  
  
 <span data-ttu-id="8f598-187">Aby uzyskać więcej informacji na temat zmiany ustawień dziennika po wdrożeniu, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="8f598-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f598-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f598-188">See also</span></span>

- [<span data-ttu-id="8f598-189">Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="8f598-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="8f598-190">Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="8f598-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="8f598-191">Przewodnik: Tworzenie odbiorników logu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="8f598-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="8f598-192">Instrukcje: Zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="8f598-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="8f598-193">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="8f598-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="8f598-194">Rejestrowanie informacji z aplikacji</span><span class="sxs-lookup"><span data-stu-id="8f598-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
