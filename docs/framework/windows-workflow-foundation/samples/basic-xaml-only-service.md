---
title: "Tylko usługi podstawowe języka XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06a302b13db3b82dabb43989ac272df0d9aac008
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="basic-xaml-only-service"></a><span data-ttu-id="7056f-102">Tylko usługi podstawowe języka XAML</span><span class="sxs-lookup"><span data-stu-id="7056f-102">Basic XAML only Service</span></span>
<span data-ttu-id="7056f-103">W tym przykładzie pokazano, jak utworzyć usługę tylko XAML.</span><span class="sxs-lookup"><span data-stu-id="7056f-103">This sample demonstrates how to create a XAML only service.</span></span> <span data-ttu-id="7056f-104">Scenariusz jest usługą Diagnostyka dla problemów związanych z samochodów.</span><span class="sxs-lookup"><span data-stu-id="7056f-104">The scenario is a diagnostics service for car-related problems.</span></span> <span data-ttu-id="7056f-105">Usługa jest wdrażana jako przepływ pracy, która najpierw zadaje szereg pytań, aby zdiagnozować problem klienta.</span><span class="sxs-lookup"><span data-stu-id="7056f-105">The service is implemented as a workflow that asks the client a series of questions to diagnose the problem.</span></span> <span data-ttu-id="7056f-106">Istnieją dwa typy usługi diagnozować problemy (samochód się nie uruchomić lub klimatyzacja nie działa).</span><span class="sxs-lookup"><span data-stu-id="7056f-106">There are two types of issues the service can diagnose (car does not start or air conditioning not working).</span></span> <span data-ttu-id="7056f-107">Przepływ pracy używa szablonu żądania/odpowiedzi przy użyciu projektanta do udostępnienia trzy operacje usługi simple.</span><span class="sxs-lookup"><span data-stu-id="7056f-107">The workflow uses Request/Reply template from the designer to expose three simple service operations.</span></span> <span data-ttu-id="7056f-108">Usługa znajduje się w usługach IIS przez tworzenie katalogu wirtualnego w usługach IIS i kopiowanie service1.xamlx i plikach Web.config w katalogu wirtualnego, nie skompilowanego kodu jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="7056f-108">The service is hosted in IIS by creating a virtual directory in IIS and copying the service1.xamlx and Web.config files into the virtual directory, no compiled code is required.</span></span> <span data-ttu-id="7056f-109">Domyślnie ten przykład automatycznie skopiuje pliki potrzebne do utworzenia, wykonaj instrukcje instalacji dla przykładów WCF i WF katalogu wirtualnego: [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) podczas tworzenia w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="7056f-109">By default this sample will automatically copy the needed files into the virtual directory created when you follow the setup instructions for the WCF and WF samples: [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) when built in Visual Studio 2010.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7056f-110">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="7056f-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="7056f-111">Załadowanie projektu rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="7056f-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="7056f-112">Uruchom aplikację klienta wygenerowanego w \Client\bin\debug [katalogu podstawowego rozwiązania].</span><span class="sxs-lookup"><span data-stu-id="7056f-112">Run the Client application generated in [solution base directory]\Client\bin\debug.</span></span>  
  
3.  <span data-ttu-id="7056f-113">Aplikacja do drukowania opcje wybiera opcję.</span><span class="sxs-lookup"><span data-stu-id="7056f-113">The application prints out options, selects an option.</span></span> <span data-ttu-id="7056f-114">Następnie aplikacja prosi pytaniami odpowiedzieć tak lub nie (przy użyciu kluczy T/N).</span><span class="sxs-lookup"><span data-stu-id="7056f-114">The application then asks some questions, answer them yes or no (using Y/N keys).</span></span> <span data-ttu-id="7056f-115">Po zakończeniu jest usługa diagnozowanie problemów, drukowania diagnostyki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7056f-115">When the service is done diagnosing the issues, the application prints out a diagnosis.</span></span>  
  
4.  <span data-ttu-id="7056f-116">Aplikacja Przechodzi wstecz do opcji.</span><span class="sxs-lookup"><span data-stu-id="7056f-116">The application goes back to the options.</span></span> <span data-ttu-id="7056f-117">Można zdiagnozować problem innego lub zamknij aplikację.</span><span class="sxs-lookup"><span data-stu-id="7056f-117">You can diagnose another problem or exit the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7056f-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7056f-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7056f-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7056f-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7056f-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="7056f-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7056f-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7056f-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`