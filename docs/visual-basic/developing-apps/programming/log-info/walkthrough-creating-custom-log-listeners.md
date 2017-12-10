---
title: "Tworzenie odbiorników logu niestandardowego (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1bda4a3465af4ed95de720117ea2e03f9a86b84
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="3b6fd-102">Wskazówki: tworzenie odbiorników logu niestandardowego (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b6fd-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="3b6fd-103">W tym przewodniku pokazano, jak utworzyć odbiornik dziennik niestandardowy i skonfigurować go do nasłuchiwania na dane wyjściowe `My.Application.Log` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="3b6fd-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="3b6fd-104">Getting Started</span></span>  
 <span data-ttu-id="3b6fd-105">Odbiorniki logu musi dziedziczyć z <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="3b6fd-106">Aby utworzyć odbiornik</span><span class="sxs-lookup"><span data-stu-id="3b6fd-106">To create the listener</span></span>  
  
-   <span data-ttu-id="3b6fd-107">W aplikacji, Utwórz klasę o nazwie `SimpleListener` dziedziczący po <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]  
  
     <span data-ttu-id="3b6fd-108"><xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> wywołania metody, wymagane przez klasę podstawową `MsgBox` do wyświetlania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="3b6fd-109"><xref:System.Security.Permissions.HostProtectionAttribute> Atrybut jest stosowany do <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody, aby ich atrybutów odpowiadały metod klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="3b6fd-110"><xref:System.Security.Permissions.HostProtectionAttribute> Atrybutu umożliwia hosta, który uruchamia kod, aby określić, że kod przedstawia synchronizacji ochrony hosta.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3b6fd-111"><xref:System.Security.Permissions.HostProtectionAttribute> Atrybut obowiązuje tylko w przypadku niezarządzanych aplikacji, która hostowanie środowiska CLR i implementują ochrony hosta, takich jak SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="3b6fd-112">Aby upewnić się, że `My.Application.Log` używa odbiornika z dziennika, należy silnie nazwę zestawu zawierającego odbiornika z dziennika.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="3b6fd-113">Następna procedura zawiera kilku prostych czynności tworzenia zestawu o silnej nazwie odbiornika dziennika.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="3b6fd-114">Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="3b6fd-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="3b6fd-115">Silnej nazwy zestawu odbiornika dziennika</span><span class="sxs-lookup"><span data-stu-id="3b6fd-115">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="3b6fd-116">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3b6fd-117">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-117">On the **Project** menu, choose **Properties**.</span></span> <span data-ttu-id="3b6fd-118">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="3b6fd-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="3b6fd-119">Kliknij przycisk **podpisywanie** kartę.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-119">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="3b6fd-120">Wybierz **Podpisz zestaw** pole.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-120">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="3b6fd-121">Wybierz  **\<nowy >** z **wybierz plik klucza o silnej nazwie** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-121">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="3b6fd-122">**Tworzenie silnej nazwy klucza** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-122">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="3b6fd-123">Podaj nazwę dla pliku klucza w **nazwę pliku klucza** pole.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-123">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="3b6fd-124">Wprowadź hasło w **wprowadź hasło** i **Potwierdź hasło** pola.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-124">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="3b6fd-125">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-125">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="3b6fd-126">Skompiluj ponownie aplikację.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-126">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="3b6fd-127">Dodawanie odbiornika</span><span class="sxs-lookup"><span data-stu-id="3b6fd-127">Adding the Listener</span></span>  
 <span data-ttu-id="3b6fd-128">Teraz, gdy zestaw ma silną nazwę, należy określić silne nazwę odbiornika, aby `My.Application.Log` używa odbiornika z dziennika.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-128">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="3b6fd-129">Format typu silną nazwą ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-129">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="3b6fd-130">\<Nazwa typu >, \<Nazwa zestawu >, \<numer wersji >, \<kultury >, \<silnej nazwy ></span><span class="sxs-lookup"><span data-stu-id="3b6fd-130">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="3b6fd-131">Aby określić silnej nazwy odbiornika</span><span class="sxs-lookup"><span data-stu-id="3b6fd-131">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="3b6fd-132">Poniższy kod przedstawia sposób określić nazwę typu o silnej nazwie `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-132">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]  
  
     <span data-ttu-id="3b6fd-133">Silnej nazwy typu zależy od projektu.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-133">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="3b6fd-134">O silnej nazwie, można dodać obiektu nasłuchującego do `My.Application.Log` kolekcji odbiornika dziennika.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-134">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="3b6fd-135">Aby dodać odbiornika do My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="3b6fd-135">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="3b6fd-136">Kliknij prawym przyciskiem myszy w pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-136">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="3b6fd-137">—lub—</span><span class="sxs-lookup"><span data-stu-id="3b6fd-137">-or-</span></span>  
  
     <span data-ttu-id="3b6fd-138">W przypadku pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="3b6fd-138">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="3b6fd-139">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-139">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="3b6fd-140">Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-140">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="3b6fd-141">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-141">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="3b6fd-142">Zlokalizuj `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" znajduje się w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-142">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="3b6fd-143">`<sources>` Sekcja znajduje się w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-143">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="3b6fd-144">Ten element, aby dodać `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="3b6fd-144">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="3b6fd-145">Zlokalizuj `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-145">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="3b6fd-146">Dodaj ten element, do którego `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="3b6fd-146">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="3b6fd-147">Zmień wartość `SimpleLogStrongName` silną nazwę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="3b6fd-147">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6fd-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b6fd-148">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="3b6fd-149">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="3b6fd-149">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="3b6fd-150">Porady: wyjątki rejestru</span><span class="sxs-lookup"><span data-stu-id="3b6fd-150">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="3b6fd-151">Porady: zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="3b6fd-151">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="3b6fd-152">Wskazówki: Zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="3b6fd-152">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
