---
title: Przykład dyspozytora tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: aa4259f8c823bebf38b9689df92c45992cb55723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143684"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="f1207-102">Przykład dyspozytora tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="f1207-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="f1207-103">Klasa <xref:System.UriTemplateTable> zawiera słownika jak struktury tabeli asocjacyjnych do pracy z zestawem <xref:System.UriTemplate> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="f1207-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="f1207-104">W tym przykładzie przedstawiono podstawowy `UriTemplateTable`aparat dyspozytorny zbudowany przy użyciu , typowy scenariusz użycia dla `UriTemplateTable` klasy.</span><span class="sxs-lookup"><span data-stu-id="f1207-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="f1207-105">W tym przykładzie przedstawiono następujące `UriTemplateTable` kluczowe pojęcia dla klasy:</span><span class="sxs-lookup"><span data-stu-id="f1207-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="f1207-106">Kojarzenie delegatów `UriTemplates` z `UriTemplateTable`w pliku .</span><span class="sxs-lookup"><span data-stu-id="f1207-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="f1207-107">Za <xref:System.UriTemplateTable.MatchSingle%2A> pomocą w celu uzyskania właściwego pełnomocnika obsługi dla określonego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="f1207-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="f1207-108">Wywoływanie delegata programu obsługi do przetwarzania żądania.</span><span class="sxs-lookup"><span data-stu-id="f1207-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f1207-109">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="f1207-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f1207-110">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1207-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="f1207-111">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1207-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f1207-112">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f1207-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1207-113">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="f1207-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f1207-114">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="f1207-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1207-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f1207-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="f1207-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1207-116">See also</span></span>

- [<span data-ttu-id="f1207-117">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="f1207-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="f1207-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="f1207-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
