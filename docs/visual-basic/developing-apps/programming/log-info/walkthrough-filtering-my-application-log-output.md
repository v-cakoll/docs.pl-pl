---
title: Filtrowanie danych wyjściowych My.Application.Log (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c048578b320fedd2153aee7b466b1494551abe0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="aec38-102">Wskazówki: filtrowanie danych wyjściowych My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aec38-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>
<span data-ttu-id="aec38-103">W tym przewodniku przedstawiono sposób zmiany domyślnego dziennika filtrowania `My.Application.Log` obiekt, aby kontrolować, jakie informacje są przekazywane z `Log` obiektu odbiorniki i jakie informacje są zapisywane przez odbiorniki.</span><span class="sxs-lookup"><span data-stu-id="aec38-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="aec38-104">Zachowanie rejestrowania można zmienić nawet po tworzenia aplikacji, ponieważ informacje o konfiguracji są przechowywane w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aec38-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="aec38-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="aec38-105">Getting Started</span></span>  
 <span data-ttu-id="aec38-106">Każdy komunikat, który `My.Application.Log` zapisy ma poziom ważności skojarzony, w których mechanizmy filtrowania umożliwia sterowanie wpisu w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="aec38-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="aec38-107">Ta przykładowa aplikacja korzysta `My.Application.Log` metod można zapisać kilka komunikaty dziennika z różne poziomy ważności.</span><span class="sxs-lookup"><span data-stu-id="aec38-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>  
  
#### <a name="to-build-the-sample-application"></a><span data-ttu-id="aec38-108">Do tworzenia przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="aec38-108">To build the sample application</span></span>  
  
1.  <span data-ttu-id="aec38-109">Otwórz nowy projekt aplikacji systemu Windows w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="aec38-109">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="aec38-110">Dodawanie przycisku o nazwie Button1 do Form1.</span><span class="sxs-lookup"><span data-stu-id="aec38-110">Add a button named Button1 to Form1.</span></span>  
  
3.  <span data-ttu-id="aec38-111">W <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla Button1, Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="aec38-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  <span data-ttu-id="aec38-112">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="aec38-112">Run the application in the debugger.</span></span>  
  
5.  <span data-ttu-id="aec38-113">Naciśnij klawisz **Button1**.</span><span class="sxs-lookup"><span data-stu-id="aec38-113">Press **Button1**.</span></span>  
  
     <span data-ttu-id="aec38-114">Aplikacja zapisuje następujące informacje do pliku wyjściowego i dziennika debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aec38-114">The application writes the following information to the application's debug output and log file.</span></span>  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  <span data-ttu-id="aec38-115">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="aec38-115">Close the application.</span></span>  
  
     <span data-ttu-id="aec38-116">Aby uzyskać informacje o sposobie wyświetlania okno danych wyjściowych debugowania aplikacji, zobacz [okno danych wyjściowych](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="aec38-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="aec38-117">Aby uzyskać informacje o lokalizacji pliku dziennika aplikacji, zobacz [wskazówki: Ustalanie gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="aec38-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aec38-118">Domyślnie aplikacja Opróżnia dane wyjściowe pliku dziennika, po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aec38-118">By default, the application flushes the log-file output when the application closes.</span></span>  
  
     <span data-ttu-id="aec38-119">W przykładzie powyżej, drugie wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> — metoda i wywołania w celu <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> generuje danych wyjściowych dziennika podczas wywołania imię i nazwisko `WriteEntry` — metoda nie.</span><span class="sxs-lookup"><span data-stu-id="aec38-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="aec38-120">Jest to spowodowane poziomy ważności `WriteEntry` i `WriteException` "Informacje" i "Błąd", które są dozwolone w `My.Application.Log` obiektu domyślne dziennika filtrowania.</span><span class="sxs-lookup"><span data-stu-id="aec38-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="aec38-121">Jednak zdarzenia z poziomami ważności "Start" i "Stop" nie generuje danych wyjściowych dziennika.</span><span class="sxs-lookup"><span data-stu-id="aec38-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="aec38-122">Filtrowanie w przypadku wszystkich odbiorników My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="aec38-122">Filtering for All My.Application.Log Listeners</span></span>  
 <span data-ttu-id="aec38-123">`My.Application.Log` Obiekt używa <xref:System.Diagnostics.SourceSwitch> o nazwie `DefaultSwitch` kontrolowanie, które komunikaty go przekazuje z `WriteEntry` i `WriteException` metody odbiorniki dzienników.</span><span class="sxs-lookup"><span data-stu-id="aec38-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="aec38-124">Można skonfigurować `DefaultSwitch` w pliku konfiguracyjnym aplikacji przez ustawienie jej wartość na jedną z <xref:System.Diagnostics.SourceLevels> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="aec38-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="aec38-125">Domyślna wartość to "Informacje".</span><span class="sxs-lookup"><span data-stu-id="aec38-125">By default, its value is "Information".</span></span>  
  
 <span data-ttu-id="aec38-126">W poniższej tabeli przedstawiono poziom ważności wymagane dla dziennika do zapisu komunikatu odbiorników, podane określonego `DefaultSwitch` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="aec38-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>  
  
|<span data-ttu-id="aec38-127">Wartość DefaultSwitch</span><span class="sxs-lookup"><span data-stu-id="aec38-127">DefaultSwitch Value</span></span>|<span data-ttu-id="aec38-128">Ważność komunikatu wymagane dla danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="aec38-128">Message severity required for output</span></span>|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|<span data-ttu-id="aec38-129">`Critical` lub `Error`</span><span class="sxs-lookup"><span data-stu-id="aec38-129">`Critical` or `Error`</span></span>|  
|`Warning`|<span data-ttu-id="aec38-130">`Critical`, `Error`, lub `Warning`</span><span class="sxs-lookup"><span data-stu-id="aec38-130">`Critical`, `Error`, or `Warning`</span></span>|  
|`Information`|<span data-ttu-id="aec38-131">`Critical`, `Error`, `Warning`, lub `Information`</span><span class="sxs-lookup"><span data-stu-id="aec38-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|  
|`Verbose`|<span data-ttu-id="aec38-132">`Critical`, `Error`, `Warning`, `Information`, lub `Verbose`</span><span class="sxs-lookup"><span data-stu-id="aec38-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|  
|`ActivityTracing`|<span data-ttu-id="aec38-133">`Start`, `Stop`, `Suspend`, `Resume`, lub `Transfer`</span><span class="sxs-lookup"><span data-stu-id="aec38-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|  
|`All`|<span data-ttu-id="aec38-134">Wszystkie komunikaty są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="aec38-134">All messages are allowed.</span></span>|  
|`Off`|<span data-ttu-id="aec38-135">Wszystkie komunikaty są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="aec38-135">All messages are blocked.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="aec38-136">`WriteEntry` i `WriteException` metody mają przeciążenia, która nie określa poziom ważności.</span><span class="sxs-lookup"><span data-stu-id="aec38-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="aec38-137">Poziom ważności niejawne `WriteEntry` jest przeciążenie "Informacje", a poziom ważności niejawne `WriteException` jest przeciążenie "Error".</span><span class="sxs-lookup"><span data-stu-id="aec38-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>  
  
 <span data-ttu-id="aec38-138">W następującej tabeli opisano w poprzednim przykładzie wpisu w dzienniku: przy użyciu domyślnego `DefaultSwitch` ustawienie "Informacje", tylko drugie wywołanie `WriteEntry` — metoda i wywołania w celu `WriteException` danych wyjściowych metody produktu dziennika.</span><span class="sxs-lookup"><span data-stu-id="aec38-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="aec38-139">Aby rejestrować zdarzenia śledzenia tylko działania</span><span class="sxs-lookup"><span data-stu-id="aec38-139">To log only activity tracing events</span></span>  
  
1.  <span data-ttu-id="aec38-140">Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="aec38-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>  
  
     <span data-ttu-id="aec38-141">—lub—</span><span class="sxs-lookup"><span data-stu-id="aec38-141">-or-</span></span>  
  
     <span data-ttu-id="aec38-142">Jeśli plik app.config, nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="aec38-142">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="aec38-143">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="aec38-143">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="aec38-144">Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="aec38-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="aec38-145">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="aec38-145">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="aec38-146">Zlokalizuj `<switches>` sekcję, co jest `<system.diagnostics>` sekcję, co jest najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="aec38-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="aec38-147">Znajdź element, który dodaje `DefaultSwitch` do kolekcji parametrów.</span><span class="sxs-lookup"><span data-stu-id="aec38-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="aec38-148">Powinien być podobny do tego elementu:</span><span class="sxs-lookup"><span data-stu-id="aec38-148">It should look similar to this element:</span></span>  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  <span data-ttu-id="aec38-149">Zmień wartość `value` atrybutu "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="aec38-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>  
  
5.  <span data-ttu-id="aec38-150">Zawartość pliku app.config powinny być podobne do następującego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="aec38-150">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
6.  <span data-ttu-id="aec38-151">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="aec38-151">Run the application in the debugger.</span></span>  
  
7.  <span data-ttu-id="aec38-152">Naciśnij klawisz **Button1**.</span><span class="sxs-lookup"><span data-stu-id="aec38-152">Press **Button1**.</span></span>  
  
     <span data-ttu-id="aec38-153">Aplikacja zapisuje następujące informacje w pliku danych wyjściowych i dziennika debugowania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="aec38-153">The application writes the following information to the application's debug output and log file:</span></span>  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  <span data-ttu-id="aec38-154">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="aec38-154">Close the application.</span></span>  
  
9. <span data-ttu-id="aec38-155">Zmień wartość `value` atrybutu "Informacje".</span><span class="sxs-lookup"><span data-stu-id="aec38-155">Change the value of the `value` attribute back to "Information".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aec38-156">`DefaultSwitch` Przełącznika tylko formanty ustawienie `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="aec38-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="aec38-157">Nie zmienia sposób [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> i <xref:System.Diagnostics.Debug?displayProperty=nameWithType> zachowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="aec38-157">It does not change how the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="aec38-158">Poszczególne filtrowanie w przypadku odbiorników My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="aec38-158">Individual Filtering For My.Application.Log Listeners</span></span>  
 <span data-ttu-id="aec38-159">Poprzednim przykładzie pokazano, jak zmienić ustawienia filtrowania dla wszystkich `My.Application.Log` danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="aec38-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="aec38-160">W tym przykładzie przedstawiono sposób filtrowania odbiornik osobny dziennik.</span><span class="sxs-lookup"><span data-stu-id="aec38-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="aec38-161">Domyślnie aplikacja ma dwa odbiorniki tego zapisu w danych wyjściowych debugowania aplikacji i pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="aec38-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>  
  
 <span data-ttu-id="aec38-162">Plik konfiguracji steruje zachowaniem odbiorniki logu zezwalając każdej z nich ma filtr, który jest podobny do przełącznika dla `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="aec38-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="aec38-163">Odbiornik dziennika dane wyjściowe obejmują wiadomości tylko wtedy, gdy ważność komunikatu jest dozwolony w obu dziennika `DefaultSwitch` i odbiornika dziennika filtru.</span><span class="sxs-lookup"><span data-stu-id="aec38-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>  
  
 <span data-ttu-id="aec38-164">W tym przykładzie pokazano, jak skonfigurować filtrowanie dla nowego odbiornika debugowania i dodaj go do `Log` obiektu.</span><span class="sxs-lookup"><span data-stu-id="aec38-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="aec38-165">Odbiornik debugowania domyślna powinna zostać usunięta z `Log` obiektu, więc jest jasne, czy komunikaty debugowania pochodzą z nowego odbiornika debugowania.</span><span class="sxs-lookup"><span data-stu-id="aec38-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="aec38-166">Do rejestrowania tylko działania śledzenia zdarzeń</span><span class="sxs-lookup"><span data-stu-id="aec38-166">To log only activity-tracing events</span></span>  
  
1.  <span data-ttu-id="aec38-167">Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="aec38-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="aec38-168">—lub—</span><span class="sxs-lookup"><span data-stu-id="aec38-168">-or-</span></span>  
  
     <span data-ttu-id="aec38-169">Jeśli plik app.config, nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="aec38-169">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="aec38-170">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="aec38-170">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="aec38-171">Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="aec38-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="aec38-172">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="aec38-172">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="aec38-173">Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="aec38-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="aec38-174">Wybierz **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="aec38-174">Choose **Open**.</span></span>  
  
3.  <span data-ttu-id="aec38-175">Zlokalizuj `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource", która znajduje się w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="aec38-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="aec38-176">`<sources>` Znajduje się w sekcji `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="aec38-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
4.  <span data-ttu-id="aec38-177">Ten element, aby dodać `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="aec38-177">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  <span data-ttu-id="aec38-178">Zlokalizuj `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="aec38-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="aec38-179">Dodaj ten element, do którego `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="aec38-179">Add this element to that `<sharedListeners>` section:</span></span>  
  
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
  
     <span data-ttu-id="aec38-180"><xref:System.Diagnostics.EventTypeFilter> Filtru przyjmuje jeden z <xref:System.Diagnostics.SourceLevels> wyliczenia wartości jako jego `initializeData` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="aec38-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>  
  
7.  <span data-ttu-id="aec38-181">Zawartość pliku app.config powinny być podobne do następującego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="aec38-181">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
8.  <span data-ttu-id="aec38-182">Uruchom aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="aec38-182">Run the application in the debugger.</span></span>  
  
9. <span data-ttu-id="aec38-183">Naciśnij klawisz **Button1**.</span><span class="sxs-lookup"><span data-stu-id="aec38-183">Press **Button1**.</span></span>  
  
     <span data-ttu-id="aec38-184">Aplikacja zapisuje następujące informacje w pliku dziennika aplikacji:</span><span class="sxs-lookup"><span data-stu-id="aec38-184">The application writes the following information to the application's log file:</span></span>  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     <span data-ttu-id="aec38-185">Aplikacja zapisuje mniej informacje w danych wyjściowych debugowania aplikacji ze względu na bardziej restrykcyjne filtrowania.</span><span class="sxs-lookup"><span data-stu-id="aec38-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>  
  
     `Default Error   2   Error`  
  
10. <span data-ttu-id="aec38-186">Zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="aec38-186">Close the application.</span></span>  
  
 <span data-ttu-id="aec38-187">Aby uzyskać więcej informacji na temat zmiany ustawień dziennika po wdrożeniu, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="aec38-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec38-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aec38-188">See Also</span></span>  
 [<span data-ttu-id="aec38-189">Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="aec38-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="aec38-190">Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="aec38-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="aec38-191">Przewodnik: tworzenie odbiorców dzienników niestandardowych</span><span class="sxs-lookup"><span data-stu-id="aec38-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 [<span data-ttu-id="aec38-192">Instrukcje: zapisywanie komunikatów dziennika</span><span class="sxs-lookup"><span data-stu-id="aec38-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="aec38-193">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="aec38-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="aec38-194">Rejestrowanie informacji z aplikacji</span><span class="sxs-lookup"><span data-stu-id="aec38-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
