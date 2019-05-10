---
title: 'Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia'
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
ms.openlocfilehash: 5c947dcd3fa3a71d5bbfdf742b106bf56d8444fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596745"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="41796-102">Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="41796-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="41796-103">Przełączniki śledzenia umożliwiają włączać, wyłączać i filtrować dane wyjściowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="41796-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="41796-104">Tworzenie i Inicjowanie przełącznikiem śledzenia</span><span class="sxs-lookup"><span data-stu-id="41796-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="41796-105">Aby można było używać przełączników śledzenia, należy najpierw utworzyć je i umieścić je w kodzie.</span><span class="sxs-lookup"><span data-stu-id="41796-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="41796-106">Istnieją dwie klasy wstępnie zdefiniowanych, z których możesz tworzyć obiekty przełącznika: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> klasy i <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="41796-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="41796-107">Należy użyć <xref:System.Diagnostics.BooleanSwitch> interesujące Cię tylko czy pojawi się komunikat śledzenia; należy użyć <xref:System.Diagnostics.TraceSwitch> Aby rozróżnić poziomy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="41796-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="41796-108">Jeśli używasz <xref:System.Diagnostics.TraceSwitch>, można zdefiniować własne komunikatów debugowania i skojarzyć je z różnymi poziomami śledzenia.</span><span class="sxs-lookup"><span data-stu-id="41796-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="41796-109">Można użyć obu rodzajów przełączników przy użyciu śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="41796-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="41796-110">Domyślnie <xref:System.Diagnostics.BooleanSwitch> jest wyłączona i <xref:System.Diagnostics.TraceSwitch> jest ustawiona na poziomie <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41796-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41796-111">Przełączniki śledzenia można tworzyć i umieszczane w dowolnej części swój kod, który może ich używać.</span><span class="sxs-lookup"><span data-stu-id="41796-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="41796-112">Mimo że w kodzie, można ustawić poziomu śledzenia i inne opcje konfiguracji, zaleca się użyć pliku konfiguracji do zarządzania stanem przełączników.</span><span class="sxs-lookup"><span data-stu-id="41796-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="41796-113">Jest to spowodowane zarządzania konfiguracją przełączników w systemie konfiguracji zapewnia większą elastyczność — można włączać i wyłączać różnych przełączników i zmieniać poziomy bez konieczności ponownego kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41796-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="41796-114">Aby utworzyć i zainicjować przełącznikiem śledzenia</span><span class="sxs-lookup"><span data-stu-id="41796-114">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="41796-115">Przełącznik jest definiowana jako dowolnego typu <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> lub typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> i ustaw nazwę i opis przełącznika.</span><span class="sxs-lookup"><span data-stu-id="41796-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="41796-116">Skonfiguruj na przełączniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="41796-116">Configure your trace switch.</span></span> <span data-ttu-id="41796-117">Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](#configure).</span><span class="sxs-lookup"><span data-stu-id="41796-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="41796-118">Poniższy kod tworzy dwa przełączniki, jeden dla każdego typu.</span><span class="sxs-lookup"><span data-stu-id="41796-118">The following code creates two switches, one of each type:</span></span>  
  
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
## <a name="configuring-trace-switches"></a><span data-ttu-id="41796-119">Konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="41796-119">Configuring trace switches</span></span>  
 <span data-ttu-id="41796-120">Po aplikacji został rozesłany, nadal można włączyć lub wyłączyć dane wyjściowe śledzenia przez skonfigurowanie przełączników śledzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41796-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="41796-121">Konfigurowanie przełącznika oznacza, zmieniając jego wartość z zewnętrznego źródła, po jego zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="41796-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="41796-122">Można zmienić wartości obiektów przełącznika, przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="41796-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="41796-123">Skonfiguruj przełącznikiem śledzenia, aby go włączyć i wyłączyć lub ustawić jego poziom Określanie wielkość i typ wiadomości przekazywane wraz z do odbiorników.</span><span class="sxs-lookup"><span data-stu-id="41796-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="41796-124">Przełączniki są skonfigurowane przy użyciu pliku Config.</span><span class="sxs-lookup"><span data-stu-id="41796-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="41796-125">Dla aplikacji sieci Web jest skojarzony z projektem pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="41796-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="41796-126">W aplikacji Windows, ten plik ma nazwę (nazwa aplikacji). exe.config. We wdrożonej aplikacji ten plik musi znajdować się w tym samym folderze co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="41796-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="41796-127">Gdy aplikacja wykonuje kod, który tworzy wystąpienie przełącznika po raz pierwszy, sprawdza plik konfiguracyjny dla poziomu śledzenia informacji o przełącznikiem o nazwie.</span><span class="sxs-lookup"><span data-stu-id="41796-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="41796-128">System śledzenia sprawdza plik konfiguracyjny tylko raz dla dowolnego określonego przełącznika — aplikacja tworzy przełącznik po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="41796-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="41796-129">Ponowne skonfigurowanie obiektami przełącznika, gdy aplikacja nie jest uruchomiona, we wdrożonej aplikacji włączyć kod śledzenia.</span><span class="sxs-lookup"><span data-stu-id="41796-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="41796-130">Zazwyczaj ten proces obejmuje Włączanie obiektami przełącznika i wyłączyć lub zmieniając poziomy śledzenia, a następnie ponownie uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="41796-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="41796-131">Podczas tworzenia wystąpienia przełącznika również jej inicjalizację, określając dwa argumenty: *displayName* argumentu i *opis* argumentu.</span><span class="sxs-lookup"><span data-stu-id="41796-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="41796-132">*DisplayName* argument zestawy Konstruktor <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> właściwość <xref:System.Diagnostics.Switch> wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="41796-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="41796-133">*DisplayName* jest nazwa, która służy do konfigurowania przełącznika w pliku config i *opis* argument powinien zwrócić krótki opis przełącznika i jakie komunikaty kontrolki.</span><span class="sxs-lookup"><span data-stu-id="41796-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="41796-134">Oprócz określenia nazwy przełącznika w celu skonfigurowania, należy także określić wartość dla przełącznika.</span><span class="sxs-lookup"><span data-stu-id="41796-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="41796-135">Ta wartość jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="41796-135">This value is an Integer.</span></span> <span data-ttu-id="41796-136">Dla <xref:System.Diagnostics.BooleanSwitch>, wartości 0 odpowiada **poza**, i odpowiada dowolną wartość różną od zera **na**.</span><span class="sxs-lookup"><span data-stu-id="41796-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="41796-137">Dla <xref:System.Diagnostics.TraceSwitch>0,1,2,3 oraz 4 odpowiadają **poza**, **błąd**, **ostrzeżenie**, **informacje**, i **pełne**, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="41796-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="41796-138">Wszystkie liczby większe niż 4 jest traktowany jako **pełne**oraz numer mniej niż zero jest traktowany jako **poza**.</span><span class="sxs-lookup"><span data-stu-id="41796-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41796-139">W .NET Framework w wersji 2.0 można użyć tekstu, aby określić wartość dla przełącznika.</span><span class="sxs-lookup"><span data-stu-id="41796-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="41796-140">Na przykład `true` dla <xref:System.Diagnostics.BooleanSwitch> lub tekstu, takie jak reprezentujących wartości wyliczenia `Error` dla <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="41796-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="41796-141">Wiersz `<add name="myTraceSwitch" value="Error" />` jest odpowiednikiem `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="41796-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="41796-142">Aby użytkownicy końcowi mogli Konfigurowanie przełączników śledzenia aplikacji musisz podać szczegółową dokumentację na temat parametrów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41796-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="41796-143">Należy szczegółowo, które przełączniki kontrolować, co oraz sposób ich włączać i wyłączać.</span><span class="sxs-lookup"><span data-stu-id="41796-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="41796-144">Należy również podać użytkownikowi końcowemu przy użyciu pliku .config zawierającej odpowiednią pomoc w komentarzach.</span><span class="sxs-lookup"><span data-stu-id="41796-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="41796-145">Aby skonfigurować przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="41796-145">To configure trace switches</span></span>  
  
1. <span data-ttu-id="41796-146">Aby można było używać przełączników śledzenia, najpierw należy je utworzyć i umieść je w swoim kodzie, zgodnie z opisem w sekcji [tworzenie i Inicjowanie przełącznikiem śledzenia](#create).</span><span class="sxs-lookup"><span data-stu-id="41796-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="41796-147">Jeśli projekt nie zawiera pliku konfiguracji (app.config lub Web.config), następnie z **projektu** menu, wybierz opcję **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="41796-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="41796-148">**Visual Basic:** W **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="41796-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="41796-149">Plik konfiguracji aplikacji zostanie utworzony i otwarty.</span><span class="sxs-lookup"><span data-stu-id="41796-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="41796-150">To jest którego element główny dokumentu XML `<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="41796-150">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="41796-151">**Wizualne C#:** W **Dodaj nowy element** okna dialogowego wybierz **pliku XML**.</span><span class="sxs-lookup"><span data-stu-id="41796-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="41796-152">Nazwij ten plik **app.config**. W edytorze XML, po deklaracji XML, Dodaj następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="41796-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="41796-153">Podczas kompilowania projektu pliku app.config jest kopiowany do folderu wyjściowego projektu i została zmieniona *applicationname*. exe.config.</span><span class="sxs-lookup"><span data-stu-id="41796-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="41796-154">Po `<configuration>` tagu, ale przed `</configuration>` tag, Dodaj odpowiedni kod XML do skonfigurowania przełączników.</span><span class="sxs-lookup"><span data-stu-id="41796-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="41796-155">W poniższych przykładach pokazano **BooleanSwitch** z **DisplayName** właściwość `DataMessageSwitch` i **TraceSwitch** z **DisplayName**  właściwość `TraceLevelSwitch`.</span><span class="sxs-lookup"><span data-stu-id="41796-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="41796-156">W tej konfiguracji oba przełączniki są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="41796-156">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="41796-157">Jeśli konieczne jest włączenie **BooleanSwitch**, takich jak `DataMessagesSwitch` pokazano w poprzednim przykładzie, zmień **wartość** do dowolnej liczby całkowitej, innym niż 0.</span><span class="sxs-lookup"><span data-stu-id="41796-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="41796-158">Jeśli konieczne jest włączenie **TraceSwitch**, takich jak `TraceLevelSwitch` pokazano w poprzednim przykładzie, zmień **wartość** odpowiednie ustawienie poziomie (od 1 do 4).</span><span class="sxs-lookup"><span data-stu-id="41796-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="41796-159">Aby użytkownik końcowy miał świadomość, jakich wartości można zmienić na odpowiednio skonfigurować przełączniki, dodać komentarze do pliku Config.</span><span class="sxs-lookup"><span data-stu-id="41796-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="41796-160">Poniższy przykład pokazuje, jak może wyglądać końcowego kodu, w tym komentarzy:</span><span class="sxs-lookup"><span data-stu-id="41796-160">The following example shows how the final code, including comments, might look:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41796-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41796-161">See also</span></span>

- [<span data-ttu-id="41796-162">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="41796-162">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="41796-163">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="41796-163">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="41796-164">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="41796-164">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="41796-165">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="41796-165">Trace and Debug Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
