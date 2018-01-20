---
title: "Uruchamianie przykładów programu Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 603a6dce17d527a3f14e408da19006509514df52
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="running-the-windows-communication-foundation-samples"></a><span data-ttu-id="ee82b-102">Uruchamianie przykładów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ee82b-102">Running the Windows Communication Foundation Samples</span></span>
<span data-ttu-id="ee82b-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Próbki mogą być uruchamiane w konfiguracji pojedynczego komputera lub między komputerami.</span><span class="sxs-lookup"><span data-stu-id="ee82b-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can be run in a single-machine or cross-machine configuration.</span></span> <span data-ttu-id="ee82b-104">Dostarczony, próbki są gotowe do uruchamiania na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ee82b-104">As supplied, the samples are ready for running on a single machine.</span></span> <span data-ttu-id="ee82b-105">W konfiguracji między komputerami należy zmodyfikować ustawienia pliku konfiguracji na próbkę.</span><span class="sxs-lookup"><span data-stu-id="ee82b-105">In a cross-machine configuration, it is necessary to modify a sample's configuration file settings.</span></span> <span data-ttu-id="ee82b-106">Poniższe procedury dotyczą sposobu uruchamiania próbkę w tym samym komputerze lub między komputerami konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="ee82b-106">The following procedures explain how to run a sample in same-machine and cross-machine configurations.</span></span> <span data-ttu-id="ee82b-107">Należy pamiętać, że zmiany w opisach usług hostowanych w Internet Information Services (IIS) i hostowanie Samoobsługowe próbek.</span><span class="sxs-lookup"><span data-stu-id="ee82b-107">Note that there are variations in the steps for services hosted in Internet Information Services (IIS) and the self-hosted samples.</span></span> <span data-ttu-id="ee82b-108">Większość przykładów są hostowane w usługach IIS; Zapoznaj się z informacjami readme próbki ustalenie, jak jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="ee82b-108">Most samples are hosted in IIS; see the sample readme information to determine how it is hosted.</span></span>  
  
 <span data-ttu-id="ee82b-109">Na [!INCLUDE[wv](../../../../includes/wv-md.md)], przykłady, które nie są obsługiwane w usługach IIS wymaga podwyższonego poziomu uprawnień, aby zarejestrować odbiornik przy użyciu składnika Http.sys.</span><span class="sxs-lookup"><span data-stu-id="ee82b-109">On [!INCLUDE[wv](../../../../includes/wv-md.md)], samples that are not hosted in IIS require elevated privileges to register a listener with Http.sys.</span></span> <span data-ttu-id="ee82b-110">Użyj Httpcfg.exe, aby zarejestrować adresy nasłuchiwania usługi przy użyciu konta, które usługa jest uruchomiona w obszarze, lub uruchom usługi z wiersza polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="ee82b-110">Use Httpcfg.exe to register the service's listening addresses with the account the service is running under, or launch the service from a command prompt running with administrator privileges.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee82b-111">Tworzenie lub z dowolnym z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbek, pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee82b-111">Before building or running any of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples, be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="ee82b-112">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="ee82b-112">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="ee82b-113">Jeśli usługa jest obsługiwana przez usługi IIS, upewnij się, że masz dostęp usługi przy użyciu przeglądarki wprowadź następujący adres: http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="ee82b-113">If the service is hosted by IIS, ensure that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="ee82b-114">Powinna być wyświetlana strona potwierdzenia w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ee82b-114">A confirmation page should be displayed in response.</span></span> <span data-ttu-id="ee82b-115">Jeśli nie zostanie wyświetlona strona potwierdzenia, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ee82b-115">If the confirmation page is not displayed, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
2.  <span data-ttu-id="ee82b-116">Jeśli usługa własnym jest obsługiwana, należy uruchomić Service.exe z \service\bin z folderu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="ee82b-116">If the service is self-hosted, run Service.exe from \service\bin, from under the language-specific folder.</span></span> <span data-ttu-id="ee82b-117">Działanie usługi jest wyświetlany w oknie konsoli usługi.</span><span class="sxs-lookup"><span data-stu-id="ee82b-117">Service activity is displayed on the service console window.</span></span>  
  
3.  <span data-ttu-id="ee82b-118">Uruchom Client.exe z \client\bin\\, z folderu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="ee82b-118">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="ee82b-119">Aktywność klienta jest wyświetlany w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="ee82b-119">Client activity is displayed on the client console window.</span></span>  
  
4.  <span data-ttu-id="ee82b-120">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ee82b-120">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="ee82b-121">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="ee82b-121">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="ee82b-122">Jeśli usługa jest obsługiwana w usługach IIS:</span><span class="sxs-lookup"><span data-stu-id="ee82b-122">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="ee82b-123">Na komputerze usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="ee82b-123">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="ee82b-124">Plik wsadowy dołączonego Setupvroot.bat [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) może służyć do tworzenia katalogu na dysku i katalog wirtualny.</span><span class="sxs-lookup"><span data-stu-id="ee82b-124">The batch file Setupvroot.bat included with [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="ee82b-125">Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="ee82b-125">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="ee82b-126">Upewnij się, obejmują pliki w katalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="ee82b-126">Ensure that you include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="ee82b-127">Aby uzyskać dostęp do usługi z komputera klienta przy użyciu przeglądarki testu.</span><span class="sxs-lookup"><span data-stu-id="ee82b-127">Test that you can access the service from the client machine using a browser.</span></span>  
  
     <span data-ttu-id="ee82b-128">Jeśli usługa jest samodzielnie hostowana:</span><span class="sxs-lookup"><span data-stu-id="ee82b-128">If the service is self-hosted:</span></span>  
  
    1.  <span data-ttu-id="ee82b-129">Na komputerze usługi należy utworzyć katalog do przechowywania plików usługi.</span><span class="sxs-lookup"><span data-stu-id="ee82b-129">On the service machine, create a directory to hold the service files.</span></span>  
  
    2.  <span data-ttu-id="ee82b-130">Skopiuj pliki programu usługi z folderu \service\bin\ w folderze danego języka maszyną usługi.</span><span class="sxs-lookup"><span data-stu-id="ee82b-130">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service machine.</span></span>  
  
    3.  <span data-ttu-id="ee82b-131">W pliku konfiguracji usługi Zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą.</span><span class="sxs-lookup"><span data-stu-id="ee82b-131">In the service configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="ee82b-132">Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="ee82b-132">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    4.  <span data-ttu-id="ee82b-133">Uruchom Service.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee82b-133">Launch Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="ee82b-134">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="ee82b-134">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
3.  <span data-ttu-id="ee82b-135">Ustaw adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ee82b-135">Set the endpoint address.</span></span>  
  
    1.  <span data-ttu-id="ee82b-136">Jeśli usługa nie jest uruchomiona w ramach konta domeny, otwórz plik konfiguracji klienta i zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą.</span><span class="sxs-lookup"><span data-stu-id="ee82b-136">If the service is not running under a domain account, open the client configuration file and change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="ee82b-137">Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="ee82b-137">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    2.  <span data-ttu-id="ee82b-138">Jeśli usługa jest uruchomiona w ramach konta domeny, należy ponownie wygenerować konfiguracji klienta, uruchamiając Svcutil.exe z usługą.</span><span class="sxs-lookup"><span data-stu-id="ee82b-138">If the service is running under a domain account, regenerate the client configuration by running Svcutil.exe against the service.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ee82b-139">Uruchamianie Svcutil.exe, zobacz [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee82b-139"> running Svcutil.exe, see [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="ee82b-140">Użyj wygenerowanego pliku zamiast pliku konfiguracji w próbce.</span><span class="sxs-lookup"><span data-stu-id="ee82b-140">Use the generated file instead of the configuration file in the sample.</span></span> <span data-ttu-id="ee82b-141">Wygenerowano plik konfiguracyjny zawiera informacje o dodatkowych tożsamości i zawiera wszystkie ustawienia niezbędne do połączenia z punktem końcowym usługi, nawet jeśli są one ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="ee82b-141">The generated configuration file has additional identity information, and contains all settings necessary to connect to the service endpoint even though they are the default settings.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ee82b-142">informacje o tożsamości, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).</span><span class="sxs-lookup"><span data-stu-id="ee82b-142"> identity information, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).</span></span>  
  
4.  <span data-ttu-id="ee82b-143">Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee82b-143">On the client machine, launch Client.exe from a command prompt.</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="ee82b-144">Aby debugować usługi</span><span class="sxs-lookup"><span data-stu-id="ee82b-144">To debug a service</span></span>  
  
1.  <span data-ttu-id="ee82b-145">Tworzenie przy użyciu rozwiązania (klient i usługa) **kompilacji** menu lub CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="ee82b-145">Build the solution (both client and service) using the **Build** menu or CTRL+SHIFT+B.</span></span>  
  
2.  <span data-ttu-id="ee82b-146">Jeśli usługa jest obsługiwana w usługach IIS:</span><span class="sxs-lookup"><span data-stu-id="ee82b-146">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="ee82b-147">Aktywowanie usługi, wprowadzając adres http://localhost/servicemodelsamples/service.svc przy użyciu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="ee82b-147">Activate the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
    2.  <span data-ttu-id="ee82b-148">W rozwiązaniu, wybierz **debugowania** menu i **dołączyć do procesu** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="ee82b-148">In the solution, choose the **Debug** menu and the **Attach to Process** menu item.</span></span>  
  
    3.  <span data-ttu-id="ee82b-149">Wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="ee82b-149">Select the **Show processes from all users** check box.</span></span>  
  
    4.  <span data-ttu-id="ee82b-150">Wybierz proces roboczy hosta W3wp.exe debugowania (Wybierz ASPNet_wp.exe w systemie Windows XP).</span><span class="sxs-lookup"><span data-stu-id="ee82b-150">Select the host worker process W3wp.exe to debug (select ASPNet_wp.exe on Windows XP).</span></span>  
  
3.  <span data-ttu-id="ee82b-151">Teraz można ustawić punktów przerwania w kodzie usługi i włączyć punkty przerwania w wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ee82b-151">You can now set breakpoints in the service code and enable breakpoints on exceptions.</span></span>  
  
4.  <span data-ttu-id="ee82b-152">Kliknij prawym przyciskiem myszy element projektu klienta, a następnie wybierz pozycję **debugowania**, **Start nowe wystąpienie**.</span><span class="sxs-lookup"><span data-stu-id="ee82b-152">Right-click the client project item and choose **Debug**, **Start new instance**.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ee82b-153">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="ee82b-153">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="ee82b-154">Jeśli usługa jest obsługiwana w usługach IIS ze względów bezpieczeństwa, Usuń katalog wirtualny definicji i uprawnienia w ramach kroków konfiguracji, po zakończeniu pracy z próbek.</span><span class="sxs-lookup"><span data-stu-id="ee82b-154">If the service is hosted in IIS for security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee82b-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee82b-155">See Also</span></span>  
 [<span data-ttu-id="ee82b-156">Kompilowanie przykładów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ee82b-156">Building the Windows Communication Foundation Samples</span></span>](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [<span data-ttu-id="ee82b-157">Uruchomione z próbek w grupie roboczej i na komputerach</span><span class="sxs-lookup"><span data-stu-id="ee82b-157">Running the Samples in a Workgroup and Across Machines</span></span>](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [<span data-ttu-id="ee82b-158">Porady dotyczące rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="ee82b-158">Troubleshooting Tips</span></span>](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
