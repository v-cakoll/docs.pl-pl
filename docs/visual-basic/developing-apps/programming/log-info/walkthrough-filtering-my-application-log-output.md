---
title: Filtrowanie danych wyjściowych my. Application. log (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: af1dc3e1ce22112d76ad566873f40c1c2ac05c9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968687"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="d3596-102">Przewodnik: Filtrowanie danych wyjściowych my. Application. log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3596-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>
<span data-ttu-id="d3596-103">W tym instruktażu pokazano, jak zmienić domyślne filtrowanie dzienników dla `My.Application.Log` obiektu, aby kontrolować, jakie informacje są przesyłane `Log` z obiektu do odbiorników i jakie informacje są zapisywane przez odbiorniki.</span><span class="sxs-lookup"><span data-stu-id="d3596-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="d3596-104">Zachowanie rejestrowania można zmienić nawet po skompilowaniu aplikacji, ponieważ informacje o konfiguracji są przechowywane w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d3596-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="d3596-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="d3596-105">Getting Started</span></span>  
 <span data-ttu-id="d3596-106">Każdy komunikat, `My.Application.Log` który zapisuje, ma skojarzony poziom ważności, którego mechanizmy filtrowania używają do kontrolowania danych wyjściowych dziennika.</span><span class="sxs-lookup"><span data-stu-id="d3596-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="d3596-107">Ta przykładowa aplikacja `My.Application.Log` używa metod do pisania kilku komunikatów dziennika z różnymi poziomami ważności.</span><span class="sxs-lookup"><span data-stu-id="d3596-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>  
  
#### <a name="to-build-the-sample-application"></a><span data-ttu-id="d3596-108">Aby skompilować aplikację przykładową</span><span class="sxs-lookup"><span data-stu-id="d3596-108">To build the sample application</span></span>  
  
1. <span data-ttu-id="d3596-109">Otwórz nowy projekt aplikacji Visual Basic systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d3596-109">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="d3596-110">Dodaj przycisk o nazwie Button1 do formularza Form1.</span><span class="sxs-lookup"><span data-stu-id="d3596-110">Add a button named Button1 to Form1.</span></span>  
  
3. <span data-ttu-id="d3596-111">W programie obsługi zdarzeń dla Button1 Dodaj następujący kod: <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="d3596-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]  
  
4. <span data-ttu-id="d3596-112">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="d3596-112">Run the application in the debugger.</span></span>  
  
5. <span data-ttu-id="d3596-113">Naciśnij pozycję **Button1**.</span><span class="sxs-lookup"><span data-stu-id="d3596-113">Press **Button1**.</span></span>  
  
     <span data-ttu-id="d3596-114">Aplikacja zapisuje następujące informacje w danych wyjściowych debugowania i pliku dziennika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d3596-114">The application writes the following information to the application's debug output and log file.</span></span>  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6. <span data-ttu-id="d3596-115">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="d3596-115">Close the application.</span></span>  
  
     <span data-ttu-id="d3596-116">Aby uzyskać informacje na temat sposobu wyświetlania okna danych wyjściowych debugowania aplikacji, zobacz [okno dane wyjściowe](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="d3596-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="d3596-117">Aby uzyskać informacje na temat lokalizacji pliku dziennika aplikacji, zobacz [Przewodnik: Ustalanie, gdzie my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)zapisuje informacje.</span><span class="sxs-lookup"><span data-stu-id="d3596-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d3596-118">Domyślnie aplikacja opróżnia plik dziennika danych wyjściowych po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d3596-118">By default, the application flushes the log-file output when the application closes.</span></span>  
  
     <span data-ttu-id="d3596-119">W powyższym przykładzie drugie wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> metody i wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> metody generuje dane wyjściowe dziennika, podczas gdy pierwsze `WriteEntry` i ostatnie wywołania metody nie.</span><span class="sxs-lookup"><span data-stu-id="d3596-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="d3596-120">Wynika to z faktu, że `WriteEntry` poziomy `WriteException` ważności i są "informacje" i "błąd", `My.Application.Log` które są dozwolone przez domyślne filtrowanie dzienników obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3596-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="d3596-121">Jednak zdarzenia z poziomami ważności "Start" i "Stop" uniemożliwiają tworzenie danych wyjściowych dziennika.</span><span class="sxs-lookup"><span data-stu-id="d3596-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="d3596-122">Filtrowanie dla wszystkich odbiorników my. Application. log</span><span class="sxs-lookup"><span data-stu-id="d3596-122">Filtering for All My.Application.Log Listeners</span></span>  
 <span data-ttu-id="d3596-123">`WriteException` `WriteEntry` Obiekt używa nazwy do`DefaultSwitch` kontrolowania, które wiadomości są przekazywane z i metod do odbiorników dziennika. <xref:System.Diagnostics.SourceSwitch> `My.Application.Log`</span><span class="sxs-lookup"><span data-stu-id="d3596-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="d3596-124">Można skonfigurować `DefaultSwitch` w pliku konfiguracyjnym aplikacji, ustawiając jego wartość na jedną <xref:System.Diagnostics.SourceLevels> z wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d3596-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="d3596-125">Wartością domyślną jest "informacje".</span><span class="sxs-lookup"><span data-stu-id="d3596-125">By default, its value is "Information".</span></span>  
  
 <span data-ttu-id="d3596-126">W tej tabeli przedstawiono poziom ważności wymagany dla dziennika w celu zapisania komunikatu do odbiorników z uwzględnieniem konkretnego `DefaultSwitch` ustawienia.</span><span class="sxs-lookup"><span data-stu-id="d3596-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>  
  
|<span data-ttu-id="d3596-127">DefaultSwitch wartość</span><span class="sxs-lookup"><span data-stu-id="d3596-127">DefaultSwitch Value</span></span>|<span data-ttu-id="d3596-128">Ważność komunikatu jest wymagana dla danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="d3596-128">Message severity required for output</span></span>|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|<span data-ttu-id="d3596-129">`Critical` lub `Error`</span><span class="sxs-lookup"><span data-stu-id="d3596-129">`Critical` or `Error`</span></span>|  
|`Warning`|<span data-ttu-id="d3596-130">`Critical`, `Error`lub`Warning`</span><span class="sxs-lookup"><span data-stu-id="d3596-130">`Critical`, `Error`, or `Warning`</span></span>|  
|`Information`|<span data-ttu-id="d3596-131">`Critical`, `Error`, `Warning`lub`Information`</span><span class="sxs-lookup"><span data-stu-id="d3596-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|  
|`Verbose`|<span data-ttu-id="d3596-132">`Critical`, `Error`, `Warning`, lub`Information``Verbose`</span><span class="sxs-lookup"><span data-stu-id="d3596-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|  
|`ActivityTracing`|<span data-ttu-id="d3596-133">`Start`, `Stop`, `Suspend`, lub`Resume``Transfer`</span><span class="sxs-lookup"><span data-stu-id="d3596-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|  
|`All`|<span data-ttu-id="d3596-134">Dozwolone są wszystkie komunikaty.</span><span class="sxs-lookup"><span data-stu-id="d3596-134">All messages are allowed.</span></span>|  
|`Off`|<span data-ttu-id="d3596-135">Wszystkie komunikaty są blokowane.</span><span class="sxs-lookup"><span data-stu-id="d3596-135">All messages are blocked.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="d3596-136">Metody `WriteEntry` i`WriteException` każdy mają Przeciążenie, które nie określają poziomu ważności.</span><span class="sxs-lookup"><span data-stu-id="d3596-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="d3596-137">Niejawny poziom `WriteEntry` ważności przeciążenia to "informacje" i niejawny poziom `WriteException` ważności przeciążenia to "Error".</span><span class="sxs-lookup"><span data-stu-id="d3596-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>  
  
 <span data-ttu-id="d3596-138">W tej tabeli objaśniono dane wyjściowe dziennika pokazane w poprzednim przykładzie: z `DefaultSwitch` domyślnym ustawieniem "informacje", tylko drugie wywołanie `WriteEntry` metody `WriteException` i wywołanie metody generowanie danych wyjściowych dziennika.</span><span class="sxs-lookup"><span data-stu-id="d3596-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="d3596-139">Aby rejestrować tylko zdarzenia śledzenia aktywności</span><span class="sxs-lookup"><span data-stu-id="d3596-139">To log only activity tracing events</span></span>  
  
1. <span data-ttu-id="d3596-140">Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="d3596-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>  
  
     <span data-ttu-id="d3596-141">—lub—</span><span class="sxs-lookup"><span data-stu-id="d3596-141">-or-</span></span>  
  
     <span data-ttu-id="d3596-142">Jeśli nie ma pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="d3596-142">If there is no app.config file:</span></span>  
  
    1. <span data-ttu-id="d3596-143">W menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d3596-143">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="d3596-144">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="d3596-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="d3596-145">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d3596-145">Click **Add**.</span></span>  
  
2. <span data-ttu-id="d3596-146">Znajdź sekcję znajdującą się `<system.diagnostics>` w sekcji, która znajduje się w sekcji najwyższego poziomu `<configuration>`. `<switches>`</span><span class="sxs-lookup"><span data-stu-id="d3596-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>  
  
3. <span data-ttu-id="d3596-147">Znajdź element, który dodaje `DefaultSwitch` do kolekcji przełączników.</span><span class="sxs-lookup"><span data-stu-id="d3596-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="d3596-148">Powinien wyglądać podobnie do tego elementu:</span><span class="sxs-lookup"><span data-stu-id="d3596-148">It should look similar to this element:</span></span>  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4. <span data-ttu-id="d3596-149">Zmień wartość `value` atrybutu na "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="d3596-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>  
  
5. <span data-ttu-id="d3596-150">Zawartość pliku App. config powinna wyglądać podobnie do następującego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="d3596-150">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
6. <span data-ttu-id="d3596-151">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="d3596-151">Run the application in the debugger.</span></span>  
  
7. <span data-ttu-id="d3596-152">Naciśnij pozycję **Button1**.</span><span class="sxs-lookup"><span data-stu-id="d3596-152">Press **Button1**.</span></span>  
  
     <span data-ttu-id="d3596-153">Aplikacja zapisuje następujące informacje w danych wyjściowych debugowania aplikacji i pliku dziennika:</span><span class="sxs-lookup"><span data-stu-id="d3596-153">The application writes the following information to the application's debug output and log file:</span></span>  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8. <span data-ttu-id="d3596-154">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="d3596-154">Close the application.</span></span>  
  
9. <span data-ttu-id="d3596-155">Zmień wartość `value` atrybutu z powrotem na "informacje".</span><span class="sxs-lookup"><span data-stu-id="d3596-155">Change the value of the `value` attribute back to "Information".</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d3596-156">`DefaultSwitch` Ustawienia`My.Application.Log`przełącznika.</span><span class="sxs-lookup"><span data-stu-id="d3596-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="d3596-157">Nie zmienia to sposobu zachowania .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> i <xref:System.Diagnostics.Debug?displayProperty=nameWithType> klas.</span><span class="sxs-lookup"><span data-stu-id="d3596-157">It does not change how the .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="d3596-158">Indywidualne filtrowanie dla odbiorników my. Application. log</span><span class="sxs-lookup"><span data-stu-id="d3596-158">Individual Filtering For My.Application.Log Listeners</span></span>  
 <span data-ttu-id="d3596-159">W poprzednim przykładzie pokazano, jak zmienić filtrowanie dla wszystkich `My.Application.Log` danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d3596-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="d3596-160">Ten przykład ilustruje sposób filtrowania poszczególnych odbiorników dziennika.</span><span class="sxs-lookup"><span data-stu-id="d3596-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="d3596-161">Domyślnie aplikacja ma dwa detektory, które zapisują w danych wyjściowych debugowania aplikacji i pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="d3596-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>  
  
 <span data-ttu-id="d3596-162">Plik konfiguracji steruje zachowaniem detektorów dzienników, umożliwiając każdemu z nich filtr, który jest podobny do przełącznika `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="d3596-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="d3596-163">Odbiornik dziennika będzie wyprowadzał komunikat tylko wtedy, gdy ważność komunikatu jest dozwolona zarówno w przypadku filtru, `DefaultSwitch` jak i dla filtra odbiornika dzienników.</span><span class="sxs-lookup"><span data-stu-id="d3596-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>  
  
 <span data-ttu-id="d3596-164">W tym przykładzie pokazano, jak skonfigurować filtrowanie dla nowego odbiornika debugowania i dodać go do `Log` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3596-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="d3596-165">Domyślny odbiornik debugowania powinien zostać usunięty z `Log` obiektu, dlatego jest jasne, że komunikaty debugowania pochodzą z nowego odbiornika debugowania.</span><span class="sxs-lookup"><span data-stu-id="d3596-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="d3596-166">Aby rejestrować tylko zdarzenia śledzenia działania</span><span class="sxs-lookup"><span data-stu-id="d3596-166">To log only activity-tracing events</span></span>  
  
1. <span data-ttu-id="d3596-167">Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="d3596-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="d3596-168">—lub—</span><span class="sxs-lookup"><span data-stu-id="d3596-168">-or-</span></span>  
  
     <span data-ttu-id="d3596-169">Jeśli nie ma pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="d3596-169">If there is no app.config file:</span></span>  
  
    1. <span data-ttu-id="d3596-170">W menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d3596-170">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="d3596-171">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="d3596-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="d3596-172">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d3596-172">Click **Add**.</span></span>  
  
2. <span data-ttu-id="d3596-173">Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d3596-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="d3596-174">Wybierz pozycję **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="d3596-174">Choose **Open**.</span></span>  
  
3. <span data-ttu-id="d3596-175">Znajdź sekcję w sekcji z `name` atrybutem `<sources>` "DefaultSource", który znajduje się poniżej sekcji. `<source>` `<listeners>`</span><span class="sxs-lookup"><span data-stu-id="d3596-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="d3596-176">Sekcja znajduje się `<system.diagnostics>` poniżej sekcji w sekcji najwyższego poziomu `<configuration>`. `<sources>`</span><span class="sxs-lookup"><span data-stu-id="d3596-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
4. <span data-ttu-id="d3596-177">Dodaj ten element do `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="d3596-177">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5. <span data-ttu-id="d3596-178">`<sharedListeners>` Znajdź sekcję `<system.diagnostics>` w sekcji, w sekcji najwyższego poziomu `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="d3596-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6. <span data-ttu-id="d3596-179">Dodaj ten element do tej `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="d3596-179">Add this element to that `<sharedListeners>` section:</span></span>  
  
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
  
     <span data-ttu-id="d3596-180">Filtr przyjmuje jedną <xref:System.Diagnostics.SourceLevels> z wartości wyliczenia jako `initializeData` atrybut. <xref:System.Diagnostics.EventTypeFilter></span><span class="sxs-lookup"><span data-stu-id="d3596-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>  
  
7. <span data-ttu-id="d3596-181">Zawartość pliku App. config powinna wyglądać podobnie do następującego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="d3596-181">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
8. <span data-ttu-id="d3596-182">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="d3596-182">Run the application in the debugger.</span></span>  
  
9. <span data-ttu-id="d3596-183">Naciśnij pozycję **Button1**.</span><span class="sxs-lookup"><span data-stu-id="d3596-183">Press **Button1**.</span></span>  
  
     <span data-ttu-id="d3596-184">Aplikacja zapisuje następujące informacje w pliku dziennika aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d3596-184">The application writes the following information to the application's log file:</span></span>  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     <span data-ttu-id="d3596-185">Aplikacja zapisuje mniej informacji do danych wyjściowych debugowania aplikacji ze względu na bardziej restrykcyjne filtrowanie.</span><span class="sxs-lookup"><span data-stu-id="d3596-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>  
  
     `Default Error   2   Error`  
  
10. <span data-ttu-id="d3596-186">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="d3596-186">Close the application.</span></span>  
  
 <span data-ttu-id="d3596-187">Aby uzyskać więcej informacji na temat zmiany ustawień dziennika po wdrożeniu, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="d3596-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3596-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3596-188">See also</span></span>

- [<span data-ttu-id="d3596-189">Przewodnik: Ustalanie, gdzie my. Application. Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="d3596-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="d3596-190">Przewodnik: Zmienianie, gdzie my. Application. Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="d3596-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="d3596-191">Przewodnik: Tworzenie niestandardowych odbiorników dziennika</span><span class="sxs-lookup"><span data-stu-id="d3596-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="d3596-192">Instrukcje: Zapisuj komunikaty dziennika</span><span class="sxs-lookup"><span data-stu-id="d3596-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="d3596-193">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="d3596-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="d3596-194">Rejestrowanie informacji z aplikacji</span><span class="sxs-lookup"><span data-stu-id="d3596-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
