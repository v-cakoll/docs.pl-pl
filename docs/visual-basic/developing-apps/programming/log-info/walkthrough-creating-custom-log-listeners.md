---
title: tworzenie odbiorców dzienników niestandardowych
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 5a140607a4fe7e1e13de54e8d56cab53e52aaa2a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398269"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="a9189-102">Wskazówki: tworzenie odbiorników logu niestandardowego (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9189-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="a9189-103">W tym instruktażu pokazano, jak utworzyć odbiornik dziennika niestandardowego i skonfigurować go do nasłuchiwania danych wyjściowych `My.Application.Log` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9189-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="a9189-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="a9189-104">Getting Started</span></span>

<span data-ttu-id="a9189-105">Odbiorniki dzienników muszą dziedziczyć z <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="a9189-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="a9189-106">Aby utworzyć odbiornik</span><span class="sxs-lookup"><span data-stu-id="a9189-106">To create the listener</span></span>

- <span data-ttu-id="a9189-107">W aplikacji Utwórz klasę o nazwie `SimpleListener` , która dziedziczy z <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="a9189-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="a9189-108"><xref:System.Diagnostics.TraceListener.Write%2A>Metody i <xref:System.Diagnostics.TraceListener.WriteLine%2A> , wymagane przez klasę bazową, wywołują, `MsgBox` Aby wyświetlić ich dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="a9189-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="a9189-109">Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut jest stosowany do <xref:System.Diagnostics.TraceListener.Write%2A> metod i, <xref:System.Diagnostics.TraceListener.WriteLine%2A> tak aby ich atrybuty pasowały do metod klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="a9189-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="a9189-110">Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut zezwala na hosta, na którym jest uruchamiany kod, aby określić, że kod uwidacznia synchronizację z ochroną hosta.</span><span class="sxs-lookup"><span data-stu-id="a9189-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a9189-111">Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut obowiązuje tylko w przypadku niezarządzanych aplikacji obsługujących środowisko uruchomieniowe języka wspólnego i implementujących ochronę hosta, takich jak SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a9189-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="a9189-112">Aby zapewnić, że program `My.Application.Log` korzysta z odbiornika dzienników, należy silnie nawiązać nazwę zestawu, który zawiera odbiornik dzienników.</span><span class="sxs-lookup"><span data-stu-id="a9189-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="a9189-113">Kolejna procedura zawiera kilka prostych kroków służących do tworzenia silnie nazwanego zestawu detektora dzienników.</span><span class="sxs-lookup"><span data-stu-id="a9189-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="a9189-114">Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnej nazwie](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="a9189-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="a9189-115">Aby silnie nawiązać nazwę zestawu odbiornika dzienników</span><span class="sxs-lookup"><span data-stu-id="a9189-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="a9189-116">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="a9189-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a9189-117">W menu **projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a9189-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="a9189-118">Kliknij kartę **podpisywanie** .</span><span class="sxs-lookup"><span data-stu-id="a9189-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="a9189-119">Zaznacz pole **podpisz zestaw** .</span><span class="sxs-lookup"><span data-stu-id="a9189-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="a9189-120">Wybierz **\<New>** z listy rozwijanej **Wybierz plik klucza o silnej nazwie** .</span><span class="sxs-lookup"><span data-stu-id="a9189-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="a9189-121">Zostanie otwarte okno dialogowe **Tworzenie klucza silnej nazwy** .</span><span class="sxs-lookup"><span data-stu-id="a9189-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="a9189-122">Podaj nazwę pliku klucza w polu **Nazwa pliku klucza** .</span><span class="sxs-lookup"><span data-stu-id="a9189-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="a9189-123">Wprowadź hasło w polach **Wprowadź hasło** i **Potwierdź hasło** .</span><span class="sxs-lookup"><span data-stu-id="a9189-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="a9189-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9189-124">Click **OK**.</span></span>

8. <span data-ttu-id="a9189-125">Skompiluj ponownie aplikację.</span><span class="sxs-lookup"><span data-stu-id="a9189-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="a9189-126">Dodawanie odbiornika</span><span class="sxs-lookup"><span data-stu-id="a9189-126">Adding the Listener</span></span>

<span data-ttu-id="a9189-127">Teraz, gdy zestaw ma silną nazwę, należy określić silną nazwę odbiornika, aby `My.Application.Log` używała odbiornika dzienników.</span><span class="sxs-lookup"><span data-stu-id="a9189-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="a9189-128">Format silnie nazwanego typu jest następujący.</span><span class="sxs-lookup"><span data-stu-id="a9189-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="a9189-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span><span class="sxs-lookup"><span data-stu-id="a9189-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="a9189-130">Aby określić silną nazwę odbiornika</span><span class="sxs-lookup"><span data-stu-id="a9189-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="a9189-131">Poniższy kod pokazuje, jak określić silną nazwę typu dla `SimpleListener` .</span><span class="sxs-lookup"><span data-stu-id="a9189-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="a9189-132">Silna nazwa typu zależy od projektu.</span><span class="sxs-lookup"><span data-stu-id="a9189-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="a9189-133">Za pomocą silnej nazwy można dodać odbiornik do `My.Application.Log` kolekcji detektorów dzienników.</span><span class="sxs-lookup"><span data-stu-id="a9189-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="a9189-134">Aby dodać odbiornik do My. Application. log</span><span class="sxs-lookup"><span data-stu-id="a9189-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="a9189-135">Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="a9189-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="a9189-136">-lub-</span><span class="sxs-lookup"><span data-stu-id="a9189-136">-or-</span></span>

     <span data-ttu-id="a9189-137">Jeśli istnieje plik App. config:</span><span class="sxs-lookup"><span data-stu-id="a9189-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="a9189-138">W menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="a9189-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="a9189-139">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="a9189-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="a9189-140">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a9189-140">Click **Add**.</span></span>

2. <span data-ttu-id="a9189-141">Znajdź `<listeners>` sekcję w sekcji `<source>` z `name` atrybutem "DefaultSource", który znajduje się w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="a9189-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="a9189-142">Sekcja znajduje się `<sources>` w `<system.diagnostics>` sekcji w sekcji najwyższego poziomu `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="a9189-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="a9189-143">Dodaj ten element do `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="a9189-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="a9189-144">Znajdź sekcję w sekcji `<sharedListeners>` `<system.diagnostics>` , w sekcji najwyższego poziomu `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="a9189-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="a9189-145">Dodaj ten element do tej `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="a9189-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="a9189-146">Zmień wartość tak, `SimpleLogStrongName` aby była silną nazwą odbiornika.</span><span class="sxs-lookup"><span data-stu-id="a9189-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9189-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9189-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="a9189-148">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="a9189-148">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="a9189-149">Instrukcje: rejestrowanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="a9189-149">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="a9189-150">Instrukcje: zapisywanie komunikatów dziennika</span><span class="sxs-lookup"><span data-stu-id="a9189-150">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="a9189-151">Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="a9189-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
