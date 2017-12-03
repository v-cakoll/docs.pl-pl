---
title: "Fabryka kanałów konfiguracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aa0f4aec0a673a07c6b6d752d8609caedbcfa4b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="aa58a-102">Fabryka kanałów konfiguracji</span><span class="sxs-lookup"><span data-stu-id="aa58a-102">Configuration Channel Factory</span></span>
<span data-ttu-id="aa58a-103">W tym przykładzie przedstawiono użycie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="aa58a-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="aa58a-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umożliwia centralne zarządzanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="aa58a-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client configuration.</span></span> <span data-ttu-id="aa58a-105">Może to być również przydatne w scenariuszach, w których konfiguracja jest wybrane lub zmienić po czas ładowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa58a-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="aa58a-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="aa58a-106">Demonstrates</span></span>  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a><span data-ttu-id="aa58a-107">Omówienie</span><span class="sxs-lookup"><span data-stu-id="aa58a-107">Discussion</span></span>  
 <span data-ttu-id="aa58a-108">Ten przykład przedstawia sposób użycia <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> można dodać pliku określoną konfigurację do aplikacji klienckiej, bez konieczności używania domyślny plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa58a-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>  
  
 <span data-ttu-id="aa58a-109">Przykład zawiera dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="aa58a-109">The sample consists of two projects.</span></span> <span data-ttu-id="aa58a-110">Pierwszy projekt jest proste usługa, która działa na udzielenie odpowiedzi na wiadomości przychodzących od klientów.</span><span class="sxs-lookup"><span data-stu-id="aa58a-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="aa58a-111">Drugi projekt jest aplikacji klienckiej, która tworzy dwa <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> obiektów przy użyciu <xref:System.Configuration.ExeConfigurationFileMap> Test.config pliku konfiguracji i używa ich do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="aa58a-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="aa58a-112">Obaj klienci komunikują się z usługą za pomocą konfiguracji określone w Test.config.</span><span class="sxs-lookup"><span data-stu-id="aa58a-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>  
  
 <span data-ttu-id="aa58a-113">Poniższy kod dodaje plik konfiguracji niestandardowej do aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="aa58a-113">The following code adds a custom configuration file to a client application.</span></span>  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aa58a-114">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="aa58a-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="aa58a-115">Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="aa58a-115">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="aa58a-116">Kliknij prawym przyciskiem myszy rozwiązanie ConfigurationChannelFactory (projekty 2), a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="aa58a-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="aa58a-117">W **wspólne właściwości**, wybierz pozycję **projekt startowy**, a następnie kliknij przycisk **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="aa58a-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
4.  <span data-ttu-id="aa58a-118">Przenieś **usługi** projektu na początku listy, z **akcji "Start"**, a następnie przenieść **klienta** projektu po **usługi**projektu, także z **akcji "Start"**, więc **klienta** projektu jest wykonywany po **usługi** projektu.</span><span class="sxs-lookup"><span data-stu-id="aa58a-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>  
  
5.  <span data-ttu-id="aa58a-119">Kliknij przycisk **OK**, a następnie naciśnij klawisz F5 (lub CTRL + F5), aby uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="aa58a-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aa58a-120">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="aa58a-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aa58a-121">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="aa58a-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aa58a-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="aa58a-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa58a-123">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="aa58a-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
