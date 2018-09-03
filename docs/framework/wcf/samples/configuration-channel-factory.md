---
title: Fabryka kanałów konfiguracji
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1f95356b0b473b297b36c7661c849589e9c0d6ef
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483739"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="1dcfd-102">Fabryka kanałów konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1dcfd-102">Configuration Channel Factory</span></span>
<span data-ttu-id="1dcfd-103">Ten przykład obejmuje użycie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="1dcfd-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umożliwia centralne zarządzanie Konfiguracja klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="1dcfd-105">Może to być również przydatne w scenariuszach, w których konfiguracja jest wybrane lub ulegnie zmianie po czas ładowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1dcfd-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="1dcfd-106">Demonstrates</span></span>  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a><span data-ttu-id="1dcfd-107">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="1dcfd-107">Discussion</span></span>  
 <span data-ttu-id="1dcfd-108">Ten przykład ilustruje sposób używania <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> można dodać plik konfiguracji określonej aplikacji klienta, bez konieczności używania domyślny plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>  
  
 <span data-ttu-id="1dcfd-109">Przykład obejmuje dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-109">The sample consists of two projects.</span></span> <span data-ttu-id="1dcfd-110">Pierwszy projekt jest prostą usługę uruchomioną na udzielenie odpowiedzi na komunikaty pochodzące od klientów.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="1dcfd-111">Drugi projekt to aplikacja kliencka, która tworzy dwa <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> obiektów przy użyciu <xref:System.Configuration.ExeConfigurationFileMap> Test.config pliku konfiguracji i są one używane do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="1dcfd-112">Obaj klienci komunikują się z usługą za pomocą konfiguracji określone w Test.config.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>  
  
 <span data-ttu-id="1dcfd-113">Poniższy kod dodaje plik konfiguracji niestandardowej do aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-113">The following code adds a custom configuration file to a client application.</span></span>  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1dcfd-114">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="1dcfd-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1dcfd-115">Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-115">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="1dcfd-116">Kliknij prawym przyciskiem myszy rozwiązanie ConfigurationChannelFactory (projekty, 2), a następnie wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="1dcfd-117">W **wspólne właściwości**, wybierz opcję **projekt startowy**, a następnie kliknij przycisk **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
4.  <span data-ttu-id="1dcfd-118">Przenieś **usługi** projektu na początku listy, o **akcji "Start"**, a następnie przenieść **klienta** projektu po **usługi**projektu, również mający **akcji "Start"**, więc **klienta** projektu jest wykonywany po **usługi** projektu.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>  
  
5.  <span data-ttu-id="1dcfd-119">Kliknij przycisk **OK**, a następnie naciśnij klawisz F5 (lub CTRL + F5) do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1dcfd-120">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1dcfd-121">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="1dcfd-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1dcfd-122">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1dcfd-123">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1dcfd-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
