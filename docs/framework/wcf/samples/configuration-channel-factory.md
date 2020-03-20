---
title: Fabryka kanałów konfiguracji
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 0f00ba5e217420fe416100071d380e413c3df118
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183947"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="c903a-102">Fabryka kanałów konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c903a-102">Configuration Channel Factory</span></span>
<span data-ttu-id="c903a-103">Ten przykład obejmuje użycie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="c903a-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="c903a-104">Umożliwia <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> centralne zarządzanie konfiguracją klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="c903a-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="c903a-105">Może to być również przydatne w scenariuszach, w których konfiguracja jest zaznaczona lub zmieniona po czasie ładowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c903a-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c903a-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="c903a-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="c903a-107">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="c903a-107">Discussion</span></span>
 <span data-ttu-id="c903a-108">W tym przykładzie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> pokazano, jak użyć do dodania określonego pliku konfiguracyjnego do aplikacji klienckiej, bez konieczności używania domyślnego pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c903a-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="c903a-109">Próba składa się z dwóch projektów.</span><span class="sxs-lookup"><span data-stu-id="c903a-109">The sample consists of two projects.</span></span> <span data-ttu-id="c903a-110">Pierwszy projekt jest prostą usługą, która działa, aby odpowiedzieć na wiadomości pochodzące od klientów.</span><span class="sxs-lookup"><span data-stu-id="c903a-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="c903a-111">Drugi projekt jest aplikacją kliencką, która tworzy dwa <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> obiekty przy użyciu <xref:System.Configuration.ExeConfigurationFileMap> pliku konfiguracji Test.config i używa ich do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="c903a-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="c903a-112">Obaj klienci komunikują się z usługą przy użyciu konfiguracji określonej w Test.config.</span><span class="sxs-lookup"><span data-stu-id="c903a-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="c903a-113">Poniższy kod dodaje niestandardowy plik konfiguracji do aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="c903a-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c903a-114">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c903a-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c903a-115">Otwórz program Visual Studio 2012 z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="c903a-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="c903a-116">Kliknij prawym przyciskiem myszy rozwiązanie ConfigurationChannelFactory (2 projekty), a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c903a-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="c903a-117">W **obszarze Właściwości wspólne**wybierz pozycję Projekt **uruchomienia**, a następnie kliknij pozycję Wiele **projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="c903a-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="c903a-118">Przenieś projekt **usługi** na początek listy, z **akcji "Start",** a następnie przenieść projekt **klienta** po projekcie **usługi,** również z **akcji "Start",** więc projekt **klienta** jest wykonywany po projekt **usługi.**</span><span class="sxs-lookup"><span data-stu-id="c903a-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="c903a-119">Kliknij **przycisk OK**, a następnie naciśnij klawiszE F5 (lub CTRL+F5), aby uruchomić próbkę.</span><span class="sxs-lookup"><span data-stu-id="c903a-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c903a-120">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c903a-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c903a-121">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c903a-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c903a-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c903a-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c903a-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c903a-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
