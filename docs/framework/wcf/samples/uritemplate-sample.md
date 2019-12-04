---
title: Przykład elementu UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: c9dd8bdd21a075dca590c9446808860c006c18f8
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715425"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="11533-102">Przykład elementu UriTemplate</span><span class="sxs-lookup"><span data-stu-id="11533-102">UriTemplate Sample</span></span>
<span data-ttu-id="11533-103">Klasa <xref:System.UriTemplate> zapewnia metody pracy z zestawami identyfikatorów URI, które mają wspólną strukturę.</span><span class="sxs-lookup"><span data-stu-id="11533-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="11533-104">Ten przykład ilustruje następujące kluczowe pojęcia dotyczące `UriTemplate`:</span><span class="sxs-lookup"><span data-stu-id="11533-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="11533-105">Składnia służąca do tworzenia szablonów.</span><span class="sxs-lookup"><span data-stu-id="11533-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="11533-106">Tworzenie wystąpień identyfikatorów URI z `UriTemplate` przy użyciu <xref:System.UriTemplate.BindByName%2A> i <xref:System.UriTemplate.BindByPosition%2A>.</span><span class="sxs-lookup"><span data-stu-id="11533-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="11533-107"><xref:System.UriTemplateTable.Match%2A>, która jest operacją odwrotną `BindByName` i `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="11533-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="11533-108">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="11533-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="11533-109">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="11533-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="11533-110">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="11533-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="11533-111">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="11533-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="11533-112">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="11533-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="11533-113">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11533-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11533-114">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="11533-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="11533-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11533-115">See also</span></span>

- [<span data-ttu-id="11533-116">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="11533-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="11533-117">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="11533-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
