---
title: Tworzenie odbiorników logu niestandardowego (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 6bd950b1648bdf0b0c4673f2a90d67086b338ecd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974773"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="2459e-102">Przewodnik: Tworzenie odbiorników logu niestandardowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2459e-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="2459e-103">W tym instruktażu pokazano, jak tworzenie odbiorników logu niestandardowego i jest skonfigurowana do nasłuchiwania z danymi wyjściowymi `My.Application.Log` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2459e-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="2459e-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="2459e-104">Getting Started</span></span>  
 <span data-ttu-id="2459e-105">Odbiorniki logu musi dziedziczyć <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="2459e-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="2459e-106">Aby utworzyć odbiornik</span><span class="sxs-lookup"><span data-stu-id="2459e-106">To create the listener</span></span>  
  
-   <span data-ttu-id="2459e-107">W aplikacji, należy utworzyć klasę o nazwie `SimpleListener` tej, która dziedziczy <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="2459e-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <span data-ttu-id="2459e-108"><xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> wywołania metody, wymagane przez klasę bazową `MsgBox` wyświetlić ich dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="2459e-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="2459e-109"><xref:System.Security.Permissions.HostProtectionAttribute> Atrybut jest stosowany do <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody, aby ich atrybutów pasują do metod klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="2459e-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="2459e-110"><xref:System.Security.Permissions.HostProtectionAttribute> Atrybut umożliwia hosta, który jest uruchamiany kod w celu określenia, czy kod przedstawia synchronizacji ochrony hosta.</span><span class="sxs-lookup"><span data-stu-id="2459e-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2459e-111"><xref:System.Security.Permissions.HostProtectionAttribute> Atrybut obowiązuje tylko w przypadku niezarządzanych aplikacji, które hostują środowisko uruchomieniowe języka wspólnego i implementują ochrony hosta, takie jak SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2459e-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="2459e-112">Aby upewnić się, że `My.Application.Log` korzysta z odbiornikiem dziennika należy jednoznacznie nazwę zestawu, który zawiera Twoje odbiornika dziennika.</span><span class="sxs-lookup"><span data-stu-id="2459e-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="2459e-113">Następna procedura oferuje kilka prostych kroków tworzenia zestawu o silnej nazwie odbiornika dziennika.</span><span class="sxs-lookup"><span data-stu-id="2459e-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="2459e-114">Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="2459e-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="2459e-115">Zdecydowanie nazwy zestawu odbiornika dziennika</span><span class="sxs-lookup"><span data-stu-id="2459e-115">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="2459e-116">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="2459e-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2459e-117">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2459e-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2.  <span data-ttu-id="2459e-118">Kliknij przycisk **podpisywanie** kartę.</span><span class="sxs-lookup"><span data-stu-id="2459e-118">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="2459e-119">Wybierz **Podpisz zestaw** pole.</span><span class="sxs-lookup"><span data-stu-id="2459e-119">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="2459e-120">Wybierz  **\<nowy >** z **wybierz plik klucza o silnej nazwie** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="2459e-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="2459e-121">**Utwórz klucz silnej nazwy** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2459e-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="2459e-122">Podaj nazwę pliku klucza w **nazwę pliku klucza** pole.</span><span class="sxs-lookup"><span data-stu-id="2459e-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="2459e-123">Wprowadź hasło w **wprowadź hasło** i **Potwierdź hasło** pola.</span><span class="sxs-lookup"><span data-stu-id="2459e-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="2459e-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2459e-124">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="2459e-125">Ponownie skompiluj aplikację.</span><span class="sxs-lookup"><span data-stu-id="2459e-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="2459e-126">Dodanie detektora</span><span class="sxs-lookup"><span data-stu-id="2459e-126">Adding the Listener</span></span>  
 <span data-ttu-id="2459e-127">Teraz, że zestaw ma silną nazwą, należy określić silną nazwę odbiornika tak, aby `My.Application.Log` korzysta z odbiornikiem dziennika.</span><span class="sxs-lookup"><span data-stu-id="2459e-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="2459e-128">Format typu o silnej nazwie jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="2459e-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="2459e-129">\<Nazwa typu >, \<Nazwa zestawu >, \<numer wersji >, \<kultury >, \<silnej nazwy ></span><span class="sxs-lookup"><span data-stu-id="2459e-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="2459e-130">Aby określić silną nazwę odbiornika</span><span class="sxs-lookup"><span data-stu-id="2459e-130">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="2459e-131">Poniższy kod przedstawia sposób określić nazwę typu o silnej nazwie `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="2459e-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     <span data-ttu-id="2459e-132">Silnej nazwy typu zależy od projektu.</span><span class="sxs-lookup"><span data-stu-id="2459e-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="2459e-133">Za pomocą silnej nazwy, można dodawać przez odbiornik `My.Application.Log` kolekcji odbiornika dziennika.</span><span class="sxs-lookup"><span data-stu-id="2459e-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="2459e-134">Aby dodać odbiornika do My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="2459e-134">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="2459e-135">Kliknij prawym przyciskiem myszy w pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="2459e-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="2459e-136">—lub—</span><span class="sxs-lookup"><span data-stu-id="2459e-136">-or-</span></span>  
  
     <span data-ttu-id="2459e-137">W przypadku pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="2459e-137">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="2459e-138">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="2459e-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="2459e-139">Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2459e-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="2459e-140">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="2459e-140">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="2459e-141">Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" znajdujący się w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="2459e-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="2459e-142">`<sources>` Sekcji znajduje się w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="2459e-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="2459e-143">Dodaj ten element, aby `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="2459e-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="2459e-144">Znajdź `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="2459e-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="2459e-145">Dodaj ten element, do którego `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="2459e-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="2459e-146">Zmień wartość właściwości `SimpleLogStrongName` silną nazwę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="2459e-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2459e-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2459e-147">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="2459e-148">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="2459e-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="2459e-149">Instrukcje: Rejestruje wyjątki</span><span class="sxs-lookup"><span data-stu-id="2459e-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="2459e-150">Instrukcje: Zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="2459e-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="2459e-151">Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="2459e-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
