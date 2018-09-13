---
title: 'Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: edbc67ddf20eee6ebbe9091faa43bc1de91809d2
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705443"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="dba22-102">Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dba22-102">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="dba22-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF), która jest hostowana przez usługę Windows.</span><span class="sxs-lookup"><span data-stu-id="dba22-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="dba22-104">Scenariusz jest włączone przez usługę Windows zarządzanego hostingu opcję długotrwałych usługi WCF hostowane poza Internet Information Services (IIS) w bezpiecznym środowisku, który nie jest aktywowany komunikat o.</span><span class="sxs-lookup"><span data-stu-id="dba22-104">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="dba22-105">Okres istnienia usługi steruje zamiast tego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dba22-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="dba22-106">Ta opcja hostingu jest dostępny we wszystkich wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dba22-106">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="dba22-107">Usługi Windows można zarządzać za pomocą Microsoft.ManagementConsole.SnapIn w konsoli Microsoft Management Console (MMC) i można skonfigurować, aby uruchamiała się automatycznie, gdy system jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="dba22-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="dba22-108">Ta opcja hostingu składa się z rejestracji domeny aplikacji (AppDomain), który jest hostem usługi WCF jako usługa zarządzana Windows tak, że okres istnienia procesu usługi jest kontrolowany przez Menedżera sterowania usługami (SCM) dla usług Windows.</span><span class="sxs-lookup"><span data-stu-id="dba22-108">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="dba22-109">Kod usługi obejmuje z implementacją kontraktu usługi, usługa Windows klasy, a Instalator usługi.</span><span class="sxs-lookup"><span data-stu-id="dba22-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="dba22-110">Klasa implementacji usługi, `CalculatorService`, to usługa WCF.</span><span class="sxs-lookup"><span data-stu-id="dba22-110">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="dba22-111">`CalculatorWindowsService` Usługa Windows.</span><span class="sxs-lookup"><span data-stu-id="dba22-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="dba22-112">Aby zakwalifikować się jako usługa Windows, klasa dziedziczy `ServiceBase` i implementuje `OnStart` i `OnStop` metody.</span><span class="sxs-lookup"><span data-stu-id="dba22-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="dba22-113">W `OnStart`, <xref:System.ServiceModel.ServiceHost> jest tworzona dla `CalculatorService` wpisz i otwarty.</span><span class="sxs-lookup"><span data-stu-id="dba22-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="dba22-114">W `OnStop`, usługa jest zatrzymany i usunięty.</span><span class="sxs-lookup"><span data-stu-id="dba22-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="dba22-115">Host jest również odpowiedzialny za zapewnienie adres podstawowy host usługi, który został skonfigurowany w ustawieniach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dba22-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="dba22-116">Klasa Instalatora, która dziedziczy z <xref:System.Configuration.Install.Installer>, pozwala programowi na narzędzie Installutil.exe instaluje jako usługę Windows.</span><span class="sxs-lookup"><span data-stu-id="dba22-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="dba22-117">Utworzyć usługę i podaj kod hostingu</span><span class="sxs-lookup"><span data-stu-id="dba22-117">Construct the service and provide the hosting code</span></span>

1.  <span data-ttu-id="dba22-118">Tworzenie nowego programu Visual Studio **aplikacja Konsolowa** projekt o nazwie **usługi**.</span><span class="sxs-lookup"><span data-stu-id="dba22-118">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2.  <span data-ttu-id="dba22-119">Zmień nazwę pliku Program.cs Service.cs.</span><span class="sxs-lookup"><span data-stu-id="dba22-119">Rename Program.cs to Service.cs.</span></span>

3.  <span data-ttu-id="dba22-120">Zmień przestrzeń nazw w celu `Microsoft.ServiceModel.Samples`.</span><span class="sxs-lookup"><span data-stu-id="dba22-120">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4.  <span data-ttu-id="dba22-121">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="dba22-121">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="dba22-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="dba22-122">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="dba22-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="dba22-123">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="dba22-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="dba22-124">System.Configuration.Install.dll</span></span>

5.  <span data-ttu-id="dba22-125">Dodaj następujące instrukcje using do Service.cs.</span><span class="sxs-lookup"><span data-stu-id="dba22-125">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6.  <span data-ttu-id="dba22-126">Zdefiniuj `ICalculator` kontraktu usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="dba22-126">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7.  <span data-ttu-id="dba22-127">Implementowanie kontraktu usługi w klasie o nazwie `CalculatorService` jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="dba22-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8.  <span data-ttu-id="dba22-128">Utwórz nową klasę o nazwie `CalculatorWindowsService` tej, która dziedziczy <xref:System.ServiceProcess.ServiceBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="dba22-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="dba22-129">Dodawanie zmiennej lokalnej o nazwie `serviceHost` do odwołania <xref:System.ServiceModel.ServiceHost> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="dba22-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="dba22-130">Zdefiniuj `Main` metodę, która wywołuje `ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="dba22-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="dba22-131">Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metody tworzenia i otwierania nowych <xref:System.ServiceModel.ServiceHost> wystąpienia tak jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="dba22-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="dba22-132">Zastąp <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda zamknięcia <xref:System.ServiceModel.ServiceHost> jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="dba22-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="dba22-133">Utwórz nową klasę o nazwie `ProjectInstaller` tej, która dziedziczy <xref:System.Configuration.Install.Installer> , oznaczony za pomocą <xref:System.ComponentModel.RunInstallerAttribute> równa `true`.</span><span class="sxs-lookup"><span data-stu-id="dba22-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="dba22-134">Dzięki temu usługa Windows do zainstalowania przez narzędzie Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="dba22-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="dba22-135">Usuń `Service` klasy, który został wygenerowany podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dba22-135">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="dba22-136">Dodaj plik konfiguracji aplikacji do projektu.</span><span class="sxs-lookup"><span data-stu-id="dba22-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="dba22-137">Zastąp zawartość pliku o następującej konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="dba22-137">Replace the contents of the file with the following configuration XML.</span></span>

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

     <span data-ttu-id="dba22-138">Kliknij prawym przyciskiem myszy pliku App.config w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="dba22-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="dba22-139">W obszarze **Kopiuj do katalogu wyjściowego** wybierz **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="dba22-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="dba22-140">Ten przykład jawnie określa punkty końcowe w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dba22-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="dba22-141">Jeśli nie dodasz żadnych punktów końcowych do usługi, środowiska uruchomieniowego dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="dba22-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="dba22-142">W tym przykładzie ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> równa `true`, usługi ma także publikowanie metadanych włączone.</span><span class="sxs-lookup"><span data-stu-id="dba22-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="dba22-143">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="dba22-143">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="dba22-144">Zainstaluj i uruchom usługę</span><span class="sxs-lookup"><span data-stu-id="dba22-144">Install and run the service</span></span>

1.  <span data-ttu-id="dba22-145">Kompiluj rozwiązanie, aby utworzyć `Service.exe` pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="dba22-145">Build the solution to create the `Service.exe` executable.</span></span>

2.  <span data-ttu-id="dba22-146">Otwórz wiersz polecenia dla deweloperów programu Visual Studio i przejdź do katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="dba22-146">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="dba22-147">Typ `installutil bin\service.exe` w wierszu polecenia, aby zainstalować usługę Windows.</span><span class="sxs-lookup"><span data-stu-id="dba22-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="dba22-148">Typ `services.msc` na dostęp do Menedżera sterowania usługami (SCM), w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="dba22-148">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="dba22-149">Usługa Windows widoczny na usługi jako "WCFWindowsServiceSample".</span><span class="sxs-lookup"><span data-stu-id="dba22-149">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="dba22-150">Usługi WCF tylko może odpowiadać na klientach, jeśli usługa Windows jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="dba22-150">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="dba22-151">Aby uruchomić usługę, kliknij prawym przyciskiem myszy go w funkcji SCM i wybierz opcję "Start" lub typu **net start WCFWindowsServiceSample** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="dba22-151">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3.  <span data-ttu-id="dba22-152">Jeśli wprowadzisz zmiany w usłudze możesz zatrzymać go i jego odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="dba22-152">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="dba22-153">Aby zatrzymać usługę, kliknij prawym przyciskiem myszy usługę, w Menedżer sterowania usługami i wybierz opcję "Zatrzymaj" lub **typu net stop WCFWindowsServiceSample** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="dba22-153">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="dba22-154">Należy pamiętać, że jeśli Zatrzymaj usługę Windows, a następnie z klientem, <xref:System.ServiceModel.EndpointNotFoundException> wystąpi wyjątek, gdy klient próbuje uzyskać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="dba22-154">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="dba22-155">Aby odinstalować typ usługi Windows **installutil /u bin\service.exe** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="dba22-155">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="dba22-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="dba22-156">Example</span></span>

<span data-ttu-id="dba22-157">Poniżej przedstawiono pełną listę kod używany w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="dba22-157">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="dba22-158">Podobnie jak opcji "Własnym hostingu" usługi Windows Środowisko hostingu wymaga, że jakiś kod hostingu zapisywane jako część aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dba22-158">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="dba22-159">Ta usługa jest implementowany jako aplikację konsolową w języku i zawiera swój własny kod hostingu.</span><span class="sxs-lookup"><span data-stu-id="dba22-159">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="dba22-160">W innych środowiskach hostingu, takich jak Windows Process Activation Service (WAS) hostingu w Internet Information Services (IIS), nie jest konieczne dla deweloperów napisać kod hostingu.</span><span class="sxs-lookup"><span data-stu-id="dba22-160">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="dba22-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dba22-161">See Also</span></span>

- [<span data-ttu-id="dba22-162">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dba22-162">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="dba22-163">Hosting w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="dba22-163">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [<span data-ttu-id="dba22-164">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="dba22-164">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="dba22-165">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="dba22-165">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)