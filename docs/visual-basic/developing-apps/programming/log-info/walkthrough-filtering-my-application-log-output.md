---
title: filtrowanie danych wyjściowych elementu My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353592"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="3626b-102">Wskazówki: filtrowanie danych wyjściowych My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3626b-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>

<span data-ttu-id="3626b-103">W tym przewodniku pokazano, jak zmienić domyślne `My.Application.Log` filtrowanie dziennika dla obiektu, `Log` aby kontrolować, jakie informacje są przekazywane z obiektu do odbiorników i jakie informacje są zapisywane przez detektory.</span><span class="sxs-lookup"><span data-stu-id="3626b-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="3626b-104">Zachowanie rejestrowania można zmienić nawet po zbudowaniu aplikacji, ponieważ informacje o konfiguracji są przechowywane w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3626b-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>

## <a name="getting-started"></a><span data-ttu-id="3626b-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="3626b-105">Getting Started</span></span>

<span data-ttu-id="3626b-106">Każdy komunikat, który `My.Application.Log` pisze ma skojarzony poziom ważności, który mechanizmy filtrowania używać do kontrolowania danych wyjściowych dziennika.</span><span class="sxs-lookup"><span data-stu-id="3626b-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="3626b-107">Ta przykładowa `My.Application.Log` aplikacja używa metod do zapisu kilku komunikatów dziennika o różnych poziomach ważności.</span><span class="sxs-lookup"><span data-stu-id="3626b-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>

#### <a name="to-build-the-sample-application"></a><span data-ttu-id="3626b-108">Aby utworzyć przykładową aplikację</span><span class="sxs-lookup"><span data-stu-id="3626b-108">To build the sample application</span></span>

1. <span data-ttu-id="3626b-109">Otwórz nowy projekt aplikacji systemu Windows visual basic.</span><span class="sxs-lookup"><span data-stu-id="3626b-109">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="3626b-110">Dodaj przycisk o nazwie Button1 do formularza1.</span><span class="sxs-lookup"><span data-stu-id="3626b-110">Add a button named Button1 to Form1.</span></span>

3. <span data-ttu-id="3626b-111">W <xref:System.Windows.Forms.Control.Click> programie obsługi zdarzeń dla Button1 dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="3626b-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. <span data-ttu-id="3626b-112">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="3626b-112">Run the application in the debugger.</span></span>

5. <span data-ttu-id="3626b-113">Naciśnij **przycisk1**.</span><span class="sxs-lookup"><span data-stu-id="3626b-113">Press **Button1**.</span></span>

     <span data-ttu-id="3626b-114">Aplikacja zapisuje następujące informacje do pliku wyjściowego debugowania i dziennika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3626b-114">The application writes the following information to the application's debug output and log file.</span></span>

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. <span data-ttu-id="3626b-115">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="3626b-115">Close the application.</span></span>

     <span data-ttu-id="3626b-116">Aby uzyskać informacje dotyczące sposobu wyświetlania okna wyjściowego debugowania aplikacji, zobacz [Okno wyjściowe](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="3626b-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="3626b-117">Aby uzyskać informacje na temat lokalizacji pliku dziennika aplikacji, zobacz [Instruktaż: Określanie, gdzie my.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="3626b-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="3626b-118">Domyślnie aplikacja opróżnia dane wyjściowe pliku dziennika po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3626b-118">By default, the application flushes the log-file output when the application closes.</span></span>

     <span data-ttu-id="3626b-119">W powyższym przykładzie drugie <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> wywołanie metody i <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> wywołanie metody daje dane wyjściowe dziennika, podczas gdy pierwsze i ostatnie wywołania `WriteEntry` metody nie.</span><span class="sxs-lookup"><span data-stu-id="3626b-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="3626b-120">Jest to spowodowane poziom `WriteEntry` ważności `WriteException` i są "Informacje" i "Błąd", z `My.Application.Log` których oba są dozwolone przez domyślne filtrowanie dziennika obiektu.</span><span class="sxs-lookup"><span data-stu-id="3626b-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="3626b-121">Jednak zdarzenia z poziomami ważności "Start" i "Stop" nie mogą wytwarzania danych wyjściowych dziennika.</span><span class="sxs-lookup"><span data-stu-id="3626b-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>

## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="3626b-122">Filtrowanie dla wszystkich detektorów My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="3626b-122">Filtering for All My.Application.Log Listeners</span></span>

<span data-ttu-id="3626b-123">Obiekt `My.Application.Log` <xref:System.Diagnostics.SourceSwitch> używa `DefaultSwitch` nazwany do kontrolowania, które komunikaty przechodzi z `WriteEntry` i `WriteException` metody do detektorów dziennika.</span><span class="sxs-lookup"><span data-stu-id="3626b-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="3626b-124">Można skonfigurować `DefaultSwitch` w pliku konfiguracyjnym aplikacji, ustawiając jego wartość na jedną z wartości wyliczenia. <xref:System.Diagnostics.SourceLevels></span><span class="sxs-lookup"><span data-stu-id="3626b-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="3626b-125">Domyślnie jego wartość to "Informacje".</span><span class="sxs-lookup"><span data-stu-id="3626b-125">By default, its value is "Information".</span></span>

<span data-ttu-id="3626b-126">W tej tabeli przedstawiono poziom ważności wymagany dla dziennika do zapisu wiadomości do odbiorników, biorąc pod uwagę określone `DefaultSwitch` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="3626b-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>

|<span data-ttu-id="3626b-127">Domyślna wartość przełącznika</span><span class="sxs-lookup"><span data-stu-id="3626b-127">DefaultSwitch Value</span></span>|<span data-ttu-id="3626b-128">Ważność wiadomości wymagana dla danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="3626b-128">Message severity required for output</span></span>|
|---|---|
|`Critical`|`Critical`|
|`Error`|<span data-ttu-id="3626b-129">`Critical` lub `Error`</span><span class="sxs-lookup"><span data-stu-id="3626b-129">`Critical` or `Error`</span></span>|
|`Warning`|<span data-ttu-id="3626b-130">`Critical`, `Error`, lub`Warning`</span><span class="sxs-lookup"><span data-stu-id="3626b-130">`Critical`, `Error`, or `Warning`</span></span>|
|`Information`|<span data-ttu-id="3626b-131">`Critical`, `Error` `Warning`, , lub`Information`</span><span class="sxs-lookup"><span data-stu-id="3626b-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|
|`Verbose`|<span data-ttu-id="3626b-132">`Critical`, `Error` `Warning`, `Information`, , lub`Verbose`</span><span class="sxs-lookup"><span data-stu-id="3626b-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|
|`ActivityTracing`|<span data-ttu-id="3626b-133">`Start`, `Stop` `Suspend`, `Resume`, , lub`Transfer`</span><span class="sxs-lookup"><span data-stu-id="3626b-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|
|`All`|<span data-ttu-id="3626b-134">Wszystkie wiadomości są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3626b-134">All messages are allowed.</span></span>|
|`Off`|<span data-ttu-id="3626b-135">Wszystkie wiadomości są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="3626b-135">All messages are blocked.</span></span>|

> [!NOTE]
> <span data-ttu-id="3626b-136">I `WriteEntry` `WriteException` metody każdy ma przeciążenie, które nie określa poziomu ważności.</span><span class="sxs-lookup"><span data-stu-id="3626b-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="3626b-137">Niejawny poziom ważności `WriteEntry` przeciążenia jest "Informacje", a poziom niejawnego ważności `WriteException` przeciążenia jest "Błąd".</span><span class="sxs-lookup"><span data-stu-id="3626b-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>

<span data-ttu-id="3626b-138">W tej tabeli wyjaśniono dane wyjściowe `DefaultSwitch` dziennika pokazane w poprzednim przykładzie: `WriteEntry` z domyślnym `WriteException` ustawieniem "Informacje", tylko drugie wywołanie metody i wywołanie metody produkcji danych wyjściowych dziennika.</span><span class="sxs-lookup"><span data-stu-id="3626b-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="3626b-139">Aby rejestrować tylko zdarzenia śledzenia aktywności</span><span class="sxs-lookup"><span data-stu-id="3626b-139">To log only activity tracing events</span></span>

1. <span data-ttu-id="3626b-140">Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="3626b-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>

     <span data-ttu-id="3626b-141">— lub —</span><span class="sxs-lookup"><span data-stu-id="3626b-141">-or-</span></span>

     <span data-ttu-id="3626b-142">Jeśli nie ma pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="3626b-142">If there is no app.config file:</span></span>

    1. <span data-ttu-id="3626b-143">W menu **Projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="3626b-143">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="3626b-144">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="3626b-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="3626b-145">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="3626b-145">Click **Add**.</span></span>

2. <span data-ttu-id="3626b-146">Zlokalizuj sekcję, `<switches>` która znajduje się `<system.diagnostics>` w `<configuration>` sekcji najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="3626b-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="3626b-147">Znajdź element, `DefaultSwitch` który dodaje do kolekcji przełączników.</span><span class="sxs-lookup"><span data-stu-id="3626b-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="3626b-148">Powinien wyglądać podobnie do tego elementu:</span><span class="sxs-lookup"><span data-stu-id="3626b-148">It should look similar to this element:</span></span>

     `<add name="DefaultSwitch" value="Information" />`

4. <span data-ttu-id="3626b-149">Zmień wartość atrybutu na `value` "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="3626b-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>

5. <span data-ttu-id="3626b-150">Zawartość pliku app.config powinna być podobna do następującej opcji XML:</span><span class="sxs-lookup"><span data-stu-id="3626b-150">The content of the app.config file should be similar to the following XML:</span></span>

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

6. <span data-ttu-id="3626b-151">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="3626b-151">Run the application in the debugger.</span></span>

7. <span data-ttu-id="3626b-152">Naciśnij **przycisk1**.</span><span class="sxs-lookup"><span data-stu-id="3626b-152">Press **Button1**.</span></span>

     <span data-ttu-id="3626b-153">Aplikacja zapisuje następujące informacje do pliku wyjściowego i dziennika debugowania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="3626b-153">The application writes the following information to the application's debug output and log file:</span></span>

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. <span data-ttu-id="3626b-154">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="3626b-154">Close the application.</span></span>

9. <span data-ttu-id="3626b-155">Zmień wartość atrybutu `value` z powrotem na "Informacje".</span><span class="sxs-lookup"><span data-stu-id="3626b-155">Change the value of the `value` attribute back to "Information".</span></span>

    > [!NOTE]
    > <span data-ttu-id="3626b-156">Ustawienie `DefaultSwitch` przełącznika `My.Application.Log`steruje tylko .</span><span class="sxs-lookup"><span data-stu-id="3626b-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="3626b-157">Nie zmienia zachowania .NET <xref:System.Diagnostics.Trace?displayProperty=nameWithType> Framework <xref:System.Diagnostics.Debug?displayProperty=nameWithType> i klas.</span><span class="sxs-lookup"><span data-stu-id="3626b-157">It does not change how the .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>

## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="3626b-158">Indywidualne filtrowanie dla detektorów My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="3626b-158">Individual Filtering For My.Application.Log Listeners</span></span>

<span data-ttu-id="3626b-159">W poprzednim przykładzie pokazano, jak `My.Application.Log` zmienić filtrowanie dla wszystkich danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3626b-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="3626b-160">W tym przykładzie pokazano, jak filtrować odbiornika dziennika poszczególnych.</span><span class="sxs-lookup"><span data-stu-id="3626b-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="3626b-161">Domyślnie aplikacja ma dwa odbiorniki, które zapisują do danych wyjściowych debugowania aplikacji i pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="3626b-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>

<span data-ttu-id="3626b-162">Plik konfiguracyjny steruje zachowaniem detektorów dziennika, zezwalając każdemu z nich `My.Application.Log`na filtr, który jest podobny do przełącznika dla .</span><span class="sxs-lookup"><span data-stu-id="3626b-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="3626b-163">Odbiornik dziennika będzie wysyłać komunikat tylko wtedy, gdy ważność wiadomości jest `DefaultSwitch` dozwolone zarówno przez dziennik i filtr odbiornika dziennika.</span><span class="sxs-lookup"><span data-stu-id="3626b-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>

<span data-ttu-id="3626b-164">W tym przykładzie pokazano, jak skonfigurować filtrowanie dla nowego `Log` odbiornika debugowania i dodać go do obiektu.</span><span class="sxs-lookup"><span data-stu-id="3626b-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="3626b-165">Domyślny odbiornik debugowania powinny `Log` zostać usunięte z obiektu, więc jest jasne, że komunikaty debugowania pochodzą z nowego odbiornika debugowania.</span><span class="sxs-lookup"><span data-stu-id="3626b-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="3626b-166">Aby rejestrować tylko zdarzenia śledzenia aktywności</span><span class="sxs-lookup"><span data-stu-id="3626b-166">To log only activity-tracing events</span></span>

1. <span data-ttu-id="3626b-167">Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="3626b-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="3626b-168">\-lub-</span><span class="sxs-lookup"><span data-stu-id="3626b-168">\-or-</span></span>

     <span data-ttu-id="3626b-169">Jeśli nie ma pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="3626b-169">If there is no app.config file:</span></span>

    1. <span data-ttu-id="3626b-170">W menu **Projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="3626b-170">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="3626b-171">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="3626b-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="3626b-172">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="3626b-172">Click **Add**.</span></span>

2. <span data-ttu-id="3626b-173">Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="3626b-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="3626b-174">Wybierz **pozycję Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="3626b-174">Choose **Open**.</span></span>

3. <span data-ttu-id="3626b-175">Znajdź `<listeners>` sekcję w `<source>` sekcji `name` z atrybutem "DefaultSource", `<sources>` który znajduje się w sekcji.</span><span class="sxs-lookup"><span data-stu-id="3626b-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="3626b-176">Sekcja `<sources>` znajduje się `<system.diagnostics>` w sekcji, w `<configuration>` sekcji najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="3626b-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

4. <span data-ttu-id="3626b-177">Dodaj ten element `<listeners>` do sekcji:</span><span class="sxs-lookup"><span data-stu-id="3626b-177">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. <span data-ttu-id="3626b-178">Zlokalizuj `<sharedListeners>` `<system.diagnostics>` sekcję w sekcji `<configuration>` w sekcji najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="3626b-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="3626b-179">Dodaj ten element `<sharedListeners>` do tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="3626b-179">Add this element to that `<sharedListeners>` section:</span></span>

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

     <span data-ttu-id="3626b-180">Filtr <xref:System.Diagnostics.EventTypeFilter> przyjmuje jedną <xref:System.Diagnostics.SourceLevels> z wartości wyliczenia jako jego `initializeData` atrybut.</span><span class="sxs-lookup"><span data-stu-id="3626b-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>

7. <span data-ttu-id="3626b-181">Zawartość pliku app.config powinna być podobna do następującej opcji XML:</span><span class="sxs-lookup"><span data-stu-id="3626b-181">The content of the app.config file should be similar to the following XML:</span></span>

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

8. <span data-ttu-id="3626b-182">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="3626b-182">Run the application in the debugger.</span></span>

9. <span data-ttu-id="3626b-183">Naciśnij **przycisk1**.</span><span class="sxs-lookup"><span data-stu-id="3626b-183">Press **Button1**.</span></span>

     <span data-ttu-id="3626b-184">Aplikacja zapisuje następujące informacje do pliku dziennika aplikacji:</span><span class="sxs-lookup"><span data-stu-id="3626b-184">The application writes the following information to the application's log file:</span></span>

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     <span data-ttu-id="3626b-185">Aplikacja zapisuje mniej informacji do danych wyjściowych debugowania aplikacji ze względu na bardziej restrykcyjne filtrowanie.</span><span class="sxs-lookup"><span data-stu-id="3626b-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>

     `Default Error   2   Error`

10. <span data-ttu-id="3626b-186">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="3626b-186">Close the application.</span></span>

<span data-ttu-id="3626b-187">Aby uzyskać więcej informacji na temat zmiany ustawień dziennika po wdrożeniu, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="3626b-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3626b-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3626b-188">See also</span></span>

- [<span data-ttu-id="3626b-189">Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="3626b-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="3626b-190">Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="3626b-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="3626b-191">Przewodnik: tworzenie odbiorców dzienników niestandardowych</span><span class="sxs-lookup"><span data-stu-id="3626b-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="3626b-192">Porady: zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="3626b-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="3626b-193">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="3626b-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="3626b-194">Rejestrowanie informacji z aplikacji</span><span class="sxs-lookup"><span data-stu-id="3626b-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
