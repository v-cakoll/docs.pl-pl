---
title: 'Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows'
description: Dowiedz się, jak utworzyć usługę WCF hostowaną przez usługę systemu Windows. Ta opcja hostingu jest dostępna we wszystkich wersjach systemu Windows.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: 4e07aa7aac82fae5cfd1bfc759ef724cf87a873a
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246939"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="86696-104">Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows</span><span class="sxs-lookup"><span data-stu-id="86696-104">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="86696-105">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF) hostowanej przez usługę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="86696-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="86696-106">Ten scenariusz jest włączany przez opcję hostingu zarządzanej usługi systemu Windows, która jest długotrwałą usługą WCF hostowaną poza Internet Information Services (IIS) w bezpiecznym środowisku, które nie jest uaktywniane przez komunikat.</span><span class="sxs-lookup"><span data-stu-id="86696-106">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="86696-107">Okres istnienia usługi jest kontrolowany przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="86696-107">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="86696-108">Ta opcja hostingu jest dostępna we wszystkich wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="86696-108">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="86696-109">Usługami systemu Windows można zarządzać za pomocą przystawki Microsoft. ManagementConsole. SnapIn w programie Microsoft Management Console (MMC) i można ją skonfigurować do automatycznego uruchamiania podczas uruchamiania systemu.</span><span class="sxs-lookup"><span data-stu-id="86696-109">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="86696-110">Ta opcja hostingu polega na zarejestrowaniu domeny aplikacji (AppDomain), która hostuje usługę WCF jako usługę zarządzaną systemu Windows, dzięki czemu okres istnienia usługi jest kontrolowany przez menedżera kontroli usług (SCM) dla usług systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="86696-110">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="86696-111">Kod usługi zawiera implementację usługi kontraktu usługi, klasy usługi systemu Windows i klasy Instalatora.</span><span class="sxs-lookup"><span data-stu-id="86696-111">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="86696-112">Klasa implementacji usługi, `CalculatorService` , jest usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="86696-112">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="86696-113">`CalculatorWindowsService`Jest to usługa systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="86696-113">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="86696-114">Aby można było zakwalifikować jako usługę systemu Windows, Klasa dziedziczy z `ServiceBase` i `OnStart` implementuje `OnStop` metody i.</span><span class="sxs-lookup"><span data-stu-id="86696-114">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="86696-115">W programie `OnStart` <xref:System.ServiceModel.ServiceHost> jest tworzony dla `CalculatorService` typu i otwarty.</span><span class="sxs-lookup"><span data-stu-id="86696-115">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="86696-116">W programie `OnStop` Usługa zostanie zatrzymana i usunięta.</span><span class="sxs-lookup"><span data-stu-id="86696-116">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="86696-117">Host jest również odpowiedzialny za podanie adresu podstawowego dla hosta usługi, który został skonfigurowany w ustawieniach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86696-117">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="86696-118">Klasa Instalatora, która dziedziczy po <xref:System.Configuration.Install.Installer> , umożliwia programowi zainstalowanie jako usługę systemu Windows za pomocą narzędzia Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="86696-118">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="86696-119">Konstruowanie usługi i dostarczanie kodu hostingu</span><span class="sxs-lookup"><span data-stu-id="86696-119">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="86696-120">Utwórz nowy projekt **aplikacji konsoli** programu Visual Studio o nazwie **Usługa**.</span><span class="sxs-lookup"><span data-stu-id="86696-120">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="86696-121">Zmień nazwę Program.cs na Service.cs.</span><span class="sxs-lookup"><span data-stu-id="86696-121">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="86696-122">Zmień przestrzeń nazw na `Microsoft.ServiceModel.Samples` .</span><span class="sxs-lookup"><span data-stu-id="86696-122">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="86696-123">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="86696-123">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="86696-124">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="86696-124">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="86696-125">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="86696-125">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="86696-126">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="86696-126">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="86696-127">Dodaj następujące instrukcje using do Service.cs.</span><span class="sxs-lookup"><span data-stu-id="86696-127">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="86696-128">Zdefiniuj `ICalculator` kontrakt usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="86696-128">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="86696-129">Zaimplementuj kontrakt usługi w klasie o nazwie `CalculatorService` , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="86696-129">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="86696-130">Utwórz nową klasę o nazwie `CalculatorWindowsService` , która dziedziczy z <xref:System.ServiceProcess.ServiceBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="86696-130">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="86696-131">Dodaj zmienną lokalną o nazwie, `serviceHost` Aby odwołać się do <xref:System.ServiceModel.ServiceHost> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="86696-131">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="86696-132">Zdefiniuj `Main` metodę, która wywołuje`ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="86696-132">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="86696-133">Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metodę, tworząc i otwierając nowe <xref:System.ServiceModel.ServiceHost> wystąpienie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="86696-133">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="86696-134">Zastąp <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodę zamykającą, <xref:System.ServiceModel.ServiceHost> jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="86696-134">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="86696-135">Utwórz nową klasę o nazwie `ProjectInstaller` , która dziedziczy z <xref:System.Configuration.Install.Installer> i która jest oznaczona z <xref:System.ComponentModel.RunInstallerAttribute> ustawioną na `true` .</span><span class="sxs-lookup"><span data-stu-id="86696-135">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="86696-136">Umożliwia to zainstalowanie usługi systemu Windows za pomocą narzędzia Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="86696-136">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="86696-137">Usuń `Service` klasę, która została wygenerowana podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="86696-137">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="86696-138">Dodaj plik konfiguracji aplikacji do projektu.</span><span class="sxs-lookup"><span data-stu-id="86696-138">Add an application configuration file to the project.</span></span> <span data-ttu-id="86696-139">Zastąp zawartość pliku następującym kodem XML konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="86696-139">Replace the contents of the file with the following configuration XML.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.serviceModel>    <services>
          <!-- This section is optional with the new configuration model
               introduced in .NET Framework 4. -->
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"
                   behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
            <endpoint address=""
                      binding="wsHttpBinding"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />
          </service>
        </services>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceMetadata httpGetEnabled="true"/>
              <serviceDebug includeExceptionDetailInFaults="False"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>
      </system.serviceModel>
    </configuration>
    ```

     <span data-ttu-id="86696-140">Kliknij prawym przyciskiem myszy plik App.config w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="86696-140">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="86696-141">W obszarze **Kopiuj do katalogu wyjściowego** wybierz opcję **Kopiuj, jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="86696-141">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="86696-142">Ten przykład jawnie określa punkty końcowe w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="86696-142">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="86696-143">Jeśli nie dodasz żadnych punktów końcowych do usługi, środowisko uruchomieniowe doda domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="86696-143">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="86696-144">W tym przykładzie, ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ustawiony na `true` , usługa ma także włączone metadane publikacji.</span><span class="sxs-lookup"><span data-stu-id="86696-144">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="86696-145">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="86696-145">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="86696-146">Instalowanie i uruchamianie usługi</span><span class="sxs-lookup"><span data-stu-id="86696-146">Install and run the service</span></span>

1. <span data-ttu-id="86696-147">Skompiluj rozwiązanie, aby utworzyć `Service.exe` plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="86696-147">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="86696-148">Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio i przejdź do katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="86696-148">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="86696-149">Wpisz `installutil bin\service.exe` w wierszu polecenia, aby zainstalować usługę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="86696-149">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="86696-150">Wpisz `services.msc` w wierszu polecenia, aby uzyskać dostęp do Menedżera sterowania usługami (SCM).</span><span class="sxs-lookup"><span data-stu-id="86696-150">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="86696-151">Usługa systemu Windows powinna być wyświetlana w usługach jako "WCFWindowsServiceSample".</span><span class="sxs-lookup"><span data-stu-id="86696-151">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="86696-152">Usługa WCF może odpowiedzieć tylko na klientów, jeśli usługa systemu Windows jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="86696-152">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="86696-153">Aby uruchomić usługę, kliknij ją prawym przyciskiem myszy w SCM i wybierz polecenie "Start" lub wpisz **net start WCFWindowsServiceSample** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="86696-153">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="86696-154">Jeśli wprowadzisz zmiany w usłudze, musisz je najpierw zatrzymać i odinstalować.</span><span class="sxs-lookup"><span data-stu-id="86696-154">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="86696-155">Aby zatrzymać usługę, kliknij prawym przyciskiem myszy usługę w SCM i wybierz pozycję "Zatrzymaj" lub **wpisz net stop WCFWindowsServiceSample** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="86696-155">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="86696-156">Należy pamiętać, że w przypadku zatrzymania usługi systemu Windows, a następnie uruchomienia klienta, <xref:System.ServiceModel.EndpointNotFoundException> wyjątek występuje, gdy klient próbuje uzyskać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="86696-156">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="86696-157">Aby odinstalować typ usługi systemu Windows **Installutil/u bin\service.exe** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="86696-157">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="86696-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="86696-158">Example</span></span>

<span data-ttu-id="86696-159">Poniżej znajduje się kompletna lista kodu używanego w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="86696-159">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="86696-160">Podobnie jak w przypadku opcji "samohosting" środowisko hostingu usług systemu Windows wymaga, aby część kodu hostingu była zapisywana jako część aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86696-160">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="86696-161">Usługa jest zaimplementowana jako Aplikacja konsolowa i zawiera swój własny kod hostingu.</span><span class="sxs-lookup"><span data-stu-id="86696-161">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="86696-162">W innych środowiskach hostingu, takich jak usługa aktywacji procesów systemu Windows (WAS) w programie Internet Information Services (IIS), deweloperzy nie muszą pisać kodu hostingu.</span><span class="sxs-lookup"><span data-stu-id="86696-162">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="86696-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86696-163">See also</span></span>

- [<span data-ttu-id="86696-164">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="86696-164">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="86696-165">Hosting w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="86696-165">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)
- [<span data-ttu-id="86696-166">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="86696-166">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="86696-167">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="86696-167">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
