---
title: Ładowanie z pliku XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: c46c9020f07731d3d833332d77fd46a162ccb6dc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715950"
---
# <a name="load-from-xaml"></a><span data-ttu-id="f6bc8-102">Ładowanie z pliku XAML</span><span class="sxs-lookup"><span data-stu-id="f6bc8-102">Load From XAML</span></span>
<span data-ttu-id="f6bc8-103">Ten przykład ilustruje sposób dynamicznego ładowania przepływu pracy XAML bez konieczności uruchamiania narzędzia XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="f6bc8-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="f6bc8-104">Zamiast tego, przykład wywołuje metodę <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6bc8-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="f6bc8-105">Przykładem jest aplikacja kliencka Windows Presentation Foundation (WPF), która ładuje przepływy pracy XAML przy użyciu klasy <xref:System.Activities.XamlIntegration.ActivityXamlServices> i wykonuje je.</span><span class="sxs-lookup"><span data-stu-id="f6bc8-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="f6bc8-106">Po ich załadowaniu przy użyciu klasy <xref:System.Activities.XamlIntegration.ActivityXamlServices> zwracana jest <xref:System.Activities.DynamicActivity%601>, która może zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="f6bc8-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="f6bc8-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="f6bc8-107">To use this sample</span></span>

1. <span data-ttu-id="f6bc8-108">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania LoadFromXAML. sln.</span><span class="sxs-lookup"><span data-stu-id="f6bc8-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="f6bc8-109">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f6bc8-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="f6bc8-110">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f6bc8-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6bc8-111">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f6bc8-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f6bc8-112">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="f6bc8-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f6bc8-113">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f6bc8-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6bc8-114">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f6bc8-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
