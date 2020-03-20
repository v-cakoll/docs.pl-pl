---
title: Ładowanie z pliku XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: d07ddef8fb982aa0bf707cb688cd23f04bb231d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142722"
---
# <a name="load-from-xaml"></a><span data-ttu-id="d121f-102">Ładowanie z pliku XAML</span><span class="sxs-lookup"><span data-stu-id="d121f-102">Load From XAML</span></span>
<span data-ttu-id="d121f-103">W tym przykładzie pokazano, jak dynamicznie załadować przepływ pracy XAML bez konieczności uruchamiania narzędzia XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="d121f-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="d121f-104">Zamiast tego przykład wywołuje <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="d121f-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="d121f-105">Przykład jest windows presentation foundation (WPF) aplikacja kliencka, która <xref:System.Activities.XamlIntegration.ActivityXamlServices> ładuje przepływy pracy XAML przy użyciu klasy i wykonuje je.</span><span class="sxs-lookup"><span data-stu-id="d121f-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="d121f-106">Po ich załadowaniu <xref:System.Activities.XamlIntegration.ActivityXamlServices> przy użyciu <xref:System.Activities.DynamicActivity%601> klasy, zwracany jest, które mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="d121f-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="d121f-107">Aby użyć tej próbki</span><span class="sxs-lookup"><span data-stu-id="d121f-107">To use this sample</span></span>

1. <span data-ttu-id="d121f-108">Za pomocą programu Visual Studio 2010 otwórz plik rozwiązania LoadFromXAML.sln.</span><span class="sxs-lookup"><span data-stu-id="d121f-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="d121f-109">Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="d121f-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="d121f-110">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="d121f-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d121f-111">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d121f-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d121f-112">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="d121f-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d121f-113">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d121f-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d121f-114">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d121f-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
