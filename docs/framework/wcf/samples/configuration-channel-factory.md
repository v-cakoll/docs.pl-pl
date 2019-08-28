---
title: Fabryka kanałów konfiguracji
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1b74c15599ebc932a2a0ed46d646b54bec986794
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045655"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="d91c0-102">Fabryka kanałów konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d91c0-102">Configuration Channel Factory</span></span>
<span data-ttu-id="d91c0-103">Ten przykład obejmuje użycie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="d91c0-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="d91c0-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umożliwia centralne zarządzanie konfiguracją klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="d91c0-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="d91c0-105">Może to być również przydatne w scenariuszach, w których konfiguracja jest wybierana lub zmieniana po upływie czasu ładowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d91c0-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d91c0-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="d91c0-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="d91c0-107">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="d91c0-107">Discussion</span></span>
 <span data-ttu-id="d91c0-108">Ten przykład pokazuje, jak używać <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> do dodawania określonego pliku konfiguracji do aplikacji klienckiej bez konieczności używania domyślnego pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d91c0-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="d91c0-109">Przykład składa się z dwóch projektów.</span><span class="sxs-lookup"><span data-stu-id="d91c0-109">The sample consists of two projects.</span></span> <span data-ttu-id="d91c0-110">Pierwszy projekt to prosta usługa, która jest uruchamiana w celu odpowiedzi na komunikaty pochodzące z klientów.</span><span class="sxs-lookup"><span data-stu-id="d91c0-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="d91c0-111">Drugi projekt jest aplikacją kliencką, która kompiluje <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> dwa obiekty <xref:System.Configuration.ExeConfigurationFileMap> przy użyciu dla pliku konfiguracji test. config i używa ich do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="d91c0-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="d91c0-112">Obaj klienci komunikują się z usługą przy użyciu konfiguracji określonej w pliku test. config.</span><span class="sxs-lookup"><span data-stu-id="d91c0-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="d91c0-113">Poniższy kod dodaje niestandardowy plik konfiguracji do aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="d91c0-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d91c0-114">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d91c0-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d91c0-115">Otwórz program Visual Studio 2012 z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="d91c0-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="d91c0-116">Kliknij prawym przyciskiem myszy rozwiązanie ConfigurationChannelFactory (2 projekty), a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d91c0-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="d91c0-117">W obszarze **wspólne właściwości**wybierz pozycję **projekt startowy**, a następnie kliknij pozycję **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="d91c0-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="d91c0-118">Przenieś projekt **usługi** na początek listy, z **akcją "Start"** , a następnie przenieś projekt **klienta** po projekcie **usługi** , również z **akcją "Start"** , tak aby projekt **klienta** był wykonywany po projekcie **usługi** .</span><span class="sxs-lookup"><span data-stu-id="d91c0-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="d91c0-119">Kliknij przycisk **OK**, a następnie naciśnij klawisz F5 (lub CTRL + F5), aby uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="d91c0-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d91c0-120">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d91c0-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d91c0-121">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="d91c0-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="d91c0-122">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d91c0-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d91c0-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d91c0-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
