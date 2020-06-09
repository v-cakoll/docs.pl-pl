---
title: Przykład elementu UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: fb956882ae653f584026fefb20e261c90010ca9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591062"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="d8a06-102">Przykład elementu UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d8a06-102">UriTemplate Sample</span></span>
<span data-ttu-id="d8a06-103"><xref:System.UriTemplate>Klasa zawiera metody pracy z zestawami identyfikatorów URI, które mają wspólną strukturę.</span><span class="sxs-lookup"><span data-stu-id="d8a06-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="d8a06-104">Ten przykład ilustruje następujące kluczowe pojęcia dotyczące `UriTemplate` :</span><span class="sxs-lookup"><span data-stu-id="d8a06-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="d8a06-105">Składnia służąca do tworzenia szablonów.</span><span class="sxs-lookup"><span data-stu-id="d8a06-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="d8a06-106">Tworzenie wystąpienia identyfikatorów URI z `UriTemplate` użyciem <xref:System.UriTemplate.BindByName%2A> i <xref:System.UriTemplate.BindByPosition%2A> .</span><span class="sxs-lookup"><span data-stu-id="d8a06-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="d8a06-107"><xref:System.UriTemplateTable.Match%2A>, która jest operacją odwrotną `BindByName` i `BindByPosition` .</span><span class="sxs-lookup"><span data-stu-id="d8a06-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d8a06-108">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d8a06-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d8a06-109">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d8a06-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="d8a06-110">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d8a06-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d8a06-111">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d8a06-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d8a06-112">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="d8a06-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d8a06-113">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d8a06-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d8a06-114">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d8a06-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="d8a06-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8a06-115">See also</span></span>

- [<span data-ttu-id="d8a06-116">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d8a06-116">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="d8a06-117">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d8a06-117">UriTemplate Table Dispatcher</span></span>](uritemplate-table-dispatcher-sample.md)
