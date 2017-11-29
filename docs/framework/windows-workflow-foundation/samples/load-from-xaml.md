---
title: "Ładowanie z XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ca5f830e666ad65ca2162ffd1abb03ce9beca387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="load-from-xaml"></a><span data-ttu-id="14074-102">Ładowanie z XAML</span><span class="sxs-lookup"><span data-stu-id="14074-102">Load From XAML</span></span>
<span data-ttu-id="14074-103">W tym przykładzie pokazano, jak załadować dynamicznie XAML przepływu pracy bez konieczności uruchamiania narzędzia XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="14074-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="14074-104">Przykład wywołuje <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="14074-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="14074-105">Próbka jest [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] aplikacji klienckiej, która ładuje przy użyciu przepływów pracy XAML <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy i wykonuje je.</span><span class="sxs-lookup"><span data-stu-id="14074-105">The sample is a [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="14074-106">Po ich zostały załadowane przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> klasy, <xref:System.Activities.DynamicActivity%601> jest zwracany, które mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="14074-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="14074-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="14074-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="14074-108">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LoadFromXAML.sln.</span><span class="sxs-lookup"><span data-stu-id="14074-108">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LoadFromXAML.sln solution file.</span></span>  
  
2.  <span data-ttu-id="14074-109">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="14074-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="14074-110">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="14074-110">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14074-111">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="14074-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14074-112">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="14074-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="14074-113">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="14074-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14074-114">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="14074-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`  
  
## <a name="see-also"></a><span data-ttu-id="14074-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14074-115">See Also</span></span>
