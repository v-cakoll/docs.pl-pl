---
title: Przykład tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 9d60de39c8c025b31c45c79309442906fc3aab4e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044572"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="e1789-102">Przykład tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e1789-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="e1789-103">Klasa zawiera strukturę tabeli asocjacyjnej, która umożliwia pracę z `UriTemplate` zestawem wystąpień. <xref:System.UriTemplateTable></span><span class="sxs-lookup"><span data-stu-id="e1789-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="e1789-104">Określone identyfikatory URI (Uniform Resource Identifier) można efektywnie dopasować do wszystkich szablonów w tabeli, a dane skojarzone z pasującym szablonem mogą zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="e1789-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="e1789-105">Ten przykład ilustruje następujące kluczowe pojęcia związane `UriTemplateTable` z klasą:</span><span class="sxs-lookup"><span data-stu-id="e1789-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="e1789-106">Składnia dla tworzenia wystąpienia `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="e1789-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="e1789-107">Wypełnianie `UriTemplateTable` z zestawem par klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="e1789-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="e1789-108">Dopasowanie identyfikatora URI kandydata do tabeli przy <xref:System.UriTemplateTable.MatchSingle%2A>użyciu.</span><span class="sxs-lookup"><span data-stu-id="e1789-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e1789-109">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="e1789-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e1789-110">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1789-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="e1789-111">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1789-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e1789-112">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e1789-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e1789-113">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="e1789-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e1789-114">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e1789-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1789-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e1789-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="e1789-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1789-116">See also</span></span>

- [<span data-ttu-id="e1789-117">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e1789-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="e1789-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e1789-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
