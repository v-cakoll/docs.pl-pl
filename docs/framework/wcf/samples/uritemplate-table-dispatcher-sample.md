---
title: Przykład dyspozytora tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: af988a400361551dd11b74f781cf1ba108a3f5c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498492"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="82028-102">Przykład dyspozytora tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="82028-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="82028-103"><xref:System.UriTemplateTable> Klasa udostępnia struktury tabeli asocjacyjnych słownika podobne do pracy z zestawem <xref:System.UriTemplate> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="82028-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="82028-104">W tym przykładzie przedstawiono podstawowe aparatu dispatching utworzone przy użyciu `UriTemplateTable`, typowy scenariusz użycia dla `UriTemplateTable` klasy.</span><span class="sxs-lookup"><span data-stu-id="82028-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="82028-105">Niniejszy przykład pokazuje następujące kluczowe pojęcia związane z `UriTemplateTable` klasy:</span><span class="sxs-lookup"><span data-stu-id="82028-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="82028-106">Kojarzenie obiektów delegowanych z `UriTemplates` w `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="82028-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="82028-107">Za pomocą <xref:System.UriTemplateTable.MatchSingle%2A> uzyskać prawidłowe procedury obsługi delegata dla określonego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="82028-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
-   <span data-ttu-id="82028-108">Wywołanie delegata obsługi do przetwarzania żądania.</span><span class="sxs-lookup"><span data-stu-id="82028-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="82028-109">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="82028-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="82028-110">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82028-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="82028-111">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82028-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82028-112">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="82028-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="82028-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="82028-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="82028-114">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="82028-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82028-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="82028-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="82028-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82028-116">See also</span></span>
- [<span data-ttu-id="82028-117">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="82028-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="82028-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="82028-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
