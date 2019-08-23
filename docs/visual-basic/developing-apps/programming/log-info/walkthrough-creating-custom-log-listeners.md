---
title: Tworzenie odbiorników dziennika niestandardowego (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 90135074a4d34ea73743faffb2531305fcb326fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965260"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="abf74-102">Przewodnik: Tworzenie odbiorników dziennika niestandardowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abf74-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="abf74-103">W tym instruktażu pokazano, jak utworzyć odbiornik dziennika niestandardowego i skonfigurować go do nasłuchiwania danych wyjściowych `My.Application.Log` obiektu.</span><span class="sxs-lookup"><span data-stu-id="abf74-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="abf74-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="abf74-104">Getting Started</span></span>  
 <span data-ttu-id="abf74-105">Odbiorniki dzienników muszą dziedziczyć <xref:System.Diagnostics.TraceListener> z klasy.</span><span class="sxs-lookup"><span data-stu-id="abf74-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="abf74-106">Aby utworzyć odbiornik</span><span class="sxs-lookup"><span data-stu-id="abf74-106">To create the listener</span></span>  
  
- <span data-ttu-id="abf74-107">W aplikacji Utwórz klasę o nazwie `SimpleListener` , która dziedziczy z. <xref:System.Diagnostics.TraceListener></span><span class="sxs-lookup"><span data-stu-id="abf74-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <span data-ttu-id="abf74-108">Metody <xref:System.Diagnostics.TraceListener.Write%2A> `MsgBox` i <xref:System.Diagnostics.TraceListener.WriteLine%2A> , wymagane przez klasę bazową, wywołują, aby wyświetlić ich dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="abf74-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="abf74-109">Ten atrybut jest stosowany <xref:System.Diagnostics.TraceListener.Write%2A> do metod i <xref:System.Diagnostics.TraceListener.WriteLine%2A> , tak aby ich atrybuty pasowały do metod klasy bazowej. <xref:System.Security.Permissions.HostProtectionAttribute></span><span class="sxs-lookup"><span data-stu-id="abf74-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="abf74-110">Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut zezwala na hosta, na którym jest uruchamiany kod, aby określić, że kod uwidacznia synchronizację z ochroną hosta.</span><span class="sxs-lookup"><span data-stu-id="abf74-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="abf74-111">Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut obowiązuje tylko w przypadku niezarządzanych aplikacji obsługujących środowisko uruchomieniowe języka wspólnego i implementujących ochronę hosta, takich jak SQL Server.</span><span class="sxs-lookup"><span data-stu-id="abf74-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="abf74-112">Aby zapewnić, `My.Application.Log` że program korzysta z odbiornika dzienników, należy silnie nawiązać nazwę zestawu, który zawiera odbiornik dzienników.</span><span class="sxs-lookup"><span data-stu-id="abf74-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="abf74-113">Kolejna procedura zawiera kilka prostych kroków służących do tworzenia silnie nazwanego zestawu detektora dzienników.</span><span class="sxs-lookup"><span data-stu-id="abf74-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="abf74-114">Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnej nazwie](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="abf74-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="abf74-115">Aby silnie nawiązać nazwę zestawu odbiornika dzienników</span><span class="sxs-lookup"><span data-stu-id="abf74-115">To strongly name the log-listener assembly</span></span>  
  
1. <span data-ttu-id="abf74-116">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="abf74-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="abf74-117">W menu **projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="abf74-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2. <span data-ttu-id="abf74-118">Kliknij kartę podpisywanie.</span><span class="sxs-lookup"><span data-stu-id="abf74-118">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="abf74-119">Zaznacz pole **podpisz zestaw** .</span><span class="sxs-lookup"><span data-stu-id="abf74-119">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="abf74-120">Wybierz pozycję  **\<Nowy >** z listy rozwijanej **Wybierz plik klucza o silnej nazwie** .</span><span class="sxs-lookup"><span data-stu-id="abf74-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="abf74-121">Zostanie otwarte okno dialogowe **Tworzenie klucza silnej nazwy** .</span><span class="sxs-lookup"><span data-stu-id="abf74-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5. <span data-ttu-id="abf74-122">Podaj nazwę pliku klucza w polu **Nazwa pliku klucza** .</span><span class="sxs-lookup"><span data-stu-id="abf74-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6. <span data-ttu-id="abf74-123">Wprowadź hasło w polach **Wprowadź hasło** i **Potwierdź hasło** .</span><span class="sxs-lookup"><span data-stu-id="abf74-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7. <span data-ttu-id="abf74-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="abf74-124">Click **OK**.</span></span>  
  
8. <span data-ttu-id="abf74-125">Skompiluj ponownie aplikację.</span><span class="sxs-lookup"><span data-stu-id="abf74-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="abf74-126">Dodawanie odbiornika</span><span class="sxs-lookup"><span data-stu-id="abf74-126">Adding the Listener</span></span>  
 <span data-ttu-id="abf74-127">Teraz, gdy zestaw ma silną nazwę, należy określić silną nazwę odbiornika, aby `My.Application.Log` używała odbiornika dzienników.</span><span class="sxs-lookup"><span data-stu-id="abf74-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="abf74-128">Format silnie nazwanego typu jest następujący.</span><span class="sxs-lookup"><span data-stu-id="abf74-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="abf74-129">\<Nazwa typu >, \<nazwa zestawu >, \<numer wersji >, \<kultura >, \<silna nazwa ></span><span class="sxs-lookup"><span data-stu-id="abf74-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="abf74-130">Aby określić silną nazwę odbiornika</span><span class="sxs-lookup"><span data-stu-id="abf74-130">To determine the strong name of the listener</span></span>  
  
- <span data-ttu-id="abf74-131">Poniższy kod pokazuje, jak określić silną nazwę typu dla `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="abf74-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     <span data-ttu-id="abf74-132">Silna nazwa typu zależy od projektu.</span><span class="sxs-lookup"><span data-stu-id="abf74-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="abf74-133">Za pomocą silnej nazwy można dodać odbiornik do `My.Application.Log` kolekcji detektorów dzienników.</span><span class="sxs-lookup"><span data-stu-id="abf74-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="abf74-134">Aby dodać odbiornik do My. Application. log</span><span class="sxs-lookup"><span data-stu-id="abf74-134">To add the listener to My.Application.Log</span></span>  
  
1. <span data-ttu-id="abf74-135">Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="abf74-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="abf74-136">—lub—</span><span class="sxs-lookup"><span data-stu-id="abf74-136">-or-</span></span>  
  
     <span data-ttu-id="abf74-137">Jeśli istnieje plik App. config:</span><span class="sxs-lookup"><span data-stu-id="abf74-137">If there is an app.config file:</span></span>  
  
    1. <span data-ttu-id="abf74-138">W menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="abf74-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="abf74-139">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="abf74-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="abf74-140">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="abf74-140">Click **Add**.</span></span>  
  
2. <span data-ttu-id="abf74-141">Znajdź sekcję w sekcji z `name` atrybutem "DefaultSource", który znajduje się w sekcji.`<sources>` `<source>` `<listeners>`</span><span class="sxs-lookup"><span data-stu-id="abf74-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="abf74-142">Sekcja znajduje się `<system.diagnostics>` w sekcji w sekcji najwyższego poziomu `<configuration>`. `<sources>`</span><span class="sxs-lookup"><span data-stu-id="abf74-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3. <span data-ttu-id="abf74-143">Dodaj ten element do `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="abf74-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4. <span data-ttu-id="abf74-144">`<sharedListeners>` Znajdź sekcję `<system.diagnostics>` w sekcji, w sekcji najwyższego poziomu `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="abf74-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5. <span data-ttu-id="abf74-145">Dodaj ten element do tej `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="abf74-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="abf74-146">Zmień wartość `SimpleLogStrongName` tak, aby była silną nazwą odbiornika.</span><span class="sxs-lookup"><span data-stu-id="abf74-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf74-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abf74-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="abf74-148">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="abf74-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="abf74-149">Instrukcje: Wyjątki dziennika</span><span class="sxs-lookup"><span data-stu-id="abf74-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="abf74-150">Instrukcje: Zapisuj komunikaty dziennika</span><span class="sxs-lookup"><span data-stu-id="abf74-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="abf74-151">Przewodnik: Zmienianie, gdzie my. Application. Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="abf74-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
