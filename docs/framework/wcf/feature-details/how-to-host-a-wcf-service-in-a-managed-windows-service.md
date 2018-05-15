---
title: 'Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: c6c3e057fd07569d462f1bf25d1c283e42024a8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="50cd4-102">Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows</span><span class="sxs-lookup"><span data-stu-id="50cd4-102">How to: Host a WCF Service in a Managed Windows Service</span></span>
<span data-ttu-id="50cd4-103">W tym temacie przedstawiono podstawowe czynności wymagane do tworzenia usług Windows Communication Foundation (WCF), obsługiwanej przez usługę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="50cd4-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="50cd4-104">Scenariusz jest włączone przez usługę systemu Windows zarządzany hosting opcję długotrwałe usługi WCF hostowanej poza Internet Information Services (IIS) w bezpiecznym środowisku, który nie jest aktywowany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="50cd4-104">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="50cd4-105">Okres istnienia usługi steruje zamiast tego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="50cd4-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="50cd4-106">Ta opcja obsługi jest dostępna we wszystkich wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="50cd4-106">This hosting option is available in all versions of Windows.</span></span>  
  
 <span data-ttu-id="50cd4-107">Usługi systemu Windows można zarządzać za pomocą Microsoft.ManagementConsole.SnapIn w konsoli Microsoft Management Console (MMC) i można skonfigurować tak, aby uruchamiała się automatycznie, gdy system jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="50cd4-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="50cd4-108">Ta opcja hostingu składa się z rejestrowania domeny aplikacji (AppDomain), który jest hostem usługi WCF jako zarządzanych usług systemu Windows tak, aby okres istnienia procesu usługi jest kontrolowany przez Menedżera sterowania usługami (SCM) dla usług systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="50cd4-108">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>  
  
 <span data-ttu-id="50cd4-109">Kod usługi zawiera implementacji usługi, kontrakt usługi, klasa usługi systemu Windows i klasę Instalatora.</span><span class="sxs-lookup"><span data-stu-id="50cd4-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="50cd4-110">Klasa implementacji usługi, `CalculatorService`, to usługa WCF.</span><span class="sxs-lookup"><span data-stu-id="50cd4-110">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="50cd4-111">`CalculatorWindowsService` To usługa systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="50cd4-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="50cd4-112">Aby zakwalifikować się jako usługa systemu Windows, dziedziczy po klasie `ServiceBase` i implementuje `OnStart` i `OnStop` metody.</span><span class="sxs-lookup"><span data-stu-id="50cd4-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="50cd4-113">W `OnStart`, <xref:System.ServiceModel.ServiceHost> jest tworzona dla `CalculatorService` wpisz i otworzyć.</span><span class="sxs-lookup"><span data-stu-id="50cd4-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="50cd4-114">W `OnStop`, że usługa jest zatrzymana i usunięty.</span><span class="sxs-lookup"><span data-stu-id="50cd4-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="50cd4-115">Host jest również odpowiedzialność za zapewnienie adres podstawowy hosta usługi, który został skonfigurowany w ustawieniach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50cd4-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="50cd4-116">Instalator klasy, która dziedziczy <xref:System.Configuration.Install.Installer>, pozwala programowi zainstalowania przez narzędzie Installutil.exe jako usługa systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="50cd4-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>  
  
### <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="50cd4-117">Konstruowania usługi i podaj kod hostingu</span><span class="sxs-lookup"><span data-stu-id="50cd4-117">Construct the service and provide the hosting code</span></span>  
  
1.  <span data-ttu-id="50cd4-118">Utwórz nowy projekt aplikacji konsoli w usłudze Visual Studio o nazwie "Usługa".</span><span class="sxs-lookup"><span data-stu-id="50cd4-118">Create a new Visual Studio Console Application project called "Service".</span></span>  
  
2.  <span data-ttu-id="50cd4-119">Zmień nazwę pliku Program.cs Service.cs.</span><span class="sxs-lookup"><span data-stu-id="50cd4-119">Rename Program.cs to Service.cs.</span></span>  
  
3.  <span data-ttu-id="50cd4-120">Zmienić przestrzeni nazw do Microsoft.ServiceModel.Samples.</span><span class="sxs-lookup"><span data-stu-id="50cd4-120">Change the namespace to Microsoft.ServiceModel.Samples.</span></span>  
  
4.  <span data-ttu-id="50cd4-121">Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="50cd4-121">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="50cd4-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="50cd4-122">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="50cd4-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="50cd4-123">System.ServiceProcess.dll</span></span>  
  
    -   <span data-ttu-id="50cd4-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="50cd4-124">System.Configuration.Install.dll</span></span>  
  
5.  <span data-ttu-id="50cd4-125">Dodaj następujące instrukcje using do Service.cs.</span><span class="sxs-lookup"><span data-stu-id="50cd4-125">Add the following using statements to Service.cs.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]  
  
6.  <span data-ttu-id="50cd4-126">Zdefiniuj `ICalculator` kontraktu usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="50cd4-126">Define the `ICalculator` service contract as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]  
  
7.  <span data-ttu-id="50cd4-127">Implementowanie kontraktu usługi w klasie o nazwie `CalculatorService` jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="50cd4-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]  
  
8.  <span data-ttu-id="50cd4-128">Utwórz nową klasę o nazwie `CalculatorWindowsService` dziedziczący po <xref:System.ServiceProcess.ServiceBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="50cd4-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="50cd4-129">Dodawanie zmiennej lokalnej o nazwie `serviceHost` do odwołania <xref:System.ServiceModel.ServiceHost> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="50cd4-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="50cd4-130">Zdefiniuj `Main` metodę, która wywołuje `ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="50cd4-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]  
  
9. <span data-ttu-id="50cd4-131">Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metody tworzenia i otwierania nowych <xref:System.ServiceModel.ServiceHost> wystąpienie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="50cd4-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]  
  
10. <span data-ttu-id="50cd4-132">Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda zamknięcia <xref:System.ServiceModel.ServiceHost> jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="50cd4-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]  
  
11. <span data-ttu-id="50cd4-133">Utwórz nową klasę o nazwie `ProjectInstaller` dziedziczący po <xref:System.Configuration.Install.Installer> i który jest oznaczony atrybutem <xref:System.ComponentModel.RunInstallerAttribute> ustawioną `true`.</span><span class="sxs-lookup"><span data-stu-id="50cd4-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="50cd4-134">Dzięki temu można zainstalować przez narzędzie Installutil.exe usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="50cd4-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]  
  
12. <span data-ttu-id="50cd4-135">Usuń `Service` klasy, który został wygenerowany podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="50cd4-135">Remove the `Service` class that was generated when you created the project.</span></span>  
  
13. <span data-ttu-id="50cd4-136">Dodaj plik konfiguracji aplikacji do projektu.</span><span class="sxs-lookup"><span data-stu-id="50cd4-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="50cd4-137">Zastąp zawartość pliku o następującej konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="50cd4-137">Replace the contents of the file with the following configuration XML.</span></span>  
  
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
  
     <span data-ttu-id="50cd4-138">Kliknij prawym przyciskiem myszy w pliku App.config **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="50cd4-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="50cd4-139">W obszarze **Kopiuj do katalogu wyjściowego** wybierz **Kopiuj, jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="50cd4-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>  
  
     <span data-ttu-id="50cd4-140">W tym przykładzie jawnie określa punkty końcowe w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="50cd4-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="50cd4-141">Jeśli nie dodawaj żadnych punktów końcowych do usługi, środowisko uruchomieniowe dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="50cd4-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="50cd4-142">W tym przykładzie ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ustawioną `true`, usługa ma również publikowanie metadanych włączone.</span><span class="sxs-lookup"><span data-stu-id="50cd4-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="50cd4-143">Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="50cd4-143">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
### <a name="install-and-run-the-service"></a><span data-ttu-id="50cd4-144">Zainstaluj i uruchom usługę</span><span class="sxs-lookup"><span data-stu-id="50cd4-144">Install and run the service</span></span>  
  
1.  <span data-ttu-id="50cd4-145">Utworzenie rozwiązania do tworzenia `Service.exe` pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="50cd4-145">Build the solution to create the `Service.exe` executable.</span></span>  
  
2.  <span data-ttu-id="50cd4-146">Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz polecenia i przejdź do katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="50cd4-146">Open the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the project directory.</span></span> <span data-ttu-id="50cd4-147">Typ `installutil bin\service.exe` w wierszu polecenia, aby zainstalować usługę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="50cd4-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50cd4-148">Jeśli nie używasz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz polecenia, upewnij się, że `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` katalog znajduje się w ścieżce systemowej.</span><span class="sxs-lookup"><span data-stu-id="50cd4-148">If you do not use the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt, make sure that the `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` directory is in the system path.</span></span>  
  
     <span data-ttu-id="50cd4-149">Typ `services.msc` w wierszu polecenia można uzyskać dostępu do Menedżera sterowania usługami (SCM).</span><span class="sxs-lookup"><span data-stu-id="50cd4-149">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="50cd4-150">Usługa systemu Windows powinna pojawić się w usługach jako "WCFWindowsServiceSample".</span><span class="sxs-lookup"><span data-stu-id="50cd4-150">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="50cd4-151">Usługi WCF może odpowiadać tylko na klientach, jeśli usługa systemu Windows jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="50cd4-151">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="50cd4-152">Aby uruchomić usługę, kliknij prawym przyciskiem myszy go w SCM i wybierz polecenie "Start" lub typu **net start WCFWindowsServiceSample** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="50cd4-152">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>  
  
3.  <span data-ttu-id="50cd4-153">Jeśli wprowadzisz zmiany do usługi należy najpierw zatrzymaj ją i go odinstalować.</span><span class="sxs-lookup"><span data-stu-id="50cd4-153">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="50cd4-154">Aby zatrzymać usługę, kliknij prawym przyciskiem myszy usługi w SCM i wybierz pozycję stop (Zatrzymaj)", lub **typu net stop WCFWindowsServiceSample** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="50cd4-154">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="50cd4-155">Należy pamiętać, że jeśli zatrzymać usługi systemu Windows, a następnie uruchom klienta, <xref:System.ServiceModel.EndpointNotFoundException> wyjątek występuje, gdy klient próbuje uzyskać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="50cd4-155">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="50cd4-156">Aby odinstalować typu usługi systemu Windows **installutil /u bin\service.exe** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="50cd4-156">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50cd4-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="50cd4-157">Example</span></span>  
 <span data-ttu-id="50cd4-158">Poniżej znajduje się pełna lista kod używany w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="50cd4-158">The following is a complete listing of the code used by this topic.</span></span>  
  
 [!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
 [!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]  
  
 <span data-ttu-id="50cd4-159">Podobnie jak opcji "Własnym hostingu" Usługa systemu Windows obsługującego środowisko wymaga, że niektóre hostingu kodu można zapisywać w ramach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50cd4-159">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="50cd4-160">Usługa jest zaimplementowany jako aplikacji konsoli i zawiera własną hostingu kod.</span><span class="sxs-lookup"><span data-stu-id="50cd4-160">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="50cd4-161">W innych środowiskach hostingu, na przykład w Internet informacji Services (IIS), obsługa usługi aktywacji procesów systemu Windows (WAS) nie jest konieczne deweloperom pisanie hosting kodu.</span><span class="sxs-lookup"><span data-stu-id="50cd4-161">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50cd4-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50cd4-162">See Also</span></span>  
 [<span data-ttu-id="50cd4-163">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="50cd4-163">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="50cd4-164">Hosting w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="50cd4-164">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 [<span data-ttu-id="50cd4-165">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="50cd4-165">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="50cd4-166">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="50cd4-166">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
