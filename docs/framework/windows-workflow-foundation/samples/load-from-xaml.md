---
title: Ładowanie z pliku XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: 2f45beb398e6d6b91bf7444dd590b862ff8c7515
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038084"
---
# <a name="load-from-xaml"></a><span data-ttu-id="69d12-102">Ładowanie z pliku XAML</span><span class="sxs-lookup"><span data-stu-id="69d12-102">Load From XAML</span></span>
<span data-ttu-id="69d12-103">Ten przykład ilustruje sposób dynamicznego ładowania przepływu pracy XAML bez konieczności uruchamiania narzędzia XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="69d12-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="69d12-104">Zamiast tego, przykład wywołuje <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="69d12-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="69d12-105">Przykładem jest aplikacja kliencka Windows Presentation Foundation (WPF), która ładuje przepływy pracy <xref:System.Activities.XamlIntegration.ActivityXamlServices> XAML przy użyciu klasy i wykonuje je.</span><span class="sxs-lookup"><span data-stu-id="69d12-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="69d12-106">Po ich załadowaniu przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy zostanie zwrócona wartość <xref:System.Activities.DynamicActivity%601> , która może zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="69d12-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="69d12-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="69d12-107">To use this sample</span></span>

1. <span data-ttu-id="69d12-108">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania LoadFromXAML. sln.</span><span class="sxs-lookup"><span data-stu-id="69d12-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="69d12-109">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="69d12-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="69d12-110">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="69d12-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69d12-111">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="69d12-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="69d12-112">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="69d12-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="69d12-113">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="69d12-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="69d12-114">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="69d12-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
