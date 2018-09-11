---
title: Przykład dyspozytora tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 4a4f725e88e014da241e1042c27bfee270e13268
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337411"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="cbd25-102">Przykład dyspozytora tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="cbd25-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="cbd25-103"><xref:System.UriTemplateTable> Klasa udostępnia struktury tabeli asocjacyjnych słownika podobne do pracy z zestawem <xref:System.UriTemplate> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="cbd25-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="cbd25-104">W tym przykładzie przedstawiono podstawowe aparatu dispatching utworzone przy użyciu `UriTemplateTable`, typowy scenariusz użycia dla `UriTemplateTable` klasy.</span><span class="sxs-lookup"><span data-stu-id="cbd25-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="cbd25-105">Niniejszy przykład pokazuje następujące kluczowe pojęcia związane z `UriTemplateTable` klasy:</span><span class="sxs-lookup"><span data-stu-id="cbd25-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="cbd25-106">Kojarzenie obiektów delegowanych z `UriTemplates` w `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="cbd25-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="cbd25-107">Za pomocą <xref:System.UriTemplateTable.MatchSingle%2A> uzyskać prawidłowe procedury obsługi delegata dla określonego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="cbd25-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
-   <span data-ttu-id="cbd25-108">Wywołanie delegata obsługi do przetwarzania żądania.</span><span class="sxs-lookup"><span data-stu-id="cbd25-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cbd25-109">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="cbd25-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cbd25-110">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbd25-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="cbd25-111">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbd25-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cbd25-112">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cbd25-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cbd25-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cbd25-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cbd25-114">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="cbd25-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cbd25-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cbd25-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="cbd25-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbd25-116">See Also</span></span>  
 [<span data-ttu-id="cbd25-117">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="cbd25-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="cbd25-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="cbd25-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
