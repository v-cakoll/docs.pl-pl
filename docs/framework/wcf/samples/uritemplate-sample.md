---
title: "Przykład elementu UriTemplate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 729a48fe0ea34bf1630824d941341fff82ade1ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="uritemplate-sample"></a><span data-ttu-id="0ae6c-102">Przykład elementu UriTemplate</span><span class="sxs-lookup"><span data-stu-id="0ae6c-102">UriTemplate Sample</span></span>
<span data-ttu-id="0ae6c-103"><xref:System.UriTemplate> Klasa dostarcza metody do pracy z zestawami identyfikatory URI, które mają wspólną strukturę.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="0ae6c-104">W tym przykładzie przedstawiono następujące podstawowe pojęcia dotyczące `UriTemplate`:</span><span class="sxs-lookup"><span data-stu-id="0ae6c-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
-   <span data-ttu-id="0ae6c-105">Składnia tworzenia szablonów.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-105">Syntax for creating templates.</span></span>  
  
-   <span data-ttu-id="0ae6c-106">Tworzenie wystąpień identyfikatorów URI z `UriTemplate` przy użyciu <xref:System.UriTemplate.BindByName%2A> i <xref:System.UriTemplate.BindByPosition%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
-   <span data-ttu-id="0ae6c-107"><xref:System.UriTemplateTable.Match%2A>, czyli odwrotność działania `BindByName` i `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0ae6c-108">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="0ae6c-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0ae6c-109">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0ae6c-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="0ae6c-110">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0ae6c-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0ae6c-111">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0ae6c-112">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0ae6c-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0ae6c-113">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0ae6c-114">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="0ae6c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ae6c-115">See Also</span></span>  
 [<span data-ttu-id="0ae6c-116">Tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="0ae6c-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="0ae6c-117">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="0ae6c-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
