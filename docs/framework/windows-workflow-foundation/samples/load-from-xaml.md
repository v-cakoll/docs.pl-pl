---
title: Ładowanie z pliku XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: e0cac1b6dfb9568ba08079cf5194b3432eea856f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637717"
---
# <a name="load-from-xaml"></a><span data-ttu-id="55d68-102">Ładowanie z pliku XAML</span><span class="sxs-lookup"><span data-stu-id="55d68-102">Load From XAML</span></span>
<span data-ttu-id="55d68-103">W tym przykładzie pokazano, jak załadować dynamicznie XAML przepływu pracy bez konieczności uruchamiania narzędzia XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="55d68-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="55d68-104">Przykład wywołuje <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="55d68-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="55d68-105">Próbka jest aplikacja kliencka Windows Presentation Foundation (WPF), który ładuje przepływów pracy XAML przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy i wykonuje je.</span><span class="sxs-lookup"><span data-stu-id="55d68-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="55d68-106">Po zostały już załadowane, za pomocą <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy <xref:System.Activities.DynamicActivity%601> jest zwracany, które mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="55d68-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="55d68-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="55d68-107">To use this sample</span></span>

1. <span data-ttu-id="55d68-108">Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania LoadFromXAML.sln.</span><span class="sxs-lookup"><span data-stu-id="55d68-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="55d68-109">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="55d68-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="55d68-110">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="55d68-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="55d68-111">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="55d68-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="55d68-112">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="55d68-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55d68-113">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="55d68-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55d68-114">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="55d68-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
