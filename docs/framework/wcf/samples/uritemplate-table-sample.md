---
title: "Przykład tabeli UriTemplate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c4561590228531066014e69c03fcef0a6142cd70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="2fd32-102">Przykład tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2fd32-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="2fd32-103"><xref:System.UriTemplateTable> Klasa udostępnia struktury tabeli asocjacyjnej słownika podobne do pracy z zestawem `UriTemplate` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="2fd32-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="2fd32-104">Określone Uniform Resource Identifier (URI) może być dopasowana wydajnie wszystkie szablony w tabeli, a można pobrać danych skojarzone z szablonem dopasowany.</span><span class="sxs-lookup"><span data-stu-id="2fd32-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="2fd32-105">W tym przykładzie przedstawiono następujące podstawowe pojęcia związane z `UriTemplateTable` klasy:</span><span class="sxs-lookup"><span data-stu-id="2fd32-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="2fd32-106">Składnia tworzenia wystąpienia `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="2fd32-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="2fd32-107">Wypełnianie `UriTemplateTable` zestaw par klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="2fd32-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
-   <span data-ttu-id="2fd32-108">Dopasowywanie candidate URI przed potencjalnym użyciem tabeli <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="2fd32-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2fd32-109">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="2fd32-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2fd32-110">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fd32-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="2fd32-111">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fd32-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2fd32-112">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2fd32-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2fd32-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2fd32-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2fd32-114">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="2fd32-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fd32-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2fd32-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="2fd32-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fd32-116">See Also</span></span>  
 [<span data-ttu-id="2fd32-117">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2fd32-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)  
 [<span data-ttu-id="2fd32-118">Obiekt UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2fd32-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
