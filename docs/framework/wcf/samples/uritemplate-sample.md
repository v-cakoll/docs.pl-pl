---
title: Przykład elementu UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: e08333235b22e3c24fc6f4855fec43ef8b95fa5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183270"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="3a6af-102">Przykład elementu UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3a6af-102">UriTemplate Sample</span></span>
<span data-ttu-id="3a6af-103">Klasa <xref:System.UriTemplate> zawiera metody pracy z zestawami identyfikatorów URI, które mają wspólną strukturę.</span><span class="sxs-lookup"><span data-stu-id="3a6af-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="3a6af-104">W niniejszym przykładzie przedstawiono następujące `UriTemplate`kluczowe pojęcia odnoszące się do:</span><span class="sxs-lookup"><span data-stu-id="3a6af-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="3a6af-105">Składnia tworzenia szablonów.</span><span class="sxs-lookup"><span data-stu-id="3a6af-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="3a6af-106">Tworzenie wystąpienia identyfikatorów URI <xref:System.UriTemplate.BindByName%2A> <xref:System.UriTemplate.BindByPosition%2A>z `UriTemplate` using i .</span><span class="sxs-lookup"><span data-stu-id="3a6af-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="3a6af-107"><xref:System.UriTemplateTable.Match%2A>, który jest odwrotnym `BindByName` `BindByPosition`działaniem i .</span><span class="sxs-lookup"><span data-stu-id="3a6af-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a6af-108">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="3a6af-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3a6af-109">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a6af-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="3a6af-110">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a6af-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a6af-111">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3a6af-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3a6af-112">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="3a6af-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3a6af-113">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="3a6af-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a6af-114">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3a6af-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="3a6af-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a6af-115">See also</span></span>

- [<span data-ttu-id="3a6af-116">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3a6af-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="3a6af-117">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3a6af-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
