---
title: "Przykład dyspozytora tabeli UriTemplate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8fe3440c6c770052b40bbade7483e1c31e1671a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="7df25-102">Przykład dyspozytora tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7df25-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="7df25-103"><xref:System.UriTemplateTable> Klasa udostępnia struktury tabeli asocjacyjnej słownika podobne do pracy z zestawem <xref:System.UriTemplate> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="7df25-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="7df25-104">W tym przykładzie przedstawiono podstawowe aparatu wysyłania utworzony za pomocą `UriTemplateTable`, typowy scenariusz użycia dla `UriTemplateTable` klasy.</span><span class="sxs-lookup"><span data-stu-id="7df25-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="7df25-105">W tym przykładzie przedstawiono następujące kluczowe założenia `UriTemplateTable` klasy:</span><span class="sxs-lookup"><span data-stu-id="7df25-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="7df25-106">Kojarzenie obiektów delegowanych z `UriTemplates` w `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="7df25-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="7df25-107">Przy użyciu <xref:System.UriTemplateTable.MatchSingle%2A> można uzyskać obiektu delegowanego obsługi poprawne dla określonego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="7df25-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
-   <span data-ttu-id="7df25-108">Wywoływanie delegata obsługi do przetworzenia żądania.</span><span class="sxs-lookup"><span data-stu-id="7df25-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7df25-109">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="7df25-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7df25-110">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7df25-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="7df25-111">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7df25-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7df25-112">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7df25-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7df25-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7df25-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7df25-114">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="7df25-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7df25-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7df25-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="7df25-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7df25-116">See Also</span></span>  
 [<span data-ttu-id="7df25-117">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7df25-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="7df25-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7df25-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
