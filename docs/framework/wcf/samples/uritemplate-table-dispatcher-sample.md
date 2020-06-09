---
title: Przykład dyspozytora tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 97e916aaf9d137eb7931470f9565797b03620d28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591075"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="44217-102">Przykład dyspozytora tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="44217-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="44217-103"><xref:System.UriTemplateTable>Klasa zawiera strukturę tabeli asocjacyjnej, która umożliwia pracę z zestawem <xref:System.UriTemplate> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="44217-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="44217-104">W tym przykładzie przedstawiono podstawowy aparat wysyłania, który został utworzony przy użyciu `UriTemplateTable` , typowy scenariusz użycia dla `UriTemplateTable` klasy.</span><span class="sxs-lookup"><span data-stu-id="44217-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="44217-105">Ten przykład ilustruje następujące kluczowe pojęcia dotyczące `UriTemplateTable` klasy:</span><span class="sxs-lookup"><span data-stu-id="44217-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="44217-106">Kojarzenie delegatów za pomocą `UriTemplates` elementu w `UriTemplateTable` .</span><span class="sxs-lookup"><span data-stu-id="44217-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="44217-107">Korzystanie <xref:System.UriTemplateTable.MatchSingle%2A> z programu w celu uzyskania poprawnego delegata programu obsługi dla określonego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="44217-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="44217-108">Wywoływanie delegata procedury obsługi w celu przetworzenia żądania.</span><span class="sxs-lookup"><span data-stu-id="44217-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="44217-109">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="44217-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="44217-110">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="44217-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="44217-111">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="44217-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="44217-112">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="44217-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="44217-113">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="44217-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="44217-114">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="44217-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="44217-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="44217-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="44217-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44217-116">See also</span></span>

- [<span data-ttu-id="44217-117">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="44217-117">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="44217-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="44217-118">UriTemplate</span></span>](uritemplate-sample.md)
