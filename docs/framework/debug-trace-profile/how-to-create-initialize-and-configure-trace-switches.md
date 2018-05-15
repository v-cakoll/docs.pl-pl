---
title: 'Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4088c74d0ea8e9f2ad70aff37d99870d34b168ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="fe13e-102">Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="fe13e-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="fe13e-103">Przełączniki śledzenia umożliwiają włączać, wyłączać i Filtruj dane wyjściowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fe13e-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="fe13e-104">Tworzenie i Inicjowanie przełącznika śledzenia</span><span class="sxs-lookup"><span data-stu-id="fe13e-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="fe13e-105">Aby można było używać przełączników śledzenia, najpierw musisz je utworzyć i umieść je w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fe13e-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="fe13e-106">Istnieją dwie klasy wstępnie zdefiniowane, z których można utworzyć obiektów przełącznika: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> klasy i <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="fe13e-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fe13e-107">Należy użyć <xref:System.Diagnostics.BooleanSwitch> Jeśli interesujących Cię tylko czy pojawi się komunikat śledzenia; użyj <xref:System.Diagnostics.TraceSwitch> Aby rozróżnić poziomy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fe13e-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="fe13e-108">Jeśli używasz <xref:System.Diagnostics.TraceSwitch>, można zdefiniować debugowania wiadomości i skojarzyć je z poziomów śledzenia różne.</span><span class="sxs-lookup"><span data-stu-id="fe13e-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="fe13e-109">Można używać obu typów przełączników z śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="fe13e-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="fe13e-110">Domyślnie <xref:System.Diagnostics.BooleanSwitch> jest wyłączona i <xref:System.Diagnostics.TraceSwitch> jest ustawiony poziom <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe13e-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fe13e-111">Przełączniki śledzenia można tworzyć i umieszczane w dowolnej części swój kod, który może używać ich.</span><span class="sxs-lookup"><span data-stu-id="fe13e-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="fe13e-112">Mimo że można ustawić poziomy śledzenia i inne opcje konfiguracji w kodzie, zalecane jest użycie pliku konfiguracji do zarządzania stanem przełączników.</span><span class="sxs-lookup"><span data-stu-id="fe13e-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="fe13e-113">Jest to spowodowane zarządzania konfiguracją przełączników w systemie konfiguracji zapewnia większą elastyczność — można włączać i wyłączać różnych przełączników i zmienianie poziomów bez konieczności ponownego kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe13e-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="fe13e-114">Aby utworzyć i zainicjować przełącznika śledzenia</span><span class="sxs-lookup"><span data-stu-id="fe13e-114">To create and initialize a trace switch</span></span>  
  
1.  <span data-ttu-id="fe13e-115">Zdefiniuj przełącznikiem jako dowolnego typu <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> lub typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> i ustaw nazwę i opis przełącznika.</span><span class="sxs-lookup"><span data-stu-id="fe13e-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2.  <span data-ttu-id="fe13e-116">Skonfiguruj przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fe13e-116">Configure your trace switch.</span></span> <span data-ttu-id="fe13e-117">Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](#configure).</span><span class="sxs-lookup"><span data-stu-id="fe13e-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="fe13e-118">Poniższy kod tworzy dwa przełączniki, jeden z każdego typu.</span><span class="sxs-lookup"><span data-stu-id="fe13e-118">The following code creates two switches, one of each type:</span></span>  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =   
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =   
       new System.Diagnostics.TraceSwitch("General",   
       "Entire application");  
    ```  
  
<a name="configure"></a>   
## <a name="configuring-trace-switches"></a><span data-ttu-id="fe13e-119">Konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="fe13e-119">Configuring trace switches</span></span>  
 <span data-ttu-id="fe13e-120">Po aplikacji został rozesłany, nadal można włączyć lub wyłączyć dane wyjściowe śledzenia przez skonfigurowanie przełączników śledzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe13e-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="fe13e-121">Konfigurowanie przełącznikiem oznacza, że zmiany jego wartość z zewnętrznego źródła po została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="fe13e-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="fe13e-122">Można zmienić wartości obiektu przełącznika, przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fe13e-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="fe13e-123">Skonfiguruj przełącznika śledzenia, aby ją włączyć lub wyłączyć, lub jego poziom określania wielkości i typ wiadomości przekazuje do odbiorników.</span><span class="sxs-lookup"><span data-stu-id="fe13e-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="fe13e-124">Przełączniki są skonfigurowane przy użyciu pliku Config.</span><span class="sxs-lookup"><span data-stu-id="fe13e-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="fe13e-125">Dla aplikacji sieci Web jest to plik Web.config skojarzony z projektem.</span><span class="sxs-lookup"><span data-stu-id="fe13e-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="fe13e-126">W aplikacji systemu Windows, ten plik ma nazwę (nazwa aplikacji). exe.config. We wdrożonej aplikacji ten plik musi znajdować się w tym samym folderze co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="fe13e-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="fe13e-127">Podczas aplikacji kod, który tworzy wystąpienie przełącznika po raz pierwszy, sprawdza plik konfiguracji poziom śledzenia informacji o nazwanych przełącznika.</span><span class="sxs-lookup"><span data-stu-id="fe13e-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="fe13e-128">Śledzenie system sprawdza pliku konfiguracji tylko raz dla dowolnego określonego przełącznika — aplikacja tworzy przełącznika po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="fe13e-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="fe13e-129">We wdrożonej aplikacji możesz włączyć kod śledzenia za ponownej konfiguracji przełącznika obiektów, kiedy aplikacja nie jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="fe13e-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="fe13e-130">Zazwyczaj wiąże się to Włączanie obiektami przełącznika i wyłączyć lub zmieniając poziomy śledzenia, a następnie ponowne uruchomienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe13e-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="fe13e-131">Podczas tworzenia wystąpienia przełącznika można również zainicjować go przez określenie dwa argumenty: *displayName* argumentu i *opis* argumentu.</span><span class="sxs-lookup"><span data-stu-id="fe13e-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="fe13e-132">*DisplayName* argument zestawów konstruktora <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> właściwość <xref:System.Diagnostics.Switch> wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="fe13e-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="fe13e-133">*DisplayName* to nazwa, która jest używana do konfigurowania przełącznika w pliku .config i *opis* argument powinien zwrócić krótki opis przełączników i jakie komunikaty kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fe13e-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="fe13e-134">Oprócz określenia nazwy przełącznika można skonfigurować, należy określić wartość dla tego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="fe13e-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="fe13e-135">Ta wartość jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="fe13e-135">This value is an Integer.</span></span> <span data-ttu-id="fe13e-136">Dla <xref:System.Diagnostics.BooleanSwitch>, wartość 0 odpowiada **poza**, i odpowiada dowolną wartość niezerową **na**.</span><span class="sxs-lookup"><span data-stu-id="fe13e-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="fe13e-137">Dla <xref:System.Diagnostics.TraceSwitch>0,1,2,3 i 4 odpowiada **poza**, **błąd**, **ostrzeżenie**, **informacji**, i **pełne**odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="fe13e-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="fe13e-138">Wszystkie liczby większe niż 4 jest traktowany jako **pełne**oraz numer mniej niż zero jest traktowany jako **poza**.</span><span class="sxs-lookup"><span data-stu-id="fe13e-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe13e-139">W programie .NET Framework w wersji 2.0 tekst można użyć do określenia wartości dla przełącznika.</span><span class="sxs-lookup"><span data-stu-id="fe13e-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="fe13e-140">Na przykład `true` dla <xref:System.Diagnostics.BooleanSwitch> lub tekst reprezentujący wartości wyliczenia, takich jak `Error` dla <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="fe13e-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="fe13e-141">Wiersz `<add name="myTraceSwitch" value="Error" />` jest odpowiednikiem `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="fe13e-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="fe13e-142">Aby użytkownicy końcowi mogli Konfigurowanie przełączników śledzenia aplikacji musisz podać szczegółowa dokumentacja na temat parametrów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe13e-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="fe13e-143">Należy szczegółowo, które przełączniki kontroli co oraz jak je włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="fe13e-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="fe13e-144">Należy również podać użytkownikowi końcowemu z pliku .config, który ma odpowiednie pomocy w komentarzach.</span><span class="sxs-lookup"><span data-stu-id="fe13e-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="fe13e-145">Aby skonfigurować przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="fe13e-145">To configure trace switches</span></span>  
  
1.  <span data-ttu-id="fe13e-146">Aby można było używać przełączników śledzenia, najpierw musisz je utworzyć i umieść je w kodzie, zgodnie z opisem w sekcji [tworzenie i Inicjowanie przełącznika śledzenia](#create).</span><span class="sxs-lookup"><span data-stu-id="fe13e-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2.  <span data-ttu-id="fe13e-147">Jeśli projekt zawiera plik konfiguracji (app.config lub Web.config), następnie z **projektu** menu, wybierz opcję **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="fe13e-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    -   <span data-ttu-id="fe13e-148">**Visual Basic:** w **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="fe13e-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="fe13e-149">Plik konfiguracji aplikacji jest utworzony i otwarty.</span><span class="sxs-lookup"><span data-stu-id="fe13e-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="fe13e-150">To jest dokument XML, którego element główny jest `<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="fe13e-150">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    -   <span data-ttu-id="fe13e-151">**Visual C#:** w **Dodaj nowy element** oknie dialogowym wybierz **pliku XML**.</span><span class="sxs-lookup"><span data-stu-id="fe13e-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="fe13e-152">Nazwij ten plik **app.config**. W edytorze XML po deklaracji XML, Dodaj następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="fe13e-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="fe13e-153">Podczas kompilowania projektu pliku app.config jest kopiowany do folderu wyjściowego projektu i zostanie zmieniona nazwa *applicationname*. exe.config.</span><span class="sxs-lookup"><span data-stu-id="fe13e-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3.  <span data-ttu-id="fe13e-154">Po `<configuration>` tagów, ale przed wysłaniem `</configuration>` tagów, Dodaj odpowiednie XML do skonfigurowania przełączników.</span><span class="sxs-lookup"><span data-stu-id="fe13e-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="fe13e-155">W poniższych przykładach pokazano **BooleanSwitch** z **DisplayName** właściwość `DataMessageSwitch` i **TraceSwitch** z **Nazwa wyświetlana**  właściwość `TraceLevelSwitch`.</span><span class="sxs-lookup"><span data-stu-id="fe13e-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="fe13e-156">W tej konfiguracji obu przełączniki są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="fe13e-156">In this configuration, both switches are off.</span></span>  
  
4.  <span data-ttu-id="fe13e-157">Jeśli konieczne jest włączenie **BooleanSwitch**, takich jak `DataMessagesSwitch` pokazano w poprzednim przykładzie, zmień **wartość** do dowolnej liczby całkowitej niż 0.</span><span class="sxs-lookup"><span data-stu-id="fe13e-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5.  <span data-ttu-id="fe13e-158">Jeśli konieczne jest włączenie **TraceSwitch**, takich jak `TraceLevelSwitch` pokazano w poprzednim przykładzie, zmień **wartość** odpowiednich ustawień poziomu (od 1 do 4).</span><span class="sxs-lookup"><span data-stu-id="fe13e-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6.  <span data-ttu-id="fe13e-159">Dodawanie komentarzy do pliku .config, aby użytkownik końcowy miał przejrzysty jakie wartości, aby zmienić odpowiednio skonfigurować przełączników.</span><span class="sxs-lookup"><span data-stu-id="fe13e-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="fe13e-160">W poniższym przykładzie pokazano, jak może wyglądać końcowego kodu, w tym komentarzy:</span><span class="sxs-lookup"><span data-stu-id="fe13e-160">The following example shows how the final code, including comments, might look:</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fe13e-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe13e-161">See Also</span></span>  
 [<span data-ttu-id="fe13e-162">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="fe13e-162">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="fe13e-163">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="fe13e-163">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="fe13e-164">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="fe13e-164">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="fe13e-165">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="fe13e-165">Trace and Debug Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
