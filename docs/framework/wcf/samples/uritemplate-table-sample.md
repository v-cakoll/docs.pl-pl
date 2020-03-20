---
title: Przykład tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: c0aed1a49faf74ab9fd463769aab66ad72e74038
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183264"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="a823b-102">Przykład tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="a823b-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="a823b-103">Klasa <xref:System.UriTemplateTable> zawiera słownika jak struktury tabeli asocjacyjnych do pracy z zestawem `UriTemplate` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="a823b-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="a823b-104">Określone jednolite identyfikatory zasobów (URI) można skutecznie dopasować do wszystkich szablonów w tabeli, a dane skojarzone z dopasowanym szablonem mogą być pobierane.</span><span class="sxs-lookup"><span data-stu-id="a823b-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="a823b-105">W tym przykładzie przedstawiono następujące `UriTemplateTable` kluczowe pojęcia związane z klasą:</span><span class="sxs-lookup"><span data-stu-id="a823b-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="a823b-106">Składnia tworzenia wystąpienia pliku `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="a823b-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="a823b-107">Wypełnianie a `UriTemplateTable` zestawem par kluczy/wartości.</span><span class="sxs-lookup"><span data-stu-id="a823b-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="a823b-108">Dopasowywanie identyfikatora URI kandydata do tabeli przy użyciu programu <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="a823b-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a823b-109">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="a823b-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a823b-110">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a823b-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="a823b-111">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a823b-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a823b-112">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a823b-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a823b-113">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="a823b-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a823b-114">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="a823b-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a823b-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a823b-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="a823b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a823b-116">See also</span></span>

- [<span data-ttu-id="a823b-117">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="a823b-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="a823b-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="a823b-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
