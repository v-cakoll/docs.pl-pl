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
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="5d513-102">Praca z dziennikami aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d513-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="5d513-103">Obiekty `My.Application.Log` `My.Log` i ułatwiają zapisywanie rejestrowania i śledzenia informacji do dzienników.</span><span class="sxs-lookup"><span data-stu-id="5d513-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="5d513-104">Jak rejestrowane są wiadomości</span><span class="sxs-lookup"><span data-stu-id="5d513-104">How Messages are Logged</span></span>

<span data-ttu-id="5d513-105">Po pierwsze ważności wiadomości jest sprawdzany <xref:System.Diagnostics.TraceSource.Switch%2A> z właściwości log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5d513-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="5d513-106">Domyślnie tylko komunikaty o ważności "Informacje" i wyższe są przekazywane do odbiorników `TraceListener` śledzenia, określone w kolekcji dziennika.</span><span class="sxs-lookup"><span data-stu-id="5d513-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="5d513-107">Następnie każdy odbiornik porównuje ważność wiadomości do właściwości odbiornika. <xref:System.Diagnostics.TraceSource.Switch%2A></span><span class="sxs-lookup"><span data-stu-id="5d513-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="5d513-108">Jeśli ważność wiadomości jest wystarczająco wysoka, odbiornik zapisuje komunikat.</span><span class="sxs-lookup"><span data-stu-id="5d513-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="5d513-109">Na poniższym diagramie pokazano, `WriteEntry` jak komunikat napisany `WriteLine` do metody przechodzi do metod detektorów śledzenia dziennika:</span><span class="sxs-lookup"><span data-stu-id="5d513-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Diagram, który pokazuje moje wywołanie dziennika.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="5d513-111">Można zmienić zachowanie dziennika i odbiorników śledzenia, zmieniając plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d513-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="5d513-112">Na poniższym diagramie przedstawiono zgodność między częściami dziennika a plikiem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5d513-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Diagram przedstawiający konfigurację mojego dziennika.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="5d513-114">Gdzie rejestrowane są wiadomości</span><span class="sxs-lookup"><span data-stu-id="5d513-114">Where Messages are Logged</span></span>

<span data-ttu-id="5d513-115">Jeśli zestaw nie ma pliku `My.Application.Log` `My.Log` konfiguracji, i obiekty zapisu do danych <xref:System.Diagnostics.DefaultTraceListener> wyjściowych debugowania aplikacji (za pośrednictwem klasy).</span><span class="sxs-lookup"><span data-stu-id="5d513-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="5d513-116">Ponadto `My.Application.Log` obiekt zapisuje do pliku dziennika zestawu (za <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> pośrednictwem klasy), podczas gdy `My.Log` obiekt zapisuje do ASP.NET danych <xref:System.Web.WebPageTraceListener> wyjściowych strony sieci Web (za pośrednictwem klasy).</span><span class="sxs-lookup"><span data-stu-id="5d513-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="5d513-117">Dane wyjściowe debugowania można wyświetlić w oknie **dane wyjściowe** programu Visual Studio podczas uruchamiania aplikacji w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="5d513-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="5d513-118">Aby otworzyć okno **Dane wyjściowe,** kliknij element menu **Debugowanie,** wskaż polecenie **Windows**, a następnie kliknij pozycję **Wyjście**.</span><span class="sxs-lookup"><span data-stu-id="5d513-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="5d513-119">W oknie **Dane wyjściowe** wybierz **debugowanie** z pola **Pokaż dane wyjściowe.**</span><span class="sxs-lookup"><span data-stu-id="5d513-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="5d513-120">Domyślnie `My.Application.Log` zapisuje plik dziennika w ścieżce dla danych aplikacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d513-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="5d513-121">Ścieżkę można uzyskać <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> z właściwości <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5d513-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="5d513-122">Format tej ścieżki jest następujący:</span><span class="sxs-lookup"><span data-stu-id="5d513-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="5d513-123">Typowa wartość `BasePath` jest następująca.</span><span class="sxs-lookup"><span data-stu-id="5d513-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="5d513-124">C:\Dokumenty i\\`username`ustawienia \Dane aplikacji</span><span class="sxs-lookup"><span data-stu-id="5d513-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="5d513-125">Wartości , `CompanyName` `ProductName`i `ProductVersion` pochodzą z informacji o zestawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d513-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="5d513-126">Formą nazwy pliku dziennika jest *AssemblyName*.log, gdzie *Nazwa zestawu* jest nazwą pliku zestawu bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="5d513-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="5d513-127">Jeśli potrzebny jest więcej niż jeden plik dziennika, na przykład gdy oryginalny dziennik jest niedostępny, gdy aplikacja próbuje zapisać w dzienniku, formularz `Integer`dla nazwy pliku dziennika to *AssemblyName*-*iteration*.log, gdzie `iteration` jest dodatni .</span><span class="sxs-lookup"><span data-stu-id="5d513-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="5d513-128">Domyślne zachowanie można zastąpić, dodając lub zmieniając pliki konfiguracyjne komputera i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d513-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="5d513-129">Aby uzyskać więcej informacji, zobacz [Przewodnik: Zmiana miejsca, w którym my.application.log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="5d513-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="5d513-130">Konfigurowanie ustawień dziennika</span><span class="sxs-lookup"><span data-stu-id="5d513-130">Configuring Log Settings</span></span>

<span data-ttu-id="5d513-131">Obiekt `Log` ma domyślną implementację, która działa bez pliku konfiguracji aplikacji, app.config. Aby zmienić ustawienia domyślne, należy dodać plik konfiguracyjny z nowymi ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="5d513-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="5d513-132">Aby uzyskać więcej informacji, zobacz [Instruktaż: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="5d513-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="5d513-133">Sekcje konfiguracji dziennika znajdują `<system.diagnostics>` się w `<configuration>` węźle w głównym węźle pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="5d513-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="5d513-134">Informacje dziennika są zdefiniowane w kilku węzłach:</span><span class="sxs-lookup"><span data-stu-id="5d513-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="5d513-135">Detektory `Log` obiektu są zdefiniowane `<sources>` w węźle o nazwie DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="5d513-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="5d513-136">Filtr ważności `Log` obiektu jest zdefiniowany `<switches>` w węźle o nazwie DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="5d513-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="5d513-137">Odbiorniki dziennika są zdefiniowane w węźle. `<sharedListeners>`</span><span class="sxs-lookup"><span data-stu-id="5d513-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="5d513-138">Przykłady `<sources>`, `<switches>`i `<sharedListeners>` węzły są wyświetlane w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="5d513-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

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

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="5d513-139">Zmiana ustawień dziennika po wdrożeniu</span><span class="sxs-lookup"><span data-stu-id="5d513-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="5d513-140">Podczas tworzenia aplikacji jej ustawienia konfiguracji są przechowywane w pliku app.config, jak pokazano w powyższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="5d513-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="5d513-141">Po wdrożeniu aplikacji można skonfigurować dziennik, edytując plik konfiguracyjny.</span><span class="sxs-lookup"><span data-stu-id="5d513-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="5d513-142">W aplikacji opartej na systemie Windows nazwa tego pliku to *nazwa pliku .* exe.config i musi znajdować się w tym samym folderze co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="5d513-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="5d513-143">W przypadku aplikacji sieci Web jest to plik Web.config skojarzony z projektem.</span><span class="sxs-lookup"><span data-stu-id="5d513-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="5d513-144">Gdy aplikacja wykonuje kod, który tworzy wystąpienie klasy po raz pierwszy, sprawdza plik konfiguracji pod kątem informacji o obiekcie.</span><span class="sxs-lookup"><span data-stu-id="5d513-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="5d513-145">W `Log` przypadku obiektu dzieje się `Log` to przy pierwszym wejściu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="5d513-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="5d513-146">System sprawdza plik konfiguracyjny tylko raz dla dowolnego konkretnego obiektu — przy pierwszym uruchomieniu obiektu przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="5d513-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="5d513-147">W związku z tym może być konieczne ponowne uruchomienie aplikacji, aby zmiany zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="5d513-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="5d513-148">W wdrożonej aplikacji można włączyć kod śledzenia przez ponowne skonfigurowanie obiektów przełącznika przed uruchomieniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d513-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="5d513-149">Zazwyczaj wiąże się to z włączaniem i wyłączaniem obiektów przełącznika lub zmienianiem poziomów śledzenia, a następnie ponownym uruchomieniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d513-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="5d513-150">Zagadnienia związane z zabezpieczeniami</span><span class="sxs-lookup"><span data-stu-id="5d513-150">Security Considerations</span></span>

<span data-ttu-id="5d513-151">Podczas zapisywania danych w dzienniku należy wziąć pod uwagę następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="5d513-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="5d513-152">**Unikaj wycieku informacji o użytkowniku.**</span><span class="sxs-lookup"><span data-stu-id="5d513-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="5d513-153">Upewnij się, że aplikacja zapisuje tylko zatwierdzone informacje w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="5d513-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="5d513-154">Na przykład może być dopuszczalne dla dziennika aplikacji zawierają nazwy użytkowników, ale nie hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d513-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="5d513-155">**Zabezpiecz lokalizacje dzienników.**</span><span class="sxs-lookup"><span data-stu-id="5d513-155">**Make log locations secure.**</span></span> <span data-ttu-id="5d513-156">Każdy dziennik zawierający potencjalnie poufne informacje powinny być przechowywane w bezpiecznej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="5d513-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="5d513-157">**Unikaj wprowadzających w błąd informacji.**</span><span class="sxs-lookup"><span data-stu-id="5d513-157">**Avoid misleading information.**</span></span> <span data-ttu-id="5d513-158">Ogólnie rzecz biorąc aplikacja powinna sprawdzić poprawność wszystkich danych wprowadzonych przez użytkownika przed użyciem tych danych.</span><span class="sxs-lookup"><span data-stu-id="5d513-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="5d513-159">Obejmuje to zapisywanie danych w dzienniku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d513-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="5d513-160">**Unikaj odmowy usługi.**</span><span class="sxs-lookup"><span data-stu-id="5d513-160">**Avoid denial of service.**</span></span> <span data-ttu-id="5d513-161">Jeśli aplikacja zapisuje zbyt wiele informacji w dzienniku, może wypełnić dziennik lub utrudnić znalezienie ważnych informacji.</span><span class="sxs-lookup"><span data-stu-id="5d513-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d513-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d513-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="5d513-163">Rejestrowanie informacji z aplikacji</span><span class="sxs-lookup"><span data-stu-id="5d513-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
