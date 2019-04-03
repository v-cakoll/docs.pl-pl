---
title: Praca z dziennikami aplikacji w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 00c54a59ccfe2a49dcf35b322ca077a10a48ae7d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839642"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="e79db-102">Praca z dziennikami aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e79db-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="e79db-103">`My.Application.Log` i `My.Log` obiektów ułatwiają zapisu rejestrowania i śledzenia informacji w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="e79db-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="e79db-104">Jak komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="e79db-104">How Messages are Logged</span></span>

<span data-ttu-id="e79db-105">Najpierw ważności komunikatu został sprawdzony i <xref:System.Diagnostics.TraceSource.Switch%2A> właściwości dziennika <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e79db-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="e79db-106">Przez domyślne, tylko komunikaty o ważności "Informacje" i nowszej są przekazywane do detektorów śledzenia określony w dzienniku `TraceListener` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e79db-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="e79db-107">Następnie każdego odbiornika porównuje ważność wiadomości do odbiornika <xref:System.Diagnostics.TraceSource.Switch%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e79db-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="e79db-108">Jeśli ważność komunikatu jest wystarczająco wysoka, odbiornik zapisuje się komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e79db-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="e79db-109">Na poniższym diagramie przedstawiono, w jaki sposób wiadomość zapisywane `WriteEntry` przekazywane do metody `WriteLine` obiekty nasłuchujące śledzenia metody dziennika:</span><span class="sxs-lookup"><span data-stu-id="e79db-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Diagram przedstawiający Moje wywołania dziennika.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="e79db-111">Możesz zmienić zachowanie dziennika i śledzenia słuchaczy, zmieniając pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e79db-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="e79db-112">Na poniższym diagramie przedstawiono związek między częściami dziennika i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e79db-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Diagram przedstawiający konfigurację dziennika.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="e79db-114">Gdzie są rejestrowane komunikaty</span><span class="sxs-lookup"><span data-stu-id="e79db-114">Where Messages are Logged</span></span>

<span data-ttu-id="e79db-115">Jeśli zestaw ma plik konfiguracji nie `My.Application.Log` i `My.Log` obiektów zapisywać dane wyjściowe debugowania aplikacji (za pośrednictwem <xref:System.Diagnostics.DefaultTraceListener> klasy).</span><span class="sxs-lookup"><span data-stu-id="e79db-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="e79db-116">Ponadto `My.Application.Log` obiekt zapisuje do pliku dziennika zestawu (za pośrednictwem <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy), gdy `My.Log` obiekt zapisuje dane wyjściowe strony sieci Web platformy ASP.NET (za pośrednictwem <xref:System.Web.WebPageTraceListener> klasy).</span><span class="sxs-lookup"><span data-stu-id="e79db-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="e79db-117">Dane wyjściowe debugowania mogą być wyświetlane w programie Visual Studio **dane wyjściowe** okna podczas uruchamiania aplikacji w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="e79db-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="e79db-118">Aby otworzyć **dane wyjściowe** okna, kliknij przycisk **debugowania** elementu menu, wskaż **Windows**, a następnie kliknij przycisk **dane wyjściowe**.</span><span class="sxs-lookup"><span data-stu-id="e79db-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="e79db-119">W **dane wyjściowe** wybierz **debugowania** z **Pokaż dane wyjściowe z** pole.</span><span class="sxs-lookup"><span data-stu-id="e79db-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="e79db-120">Domyślnie `My.Application.Log` zapisuje plik dziennika w ścieżce dla danych aplikacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e79db-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="e79db-121">Możesz uzyskać ścieżkę z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> właściwość <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e79db-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="e79db-122">Format tej ścieżki jest następująca:</span><span class="sxs-lookup"><span data-stu-id="e79db-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="e79db-123">Typowa wartość dla `BasePath` jest następujący.</span><span class="sxs-lookup"><span data-stu-id="e79db-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="e79db-124">C:\Documents and Settings\\`username`\Application danych</span><span class="sxs-lookup"><span data-stu-id="e79db-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="e79db-125">Wartości `CompanyName`, `ProductName`, i `ProductVersion` pochodzą z informacjami o zestawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e79db-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="e79db-126">Nazwa pliku dziennika jest *AssemblyName*.log, gdzie *AssemblyName* jest nazwą pliku zestawu bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e79db-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="e79db-127">Jeśli potrzebna jest więcej niż jeden plik dziennika, np. gdy oryginalny plik dziennika jest niedostępny podczas aplikacja próbuje zapisać w dzienniku, formularz dla nazwy pliku dziennika jest *AssemblyName*-*iteracji* .log, gdzie `iteration` jest dodatni `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e79db-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="e79db-128">Zachowanie domyślne można przesłonić, przez dodanie lub zmiana plik konfiguracji komputera i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e79db-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="e79db-129">Aby uzyskać więcej informacji, zobacz [instruktażu: Zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="e79db-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="e79db-130">Konfigurowanie ustawień dziennika</span><span class="sxs-lookup"><span data-stu-id="e79db-130">Configuring Log Settings</span></span>

<span data-ttu-id="e79db-131">`Log` Obiekt ma domyślną implementację, która działa bez pliku konfiguracji aplikacji, pliku app.config. Aby zmienić ustawienia domyślne, należy dodać plik konfiguracji z nowymi ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="e79db-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="e79db-132">Aby uzyskać więcej informacji, zobacz [instruktażu: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="e79db-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="e79db-133">W sekcjach konfiguracji dziennika znajdują się w `<system.diagnostics>` węzła w głównym `<configuration>` węzła pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="e79db-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="e79db-134">Informacje w dzienniku jest zdefiniowana w kilka węzłów:</span><span class="sxs-lookup"><span data-stu-id="e79db-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="e79db-135">Detektory `Log` obiektu są zdefiniowane w `<sources>` węzeł o nazwie DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="e79db-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="e79db-136">Filtr ważność `Log` obiekt jest zdefiniowany w `<switches>` węzeł o nazwie DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="e79db-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="e79db-137">Odbiorniki logu są zdefiniowane w `<sharedListeners>` węzła.</span><span class="sxs-lookup"><span data-stu-id="e79db-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="e79db-138">Przykłady `<sources>`, `<switches>`, i `<sharedListeners>` węzły są wyświetlane w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e79db-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="e79db-139">Zmiana ustawień dziennika po wdrożeniu</span><span class="sxs-lookup"><span data-stu-id="e79db-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="e79db-140">Podczas opracowywania aplikacji, jego ustawienia konfiguracji są przechowywane w pliku app.config, jak pokazano w przykładach.</span><span class="sxs-lookup"><span data-stu-id="e79db-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="e79db-141">Po wdrożeniu aplikacji będzie możliwe skonfigurowanie dziennika, edytując plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e79db-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="e79db-142">W przypadku aplikacji z systemem Windows jest nazwę tego pliku *applicationName*. exe.config i musi znajdować się w tym samym folderze co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="e79db-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="e79db-143">Dla aplikacji sieci Web jest skojarzony z projektem pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="e79db-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="e79db-144">Gdy aplikacja wykonuje kod, który tworzy wystąpienie klasy po raz pierwszy, sprawdza plik konfiguracji, aby uzyskać informacje o obiekcie.</span><span class="sxs-lookup"><span data-stu-id="e79db-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="e79db-145">Aby uzyskać `Log` obiektu, dzieje się po raz pierwszy `Log` dostępu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="e79db-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="e79db-146">System sprawdza, czy plik konfiguracyjny tylko raz dla każdego określonego obiektu — aplikacja tworzy obiekt po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="e79db-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="e79db-147">Dlatego może być konieczne ponowne uruchomienie aplikacji, aby zmiany zaczęły obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="e79db-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="e79db-148">We wdrożonej aplikacji włączysz kod śledzenia przez ponowne skonfigurowanie obiektami przełącznika, przed uruchomieniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e79db-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="e79db-149">Zazwyczaj ten proces obejmuje Włączanie obiektami przełącznika i wyłączyć lub zmieniając poziomy śledzenia, a następnie ponownie uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="e79db-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="e79db-150">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e79db-150">Security Considerations</span></span>

<span data-ttu-id="e79db-151">Podczas zapisywania danych w dzienniku, należy wziąć pod uwagę następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e79db-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="e79db-152">**Wyciekiem informacje o użytkowniku.**</span><span class="sxs-lookup"><span data-stu-id="e79db-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="e79db-153">Upewnij się, że zapisów aplikacji tylko zatwierdzone informacji w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="e79db-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="e79db-154">Na przykład może być możliwa do dziennika aplikacji, które ma zawierać nazwy użytkownika, ale nie hasło użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e79db-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="e79db-155">**Lokalizacje dziennika zapewnić bezpieczeństwo.**</span><span class="sxs-lookup"><span data-stu-id="e79db-155">**Make log locations secure.**</span></span> <span data-ttu-id="e79db-156">Żadnych dzienników, która zawiera potencjalnie poufne informacje powinny być przechowywane w bezpiecznej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e79db-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="e79db-157">**Należy unikać mylących informacji.**</span><span class="sxs-lookup"><span data-stu-id="e79db-157">**Avoid misleading information.**</span></span> <span data-ttu-id="e79db-158">Ogólnie rzecz biorąc aplikację należy zweryfikować wszystkie dane wprowadzane przez użytkownika przed rozpoczęciem korzystania z tych danych.</span><span class="sxs-lookup"><span data-stu-id="e79db-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="e79db-159">Obejmuje to zapisywanie danych w dzienniku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e79db-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="e79db-160">**Należy unikać "odmowa usługi".**</span><span class="sxs-lookup"><span data-stu-id="e79db-160">**Avoid denial of service.**</span></span> <span data-ttu-id="e79db-161">Jeśli aplikacja zapisuje zbyt dużej ilości informacji w dzienniku, jest wypełnienie dziennika lub ułatwić znajdowanie trudne do ważnych informacji.</span><span class="sxs-lookup"><span data-stu-id="e79db-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="e79db-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e79db-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="e79db-163">Rejestrowanie informacji z aplikacji</span><span class="sxs-lookup"><span data-stu-id="e79db-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
