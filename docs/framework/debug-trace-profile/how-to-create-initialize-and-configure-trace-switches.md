---
title: 'Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia'
description: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia przy użyciu klas System. Diagnostics. BooleanSwitch i system. Diagnostics. TraceSwitch w programie .NET.
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
ms.openlocfilehash: 6a43e143abba96c841f04b7be9d482c55e78aa8f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051327"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="50507-103">Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="50507-103">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="50507-104">Przełączniki śledzenia umożliwiają włączenie, wyłączenie i filtrowanie danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="50507-104">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="50507-105">Tworzenie i Inicjowanie przełącznika śledzenia</span><span class="sxs-lookup"><span data-stu-id="50507-105">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="50507-106">Aby można było używać przełączników śledzenia, należy najpierw je utworzyć i umieścić w kodzie.</span><span class="sxs-lookup"><span data-stu-id="50507-106">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="50507-107">Istnieją dwie wstępnie zdefiniowane klasy, z których można tworzyć obiekty przełącznika: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> klasy i <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="50507-107">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="50507-108">Należy użyć, <xref:System.Diagnostics.BooleanSwitch> Jeśli chcesz się dowiedzieć, czy jest wyświetlany komunikat śledzenia, <xref:System.Diagnostics.TraceSwitch> Jeśli chcesz rozróżnić poziomy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="50507-108">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="50507-109">W przypadku korzystania z programu <xref:System.Diagnostics.TraceSwitch> można definiować własne komunikaty debugowania i kojarzyć je z różnymi poziomami śledzenia.</span><span class="sxs-lookup"><span data-stu-id="50507-109">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="50507-110">Można użyć obu typów przełączników z funkcją śledzenia lub debugowania.</span><span class="sxs-lookup"><span data-stu-id="50507-110">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="50507-111">Domyślnie <xref:System.Diagnostics.BooleanSwitch> jest wyłączona i <xref:System.Diagnostics.TraceSwitch> jest ustawiona na poziom <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="50507-111">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="50507-112">Przełączniki śledzenia można tworzyć i umieszczać w dowolnej części kodu, który może z nich korzystać.</span><span class="sxs-lookup"><span data-stu-id="50507-112">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="50507-113">Chociaż można ustawić poziomy śledzenia i inne opcje konfiguracji w kodzie, zalecamy użycie pliku konfiguracji do zarządzania stanem przełączników.</span><span class="sxs-lookup"><span data-stu-id="50507-113">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="50507-114">Jest to spowodowane tym, że zarządzanie konfiguracją przełączników w systemie konfiguracji zapewnia większą elastyczność — można włączyć i wyłączyć różne przełączniki i zmienić poziomy bez konieczności ponownego kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50507-114">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="50507-115">Aby utworzyć i zainicjować przełącznik śledzenia</span><span class="sxs-lookup"><span data-stu-id="50507-115">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="50507-116">Zdefiniuj przełącznik jako typ <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> lub typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> , a następnie ustaw nazwę i opis przełącznika.</span><span class="sxs-lookup"><span data-stu-id="50507-116">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="50507-117">Skonfiguruj przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="50507-117">Configure your trace switch.</span></span> <span data-ttu-id="50507-118">Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](#configure).</span><span class="sxs-lookup"><span data-stu-id="50507-118">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="50507-119">Poniższy kod tworzy dwa przełączniki, jeden z każdego typu:</span><span class="sxs-lookup"><span data-stu-id="50507-119">The following code creates two switches, one of each type:</span></span>  
  
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
## <a name="configuring-trace-switches"></a><span data-ttu-id="50507-120">Konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="50507-120">Configuring trace switches</span></span>  
 <span data-ttu-id="50507-121">Po rozpoczęciu dystrybuowania aplikacji nadal można włączać lub wyłączać dane wyjściowe śledzenia przez skonfigurowanie przełączników śledzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50507-121">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="50507-122">Skonfigurowanie przełącznika oznacza zmianę jego wartości ze źródła zewnętrznego po jego zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="50507-122">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="50507-123">Można zmienić wartości obiektów przełącznika przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="50507-123">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="50507-124">Można skonfigurować przełącznik śledzenia, aby go włączyć i wyłączyć, lub ustawić jego poziom, określając wielkość i typ komunikatów przesyłanych wraz z odbiornikami.</span><span class="sxs-lookup"><span data-stu-id="50507-124">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="50507-125">Przełączniki są konfigurowane przy użyciu pliku. config.</span><span class="sxs-lookup"><span data-stu-id="50507-125">Your switches are configured using the .config file.</span></span> <span data-ttu-id="50507-126">W przypadku aplikacji sieci Web jest to plik Web.config skojarzony z projektem.</span><span class="sxs-lookup"><span data-stu-id="50507-126">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="50507-127">W aplikacji systemu Windows ten plik ma nazwę (nazwa aplikacji) .exe.config. W wdrożonej aplikacji ten plik musi znajdować się w tym samym folderze co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="50507-127">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="50507-128">Gdy aplikacja wykonuje kod, który tworzy wystąpienie przełącznika po raz pierwszy, sprawdza plik konfiguracji dla informacji na poziomie śledzenia o nazwanym przełączniku.</span><span class="sxs-lookup"><span data-stu-id="50507-128">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="50507-129">System śledzenia analizuje plik konfiguracji tylko raz dla każdego określonego przełącznika — podczas pierwszego tworzenia przełącznika przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="50507-129">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="50507-130">W wdrożonej aplikacji należy włączyć kod śledzenia przez ponowne skonfigurowanie obiektów Switch, gdy aplikacja nie jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="50507-130">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="50507-131">Zazwyczaj obejmuje to włączenie i wyłączenie obiektów przełącznika lub zmianę poziomów śledzenia, a następnie ponowne uruchomienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50507-131">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="50507-132">Podczas tworzenia wystąpienia przełącznika, można go również zainicjować przez określenie dwóch argumentów: argumentu *DisplayName* i argumentu *Description* .</span><span class="sxs-lookup"><span data-stu-id="50507-132">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="50507-133">Argument *DisplayName* konstruktora ustawia <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> Właściwość <xref:System.Diagnostics.Switch> wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="50507-133">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="50507-134">*DisplayName* jest nazwą, która jest używana do konfigurowania przełącznika w pliku. config, a argument *Description* powinien zwrócić krótki opis przełącznika i komunikaty, które kontroluje.</span><span class="sxs-lookup"><span data-stu-id="50507-134">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="50507-135">Oprócz określenia nazwy przełącznika do skonfigurowania należy również określić wartość dla przełącznika.</span><span class="sxs-lookup"><span data-stu-id="50507-135">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="50507-136">Ta wartość jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="50507-136">This value is an Integer.</span></span> <span data-ttu-id="50507-137">Dla <xref:System.Diagnostics.BooleanSwitch> , wartość 0 odpowiada **off**, a każda wartość różna od zera odpowiada wartości **on**.</span><span class="sxs-lookup"><span data-stu-id="50507-137">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="50507-138">Dla <xref:System.Diagnostics.TraceSwitch> , 0, 1, 2, 3 i 4 odpowiadają **Off**odpowiednio wartościom, **błędom**, **ostrzeżeniem**, **informacjom**i **pełnym**.</span><span class="sxs-lookup"><span data-stu-id="50507-138">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="50507-139">Każda liczba większa niż 4 jest traktowana jako **pełna**, a każda liczba mniejsza od zera jest traktowana jako **wyłączona**.</span><span class="sxs-lookup"><span data-stu-id="50507-139">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50507-140">W .NET Framework w wersji 2,0 można użyć tekstu, aby określić wartość dla przełącznika.</span><span class="sxs-lookup"><span data-stu-id="50507-140">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="50507-141">Na przykład `true` dla <xref:System.Diagnostics.BooleanSwitch> lub tekst reprezentujący wartość wyliczenia, `Error` na przykład dla elementu <xref:System.Diagnostics.TraceSwitch> .</span><span class="sxs-lookup"><span data-stu-id="50507-141">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="50507-142">Wiersz `<add name="myTraceSwitch" value="Error" />` jest odpowiednikiem `<add name="myTraceSwitch" value="1" />` .</span><span class="sxs-lookup"><span data-stu-id="50507-142">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="50507-143">Aby użytkownicy końcowi mogli konfigurować przełączniki śledzenia aplikacji, należy dostarczyć szczegółowej dokumentacji dotyczącej przełączników w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50507-143">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="50507-144">Należy szczegółowo określić, które przełączniki kontrolują sposób i sposób włączania i wyłączania.</span><span class="sxs-lookup"><span data-stu-id="50507-144">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="50507-145">Należy również udostępnić użytkownikowi końcowemu plik. config, który ma odpowiednią pomoc w komentarzach.</span><span class="sxs-lookup"><span data-stu-id="50507-145">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="50507-146">Aby skonfigurować przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="50507-146">To configure trace switches</span></span>  
  
1. <span data-ttu-id="50507-147">Aby można było korzystać z przełączników śledzenia, najpierw należy je utworzyć i umieścić w kodzie zgodnie z opisem w sekcji [Tworzenie i Inicjowanie przełącznika śledzenia](#create).</span><span class="sxs-lookup"><span data-stu-id="50507-147">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="50507-148">Jeśli projekt nie zawiera pliku konfiguracji (app.config lub Web.config), w menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="50507-148">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="50507-149">**Visual Basic:** W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="50507-149">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="50507-150">Plik konfiguracji aplikacji zostanie utworzony i otwarty.</span><span class="sxs-lookup"><span data-stu-id="50507-150">The application configuration file is created and opened.</span></span> <span data-ttu-id="50507-151">Jest to dokument XML, którego element główny to`<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="50507-151">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="50507-152">**Visual C#:** W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik XML**.</span><span class="sxs-lookup"><span data-stu-id="50507-152">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="50507-153">Nazwij ten plik **app.config**. W edytorze XML, po deklaracji XML, Dodaj następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="50507-153">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="50507-154">Po skompilowaniu projektu plik app.config jest kopiowany do folderu wyjściowego projektu i ma nazwę *applicationname*.exe.config.</span><span class="sxs-lookup"><span data-stu-id="50507-154">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="50507-155">Po `<configuration>` tagu, ale przed `</configuration>` tagiem, Dodaj odpowiedni kod XML, aby skonfigurować przełączniki.</span><span class="sxs-lookup"><span data-stu-id="50507-155">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="50507-156">W poniższych przykładach przedstawiono **BooleanSwitch** z właściwością **DisplayName** `DataMessageSwitch` i **TraceSwitch** z właściwością **DisplayName** `TraceLevelSwitch` .</span><span class="sxs-lookup"><span data-stu-id="50507-156">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="50507-157">W tej konfiguracji oba przełączniki są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="50507-157">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="50507-158">Jeśli musisz włączyć **BooleanSwitch**, jak `DataMessagesSwitch` pokazano w poprzednim przykładzie, Zmień **wartość** na dowolną liczbę całkowitą inną niż 0.</span><span class="sxs-lookup"><span data-stu-id="50507-158">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="50507-159">Jeśli musisz włączyć **TraceSwitch**, jak `TraceLevelSwitch` pokazano w poprzednim przykładzie, Zmień **wartość** na odpowiednie ustawienie na poziomie (od 1 do 4).</span><span class="sxs-lookup"><span data-stu-id="50507-159">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="50507-160">Dodaj komentarze do pliku config, aby użytkownik końcowy miał jasno zrozumieć, jakie wartości należy zmienić, aby odpowiednio skonfigurować przełączniki.</span><span class="sxs-lookup"><span data-stu-id="50507-160">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="50507-161">Poniższy przykład pokazuje, jak kod końcowy, w tym komentarze, może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="50507-161">The following example shows how the final code, including comments, might look:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="50507-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50507-162">See also</span></span>

- [<span data-ttu-id="50507-163">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="50507-163">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="50507-164">Porady: dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="50507-164">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="50507-165">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="50507-165">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="50507-166">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="50507-166">Trace and Debug Settings Schema</span></span>](../configure-apps/file-schema/trace-debug/index.md)
