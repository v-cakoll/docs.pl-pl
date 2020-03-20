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
ms.openlocfilehash: 8bf3b974ff0ef9f719274ab684b3dce85295c917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181824"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="ff08a-102">Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="ff08a-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="ff08a-103">Przełączniki śledzenia umożliwiają włączanie, wyłączanie i filtrowanie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ff08a-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="ff08a-104">Tworzenie i inicjowanie przełącznika śledzenia</span><span class="sxs-lookup"><span data-stu-id="ff08a-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="ff08a-105">Aby użyć przełączników śledzenia, należy je najpierw utworzyć i umieścić je w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ff08a-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="ff08a-106">Istnieją dwie wstępnie zdefiniowane klasy, z których można <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> tworzyć <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> obiekty switch: klasę i klasę.</span><span class="sxs-lookup"><span data-stu-id="ff08a-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ff08a-107"><xref:System.Diagnostics.BooleanSwitch> Użyjesz, jeśli zależy Ci tylko na tym, czy pojawi się komunikat śledzenia; <xref:System.Diagnostics.TraceSwitch> jeśli chcesz rozróżnić poziomy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ff08a-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="ff08a-108">Jeśli używasz <xref:System.Diagnostics.TraceSwitch>programu , można zdefiniować własne komunikaty debugowania i skojarzyć je z różnymi poziomami śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ff08a-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="ff08a-109">Można użyć obu typów przełączników z śledzenia lub debugowania.</span><span class="sxs-lookup"><span data-stu-id="ff08a-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="ff08a-110">Domyślnie a <xref:System.Diagnostics.BooleanSwitch> jest wyłączona i a jest ustawiona <xref:System.Diagnostics.TraceSwitch> na poziom <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ff08a-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ff08a-111">Przełączniki śledzenia można utworzyć i umieścić w dowolnej części kodu, która może ich używać.</span><span class="sxs-lookup"><span data-stu-id="ff08a-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="ff08a-112">Chociaż można ustawić poziomy śledzenia i inne opcje konfiguracji w kodzie, zaleca się użycie pliku konfiguracyjnego do zarządzania stanem przełączników.</span><span class="sxs-lookup"><span data-stu-id="ff08a-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="ff08a-113">Dzieje się tak, ponieważ zarządzanie konfiguracją przełączników w systemie konfiguracyjnym zapewnia większą elastyczność — można włączać i wyłączać różne przełączniki i zmieniać poziomy bez ponownego komppilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff08a-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="ff08a-114">Aby utworzyć i zainicjować przełącznik śledzenia</span><span class="sxs-lookup"><span data-stu-id="ff08a-114">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="ff08a-115">Zdefiniuj przełącznik <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> jako <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> typ lub typ i ustaw nazwę i opis przełącznika.</span><span class="sxs-lookup"><span data-stu-id="ff08a-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="ff08a-116">Skonfiguruj przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ff08a-116">Configure your trace switch.</span></span> <span data-ttu-id="ff08a-117">Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](#configure).</span><span class="sxs-lookup"><span data-stu-id="ff08a-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="ff08a-118">Poniższy kod tworzy dwa przełączniki, po jednym z każdego typu:</span><span class="sxs-lookup"><span data-stu-id="ff08a-118">The following code creates two switches, one of each type:</span></span>  
  
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
## <a name="configuring-trace-switches"></a><span data-ttu-id="ff08a-119">Konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="ff08a-119">Configuring trace switches</span></span>  
 <span data-ttu-id="ff08a-120">Po rozesłaniu aplikacji nadal można włączyć lub wyłączyć dane wyjściowe śledzenia, konfigurując przełączniki śledzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff08a-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="ff08a-121">Konfigurowanie przełącznika oznacza zmianę jego wartości ze źródła zewnętrznego po jego zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="ff08a-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="ff08a-122">Za pomocą pliku konfiguracyjnego można zmienić wartości obiektów przełącznika.</span><span class="sxs-lookup"><span data-stu-id="ff08a-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="ff08a-123">Można skonfigurować przełącznik śledzenia, aby go włączyć i wyłączyć lub ustawić jego poziom, określając ilość i typ wiadomości przekazuje do odbiorników.</span><span class="sxs-lookup"><span data-stu-id="ff08a-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="ff08a-124">Przełączniki są konfigurowane przy użyciu pliku .config.</span><span class="sxs-lookup"><span data-stu-id="ff08a-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="ff08a-125">W przypadku aplikacji sieci Web jest to plik Web.config skojarzony z projektem.</span><span class="sxs-lookup"><span data-stu-id="ff08a-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="ff08a-126">W aplikacji systemu Windows ten plik nosi nazwę (nazwa aplikacji).exe.config. W wdrożonej aplikacji ten plik musi znajdować się w tym samym folderze co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="ff08a-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="ff08a-127">Gdy aplikacja wykonuje kod, który tworzy wystąpienie przełącznika po raz pierwszy, sprawdza plik konfiguracji pod kątem informacji na poziomie śledzenia o nazwanym przełączniku.</span><span class="sxs-lookup"><span data-stu-id="ff08a-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="ff08a-128">System śledzenia sprawdza plik konfiguracyjny tylko raz dla dowolnego konkretnego przełącznika — po raz pierwszy aplikacja tworzy przełącznik.</span><span class="sxs-lookup"><span data-stu-id="ff08a-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="ff08a-129">W wdrożonej aplikacji można włączyć kod śledzenia przez ponowne skonfigurowanie obiektów przełącznika, gdy aplikacja nie jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ff08a-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="ff08a-130">Zazwyczaj wiąże się to z włączaniem i wyłączaniem obiektów przełącznika lub zmienianiem poziomów śledzenia, a następnie ponownym uruchomieniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff08a-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="ff08a-131">Podczas tworzenia wystąpienia przełącznika, należy również zainicjować go, określając dwa argumenty: *argument displayName* i argument *opisu.*</span><span class="sxs-lookup"><span data-stu-id="ff08a-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="ff08a-132">Argument *displayName* konstruktora <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> ustawia właściwość wystąpienia <xref:System.Diagnostics.Switch> klasy.</span><span class="sxs-lookup"><span data-stu-id="ff08a-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="ff08a-133">*DisplayName* to nazwa używana do konfigurowania przełącznika w pliku .config, a argument *opisu* powinien zwracać krótki opis przełącznika i jakie wiadomości steruje.</span><span class="sxs-lookup"><span data-stu-id="ff08a-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="ff08a-134">Oprócz określania nazwy przełącznika do skonfigurowania, należy również określić wartość przełącznika.</span><span class="sxs-lookup"><span data-stu-id="ff08a-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="ff08a-135">Ta wartość jest całkowitej liczby.</span><span class="sxs-lookup"><span data-stu-id="ff08a-135">This value is an Integer.</span></span> <span data-ttu-id="ff08a-136">Dla <xref:System.Diagnostics.BooleanSwitch>, wartość 0 odpowiada **Off**, a każda wartość niezerowa odpowiada **On**.</span><span class="sxs-lookup"><span data-stu-id="ff08a-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="ff08a-137">Dla <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3 i 4 odpowiadają **Off**, **Błąd**, **Ostrzeżenie**, **Info**i **Pełne**, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="ff08a-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="ff08a-138">Dowolna liczba większa niż 4 jest traktowana jako **szczegółowa,** a dowolna liczba mniejsza niż zero jest traktowana jako **Wyłącz.**</span><span class="sxs-lookup"><span data-stu-id="ff08a-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff08a-139">W .NET Framework w wersji 2.0 można użyć tekstu, aby określić wartość przełącznika.</span><span class="sxs-lookup"><span data-stu-id="ff08a-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="ff08a-140">Na przykład `true` dla <xref:System.Diagnostics.BooleanSwitch> tekstu lub tekstu reprezentującego wartość wyliczenia, taką jak `Error` dla <xref:System.Diagnostics.TraceSwitch>pliku .</span><span class="sxs-lookup"><span data-stu-id="ff08a-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="ff08a-141">Linia `<add name="myTraceSwitch" value="Error" />` jest równoważna `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="ff08a-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="ff08a-142">Aby użytkownicy końcowi mogli skonfigurować przełączniki śledzenia aplikacji, należy dostarczyć szczegółową dokumentację dotyczącą przełączników w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff08a-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="ff08a-143">Należy szczegółowo, które przełączniki kontrolować, co i jak je włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="ff08a-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="ff08a-144">Należy również podać użytkownikowi końcowemu plik .config, który ma odpowiednią Pomoc w komentarzach.</span><span class="sxs-lookup"><span data-stu-id="ff08a-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="ff08a-145">Aby skonfigurować przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="ff08a-145">To configure trace switches</span></span>  
  
1. <span data-ttu-id="ff08a-146">Aby użyć przełączników śledzenia, należy je najpierw utworzyć i umieścić w kodzie zgodnie z opisem w sekcji [Tworzenie i inicjowanie przełącznika śledzenia](#create).</span><span class="sxs-lookup"><span data-stu-id="ff08a-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="ff08a-147">Jeśli projekt nie zawiera pliku konfiguracyjnego (app.config lub Web.config), z menu **Projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ff08a-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="ff08a-148">**Visual Basic:** W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="ff08a-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="ff08a-149">Plik konfiguracji aplikacji jest tworzony i otwierany.</span><span class="sxs-lookup"><span data-stu-id="ff08a-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="ff08a-150">Jest to dokument XML, którego element główny jest`<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="ff08a-150">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="ff08a-151">**Visual C#:** W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik **XML**.</span><span class="sxs-lookup"><span data-stu-id="ff08a-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="ff08a-152">Nazwij ten plik **app.config**. W edytorze XML po deklaracji XML dodaj następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="ff08a-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="ff08a-153">Podczas kompilowania projektu plik app.config jest kopiowany do folderu wyjściowego projektu i zmienia nazwę *nazwy aplikacji*.exe.config.</span><span class="sxs-lookup"><span data-stu-id="ff08a-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="ff08a-154">Po `<configuration>` tagu, `</configuration>` ale przed tagiem, dodaj odpowiedni kod XML, aby skonfigurować przełączniki.</span><span class="sxs-lookup"><span data-stu-id="ff08a-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="ff08a-155">Poniższe przykłady pokazują **przełącznik logiczny** z właściwością `DataMessageSwitch` **DisplayName** i **przełącznikiem TraceSwitch** z właściwością **DisplayName** . `TraceLevelSwitch`</span><span class="sxs-lookup"><span data-stu-id="ff08a-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="ff08a-156">W tej konfiguracji oba przełączniki są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ff08a-156">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="ff08a-157">Jeśli chcesz włączyć **przełącznik logiczny,** na przykład `DataMessagesSwitch` w poprzednim przykładzie, zmień **wartość** na dowolną liczę całkowitą inną niż 0.</span><span class="sxs-lookup"><span data-stu-id="ff08a-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="ff08a-158">Jeśli chcesz włączyć **przełącznik TraceS,** na `TraceLevelSwitch` przykład w poprzednim przykładzie, zmień **wartość** na odpowiednie ustawienie poziomu (1 na 4).</span><span class="sxs-lookup"><span data-stu-id="ff08a-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="ff08a-159">Dodaj komentarze do pliku .config, aby użytkownik końcowy miał jasną wiedzę na temat wartości, które należy zmienić, aby odpowiednio skonfigurować przełączniki.</span><span class="sxs-lookup"><span data-stu-id="ff08a-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="ff08a-160">W poniższym przykładzie pokazano, jak może wyglądać ostateczny kod, w tym komentarze:</span><span class="sxs-lookup"><span data-stu-id="ff08a-160">The following example shows how the final code, including comments, might look:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff08a-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff08a-161">See also</span></span>

- [<span data-ttu-id="ff08a-162">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="ff08a-162">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="ff08a-163">Porady: dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="ff08a-163">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="ff08a-164">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="ff08a-164">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="ff08a-165">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="ff08a-165">Trace and Debug Settings Schema</span></span>](../configure-apps/file-schema/trace-debug/index.md)
