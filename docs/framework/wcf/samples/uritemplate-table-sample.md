---
title: Przykład tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 4543d4676344d10c3e380c3522a7ca5a6a8d6294
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006450"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="bf2c8-102">Przykład tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="bf2c8-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="bf2c8-103"><xref:System.UriTemplateTable> Klasa udostępnia struktury tabeli asocjacyjnych słownika podobne do pracy z zestawem `UriTemplate` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="bf2c8-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="bf2c8-104">Określone Uniform Resource Identifier (URI) może zostać dopasowany efektywnie wszystkie szablony w tabeli i mogą być pobierane dane skojarzone z dopasowany szablon.</span><span class="sxs-lookup"><span data-stu-id="bf2c8-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="bf2c8-105">Niniejszy przykład pokazuje następujące kluczowe pojęcia związane z `UriTemplateTable` klasy:</span><span class="sxs-lookup"><span data-stu-id="bf2c8-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="bf2c8-106">Składnia podczas tworzenia wystąpienia `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="bf2c8-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="bf2c8-107">Wypełnianie `UriTemplateTable` zestaw par klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="bf2c8-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="bf2c8-108">Dopasowywanie Release candidate URI względem tabeli przy użyciu <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf2c8-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bf2c8-109">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="bf2c8-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bf2c8-110">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf2c8-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="bf2c8-111">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf2c8-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bf2c8-112">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bf2c8-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bf2c8-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="bf2c8-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bf2c8-114">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="bf2c8-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf2c8-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bf2c8-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="bf2c8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf2c8-116">See also</span></span>

- [<span data-ttu-id="bf2c8-117">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="bf2c8-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="bf2c8-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="bf2c8-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
