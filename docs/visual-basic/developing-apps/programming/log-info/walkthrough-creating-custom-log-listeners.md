---
title: tworzenie odbiorców dzienników niestandardowych
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353624"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="32e29-102">Wskazówki: tworzenie odbiorników logu niestandardowego (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32e29-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="32e29-103">W tym przewodniku pokazano, jak utworzyć odbiornik dziennika niestandardowego i skonfigurować `My.Application.Log` go do nasłuchiwać danych wyjściowych obiektu.</span><span class="sxs-lookup"><span data-stu-id="32e29-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="32e29-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="32e29-104">Getting Started</span></span>

<span data-ttu-id="32e29-105">Detektory dziennika musi <xref:System.Diagnostics.TraceListener> dziedziczyć z klasy.</span><span class="sxs-lookup"><span data-stu-id="32e29-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="32e29-106">Aby utworzyć odbiornik</span><span class="sxs-lookup"><span data-stu-id="32e29-106">To create the listener</span></span>

- <span data-ttu-id="32e29-107">W aplikacji utwórz klasę `SimpleListener` o nazwie, która dziedziczy po <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="32e29-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="32e29-108">I <xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody, wymagane przez klasę podstawową, wywołać, `MsgBox` aby wyświetlić ich dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="32e29-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="32e29-109">Atrybut <xref:System.Security.Permissions.HostProtectionAttribute> jest stosowany do <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody, tak aby ich atrybuty zgodne z metody klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="32e29-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="32e29-110">Atrybut <xref:System.Security.Permissions.HostProtectionAttribute> umożliwia hostowi, który uruchamia kod, aby ustalić, że kod udostępnia synchronizację ochrony hosta.</span><span class="sxs-lookup"><span data-stu-id="32e29-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="32e29-111">Atrybut <xref:System.Security.Permissions.HostProtectionAttribute> jest skuteczny tylko w przypadku niezarządzanych aplikacji, które hostują środowisko uruchomieniowe języka wspólnego i które implementują ochronę hosta, takich jak SQL Server.</span><span class="sxs-lookup"><span data-stu-id="32e29-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="32e29-112">Aby upewnić się, że `My.Application.Log` używa odbiornika dziennika, należy zdecydowanie nazwa zestawu, który zawiera odbiornika dziennika.</span><span class="sxs-lookup"><span data-stu-id="32e29-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="32e29-113">Następna procedura zawiera kilka prostych kroków do tworzenia zestawu odbiornika dziennika o silnie nazwanej.</span><span class="sxs-lookup"><span data-stu-id="32e29-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="32e29-114">Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="32e29-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="32e29-115">Aby zdecydowanie nazwać zestaw detektora dziennika</span><span class="sxs-lookup"><span data-stu-id="32e29-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="32e29-116">Wybierz projekt w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="32e29-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="32e29-117">W menu **Projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="32e29-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="32e29-118">Kliknij kartę **Podpisywanie.**</span><span class="sxs-lookup"><span data-stu-id="32e29-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="32e29-119">Zaznacz pole **Podpisz złożenie.**</span><span class="sxs-lookup"><span data-stu-id="32e29-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="32e29-120">Wybierz \*\* \<pozycję Nowy>\*\* z listy **rozwijanej Wybierz plik klucza silnej nazwy.**</span><span class="sxs-lookup"><span data-stu-id="32e29-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="32e29-121">Zostanie otwarte okno dialogowe **Tworzenie klucza silnej nazwy.**</span><span class="sxs-lookup"><span data-stu-id="32e29-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="32e29-122">Podaj nazwę pliku klucza w polu **Nazwa pliku klucza.**</span><span class="sxs-lookup"><span data-stu-id="32e29-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="32e29-123">Wprowadź hasło w polach **Wprowadź hasło** i **Potwierdź hasło.**</span><span class="sxs-lookup"><span data-stu-id="32e29-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="32e29-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="32e29-124">Click **OK**.</span></span>

8. <span data-ttu-id="32e29-125">Odbuduj aplikację.</span><span class="sxs-lookup"><span data-stu-id="32e29-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="32e29-126">Dodawanie odbiornika</span><span class="sxs-lookup"><span data-stu-id="32e29-126">Adding the Listener</span></span>

<span data-ttu-id="32e29-127">Teraz, gdy zestaw ma silną nazwę, należy określić silną `My.Application.Log` nazwę odbiornika, tak aby używa odbiornika dziennika.</span><span class="sxs-lookup"><span data-stu-id="32e29-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="32e29-128">Format typu o silnie nazwanym jest następujący.</span><span class="sxs-lookup"><span data-stu-id="32e29-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="32e29-129">\<> nazwa typu, \<> nazwa zestawu, \<numer wersji>, \<> kultury, \<></span><span class="sxs-lookup"><span data-stu-id="32e29-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="32e29-130">Aby określić silną nazwę odbiornika</span><span class="sxs-lookup"><span data-stu-id="32e29-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="32e29-131">Poniższy kod pokazuje, jak określić `SimpleListener`nazwę typu o silnie nazwanej dla .</span><span class="sxs-lookup"><span data-stu-id="32e29-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="32e29-132">Silna nazwa typu zależy od projektu.</span><span class="sxs-lookup"><span data-stu-id="32e29-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="32e29-133">Dzięki silnej nazwie można dodać odbiornik `My.Application.Log` do kolekcji detektora dziennika.</span><span class="sxs-lookup"><span data-stu-id="32e29-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="32e29-134">Aby dodać odbiornik do My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="32e29-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="32e29-135">Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz pozycję **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="32e29-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="32e29-136">— lub —</span><span class="sxs-lookup"><span data-stu-id="32e29-136">-or-</span></span>

     <span data-ttu-id="32e29-137">Jeśli istnieje plik app.config:</span><span class="sxs-lookup"><span data-stu-id="32e29-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="32e29-138">W menu **Projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="32e29-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="32e29-139">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="32e29-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="32e29-140">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="32e29-140">Click **Add**.</span></span>

2. <span data-ttu-id="32e29-141">Znajdź `<listeners>` sekcję w `<source>` sekcji `name` z atrybutem "DefaultSource", `<sources>` znajdującym się w sekcji.</span><span class="sxs-lookup"><span data-stu-id="32e29-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="32e29-142">Sekcja `<sources>` znajduje się `<system.diagnostics>` w sekcji, w `<configuration>` sekcji najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="32e29-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="32e29-143">Dodaj ten element `<listeners>` do sekcji:</span><span class="sxs-lookup"><span data-stu-id="32e29-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="32e29-144">Zlokalizuj `<sharedListeners>` `<system.diagnostics>` sekcję w sekcji `<configuration>` w sekcji najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="32e29-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="32e29-145">Dodaj ten element `<sharedListeners>` do tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="32e29-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="32e29-146">Zmień `SimpleLogStrongName` wartość, aby być silną nazwą odbiornika.</span><span class="sxs-lookup"><span data-stu-id="32e29-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="32e29-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32e29-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="32e29-148">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="32e29-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="32e29-149">Porady: wyjątki rejestru</span><span class="sxs-lookup"><span data-stu-id="32e29-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="32e29-150">Porady: zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="32e29-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="32e29-151">Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="32e29-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
