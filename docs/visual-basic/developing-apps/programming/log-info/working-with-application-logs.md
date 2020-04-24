---
title: Praca z dziennikami aplikacji
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 617b940d2cf15779ae3c10e4663b63c9771d44b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345899"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="18f80-102">Praca z dziennikami aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18f80-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="18f80-103">Obiekty `My.Application.Log` i `My.Log` ułatwiają zapisywanie informacji o rejestrowaniu i śledzeniu w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="18f80-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="18f80-104">Jak są rejestrowane komunikaty</span><span class="sxs-lookup"><span data-stu-id="18f80-104">How Messages are Logged</span></span>

<span data-ttu-id="18f80-105">Po pierwsze ważność komunikatu jest sprawdzana z <xref:System.Diagnostics.TraceSource.Switch%2A> właściwością <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> właściwości log.</span><span class="sxs-lookup"><span data-stu-id="18f80-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="18f80-106">Domyślnie tylko wiadomości o ważności "Information" i wyższych są przesyłane do odbiorników śledzenia określonych w `TraceListener` kolekcji dzienników.</span><span class="sxs-lookup"><span data-stu-id="18f80-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="18f80-107">Następnie każdy odbiornik porównuje ważność komunikatu z <xref:System.Diagnostics.TraceSource.Switch%2A> właściwością odbiornika.</span><span class="sxs-lookup"><span data-stu-id="18f80-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="18f80-108">Jeśli ważność komunikatu jest wystarczająco wysoka, odbiornik zapisuje komunikat.</span><span class="sxs-lookup"><span data-stu-id="18f80-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="18f80-109">Na poniższym diagramie przedstawiono sposób, w jaki komunikat zapisany `WriteEntry` w metodzie jest przesyłany do `WriteLine` metod detektorów śledzenia dziennika:</span><span class="sxs-lookup"><span data-stu-id="18f80-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Diagram przedstawiający moje wywołanie dziennika.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="18f80-111">Można zmienić zachowanie dziennika i detektorów śledzenia, zmieniając plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18f80-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="18f80-112">Na poniższym diagramie przedstawiono zgodność między częściami dziennika i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="18f80-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Diagram przedstawiający moją konfigurację dziennika.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="18f80-114">Gdzie są rejestrowane komunikaty</span><span class="sxs-lookup"><span data-stu-id="18f80-114">Where Messages are Logged</span></span>

<span data-ttu-id="18f80-115">Jeśli zestaw nie ma pliku konfiguracji, `My.Application.Log` a obiekty i `My.Log` zapisują w danych wyjściowych debugowania aplikacji (za pomocą <xref:System.Diagnostics.DefaultTraceListener> klasy).</span><span class="sxs-lookup"><span data-stu-id="18f80-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="18f80-116">Ponadto `My.Application.Log` obiekt zapisuje w pliku dziennika zestawu (za pomocą <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy), podczas gdy `My.Log` obiekt zapisuje do danych wyjściowych strony sieci Web ASP.NET (za pomocą <xref:System.Web.WebPageTraceListener> klasy).</span><span class="sxs-lookup"><span data-stu-id="18f80-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="18f80-117">Dane wyjściowe debugowania można wyświetlić w oknie **danych wyjściowych** programu Visual Studio podczas uruchamiania aplikacji w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="18f80-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="18f80-118">Aby otworzyć okno **dane wyjściowe** , kliknij element menu **Debuguj** , wskaż polecenie **Windows**, a następnie kliknij pozycję **dane wyjściowe**.</span><span class="sxs-lookup"><span data-stu-id="18f80-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="18f80-119">W oknie **dane wyjściowe** wybierz pozycję **Debuguj** w polu **Pokaż dane wyjściowe z** .</span><span class="sxs-lookup"><span data-stu-id="18f80-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="18f80-120">Domyślnie program `My.Application.Log` zapisuje plik dziennika w ścieżce dla danych aplikacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="18f80-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="18f80-121">Ścieżkę można pobrać z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> właściwości <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> obiektu.</span><span class="sxs-lookup"><span data-stu-id="18f80-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="18f80-122">Format tej ścieżki jest następujący:</span><span class="sxs-lookup"><span data-stu-id="18f80-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="18f80-123">Typowa wartość dla `BasePath` jest następująca.</span><span class="sxs-lookup"><span data-stu-id="18f80-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="18f80-124">C:\Dokumenty i ustawienia\\`username`\Dane danych</span><span class="sxs-lookup"><span data-stu-id="18f80-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="18f80-125">Wartości `CompanyName`, `ProductName`i `ProductVersion` pochodzą z informacji o zestawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18f80-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="18f80-126">Nazwa pliku dziennika to *AssemblyName*. log, gdzie *AssemblyName* jest nazwą pliku zestawu bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="18f80-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="18f80-127">Jeśli jest wymagany więcej niż jeden plik dziennika, na przykład gdy oryginalny dziennik jest niedostępny, gdy aplikacja próbuje zapisać w dzienniku, formularz dla nazwy pliku dziennika to *AssemblyName*-*iteracji*. log, gdzie `iteration` jest wartością dodatnią. `Integer`</span><span class="sxs-lookup"><span data-stu-id="18f80-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="18f80-128">Zachowanie domyślne można zastąpić przez dodanie lub zmianę plików konfiguracyjnych komputera i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18f80-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="18f80-129">Aby uzyskać więcej informacji, zobacz [Przewodnik: Zmienianie, gdzie my. Application. Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="18f80-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="18f80-130">Konfigurowanie ustawień dziennika</span><span class="sxs-lookup"><span data-stu-id="18f80-130">Configuring Log Settings</span></span>

<span data-ttu-id="18f80-131">`Log` Obiekt ma domyślną implementację, która działa bez pliku konfiguracji aplikacji App. config. Aby zmienić wartości domyślne, należy dodać plik konfiguracji z nowymi ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="18f80-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="18f80-132">Aby uzyskać więcej informacji, zobacz [Przewodnik: filtrowanie danych wyjściowych my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="18f80-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="18f80-133">Sekcje konfiguracji dziennika znajdują się w `<system.diagnostics>` węźle głównym `<configuration>` pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="18f80-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="18f80-134">Informacje dziennika są zdefiniowane w kilku węzłach:</span><span class="sxs-lookup"><span data-stu-id="18f80-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="18f80-135">Detektory dla `Log` obiektu są zdefiniowane w `<sources>` węźle o nazwie DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="18f80-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="18f80-136">Filtr ważności dla `Log` obiektu jest zdefiniowany w `<switches>` węźle o nazwie DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="18f80-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="18f80-137">Odbiorniki dzienników są zdefiniowane w `<sharedListeners>` węźle.</span><span class="sxs-lookup"><span data-stu-id="18f80-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="18f80-138">Przykłady `<sources>`, `<switches>`i `<sharedListeners>` węzłów są pokazane w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="18f80-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

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

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="18f80-139">Zmiana ustawień dziennika po wdrożeniu</span><span class="sxs-lookup"><span data-stu-id="18f80-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="18f80-140">Podczas tworzenia aplikacji jego ustawienia konfiguracji są przechowywane w pliku App. config, jak pokazano w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="18f80-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="18f80-141">Po wdrożeniu aplikacji można nadal skonfigurować dziennik, edytując plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="18f80-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="18f80-142">W aplikacji opartej na systemie Windows nazwa tego pliku to *ApplicationName*. exe. config i musi znajdować się w tym samym folderze co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="18f80-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="18f80-143">W przypadku aplikacji sieci Web jest to plik Web. config skojarzony z projektem.</span><span class="sxs-lookup"><span data-stu-id="18f80-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="18f80-144">Gdy aplikacja wykonuje kod, który tworzy wystąpienie klasy po raz pierwszy, sprawdza plik konfiguracji w celu uzyskania informacji na temat obiektu.</span><span class="sxs-lookup"><span data-stu-id="18f80-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="18f80-145">Dla `Log` obiektu, dzieje się to podczas pierwszego uzyskiwania dostępu `Log` do obiektu.</span><span class="sxs-lookup"><span data-stu-id="18f80-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="18f80-146">System analizuje plik konfiguracyjny tylko raz dla każdego określonego obiektu — podczas pierwszego tworzenia obiektu przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="18f80-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="18f80-147">W związku z tym może być konieczne ponowne uruchomienie aplikacji, aby zmiany zaczęły obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="18f80-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="18f80-148">W wdrożonej aplikacji należy włączyć kod śledzenia przez ponowne skonfigurowanie obiektów Switch przed uruchomieniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18f80-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="18f80-149">Zazwyczaj obejmuje to włączenie i wyłączenie obiektów przełącznika lub zmianę poziomów śledzenia, a następnie ponowne uruchomienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18f80-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="18f80-150">Zagadnienia związane z zabezpieczeniami</span><span class="sxs-lookup"><span data-stu-id="18f80-150">Security Considerations</span></span>

<span data-ttu-id="18f80-151">Podczas zapisywania danych do dziennika należy wziąć pod uwagę następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="18f80-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="18f80-152">**Unikaj przecieku informacji o użytkownikach.**</span><span class="sxs-lookup"><span data-stu-id="18f80-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="18f80-153">Upewnij się, że aplikacja zapisuje tylko zatwierdzone informacje w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="18f80-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="18f80-154">Na przykład może być to możliwe, aby dziennik aplikacji zawierał nazwy użytkowników, ale nie hasła użytkowników.</span><span class="sxs-lookup"><span data-stu-id="18f80-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="18f80-155">**Ustaw lokalizacje dzienników jako bezpieczne.**</span><span class="sxs-lookup"><span data-stu-id="18f80-155">**Make log locations secure.**</span></span> <span data-ttu-id="18f80-156">Wszystkie dzienniki zawierające potencjalnie poufne informacje powinny być przechowywane w bezpiecznej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="18f80-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="18f80-157">**Unikaj mylących informacji.**</span><span class="sxs-lookup"><span data-stu-id="18f80-157">**Avoid misleading information.**</span></span> <span data-ttu-id="18f80-158">Ogólnie rzecz biorąc, aplikacja powinna sprawdzać poprawność wszystkich danych wprowadzonych przez użytkownika przed użyciem tych danych.</span><span class="sxs-lookup"><span data-stu-id="18f80-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="18f80-159">Obejmuje to zapisywanie danych w dzienniku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18f80-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="18f80-160">**Unikaj odmowy usługi.**</span><span class="sxs-lookup"><span data-stu-id="18f80-160">**Avoid denial of service.**</span></span> <span data-ttu-id="18f80-161">Jeśli aplikacja zapisuje zbyt dużo informacji w dzienniku, może wypełnić dziennik lub utrudnić znalezienie ważnych informacji.</span><span class="sxs-lookup"><span data-stu-id="18f80-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="18f80-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18f80-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="18f80-163">Rejestrowanie informacji z aplikacji</span><span class="sxs-lookup"><span data-stu-id="18f80-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
