---
title: Przykład dyspozytora tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 724a13504cea2672aef7ff155fbbff055aac34e6
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044591"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="54800-102">Przykład dyspozytora tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="54800-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="54800-103">Klasa zawiera strukturę tabeli asocjacyjnej, która umożliwia pracę z <xref:System.UriTemplate> zestawem wystąpień. <xref:System.UriTemplateTable></span><span class="sxs-lookup"><span data-stu-id="54800-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="54800-104">W tym przykładzie przedstawiono podstawowy aparat wysyłania, który został utworzony `UriTemplateTable`przy użyciu, typowy scenariusz użycia `UriTemplateTable` dla klasy.</span><span class="sxs-lookup"><span data-stu-id="54800-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="54800-105">Ten przykład ilustruje następujące kluczowe pojęcia dotyczące `UriTemplateTable` klasy:</span><span class="sxs-lookup"><span data-stu-id="54800-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="54800-106">Kojarzenie delegatów za `UriTemplates` pomocą elementu `UriTemplateTable`w.</span><span class="sxs-lookup"><span data-stu-id="54800-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="54800-107">Korzystanie <xref:System.UriTemplateTable.MatchSingle%2A> z programu w celu uzyskania poprawnego delegata programu obsługi dla określonego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="54800-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="54800-108">Wywoływanie delegata procedury obsługi w celu przetworzenia żądania.</span><span class="sxs-lookup"><span data-stu-id="54800-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="54800-109">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="54800-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="54800-110">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54800-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="54800-111">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54800-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="54800-112">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="54800-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="54800-113">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="54800-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="54800-114">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="54800-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="54800-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="54800-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="54800-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54800-116">See also</span></span>

- [<span data-ttu-id="54800-117">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="54800-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="54800-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="54800-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
