---
title: Przykład dyspozytora tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: e2ec85027274f302c59673a3d937be8f03d0b43b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715354"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="8d3cf-102">Przykład dyspozytora tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8d3cf-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="8d3cf-103">Klasa <xref:System.UriTemplateTable> udostępnia strukturę tabeli asocjacyjnej, która umożliwia pracę z zestawem <xref:System.UriTemplate> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="8d3cf-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="8d3cf-104">Ten przykład ilustruje podstawowy aparat do wysyłania z wykorzystaniem `UriTemplateTable`, typowy scenariusz użycia dla klasy `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="8d3cf-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="8d3cf-105">Ten przykład ilustruje następujące kluczowe pojęcia dotyczące klasy `UriTemplateTable`:</span><span class="sxs-lookup"><span data-stu-id="8d3cf-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="8d3cf-106">Kojarzenie delegatów z `UriTemplates` w `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="8d3cf-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="8d3cf-107">Używanie <xref:System.UriTemplateTable.MatchSingle%2A>, aby uzyskać prawidłowy delegat programu obsługi dla określonego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="8d3cf-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="8d3cf-108">Wywoływanie delegata procedury obsługi w celu przetworzenia żądania.</span><span class="sxs-lookup"><span data-stu-id="8d3cf-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8d3cf-109">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="8d3cf-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8d3cf-110">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d3cf-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="8d3cf-111">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d3cf-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8d3cf-112">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8d3cf-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d3cf-113">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="8d3cf-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8d3cf-114">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d3cf-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d3cf-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8d3cf-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="8d3cf-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d3cf-116">See also</span></span>

- [<span data-ttu-id="8d3cf-117">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8d3cf-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="8d3cf-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8d3cf-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
