---
title: Programowanie magazynu metadanych
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 6efcb86e29f19a29d6ef382afa336d0ca2ce4306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="a02ec-102">Programowanie magazynu metadanych</span><span class="sxs-lookup"><span data-stu-id="a02ec-102">Metadata Store Programmability</span></span>
<span data-ttu-id="a02ec-103">Magazyn metadanych jest [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] typy funkcji, która umożliwia skojarzenie dowolnego metadane w formie atrybuty CLR w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a02ec-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="a02ec-104">Dzięki temu luźne powiązanie między składniki wykonawcze i ich odpowiedniki czasu projektowania, a także możliwość zmiany składniki czasu projektowania bez wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="a02ec-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="a02ec-105">Przykładzie pokazano, jak program względem magazynu metadanych przez stosowanie atrybutów do typu run-time, źródło, dla którego mamy żadnej kontroli nad.</span><span class="sxs-lookup"><span data-stu-id="a02ec-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="a02ec-106">Zwykle terminologii jest, że aplikacji obsługującej rejestruje metadanych dla zestawu typów.</span><span class="sxs-lookup"><span data-stu-id="a02ec-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="a02ec-107">W danych wyjściowych, mogą pojawić się dodatkowe, nieoczekiwany atrybut <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="a02ec-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="a02ec-108">To jest dodawany przy użyciu metadanych interfejsu API i nie ma wpływu na działanie próbki.</span><span class="sxs-lookup"><span data-stu-id="a02ec-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="a02ec-109">W tym przykładzie przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="a02ec-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a02ec-110">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="a02ec-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="a02ec-111">Atrybut iniekcji przy użyciu metadanych przechowywać interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="a02ec-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="a02ec-112">Odroczenie metadanych rejestracji przy użyciu mechanizmu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="a02ec-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a02ec-113">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="a02ec-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a02ec-114">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ProgrammingMetadataStore.sln.</span><span class="sxs-lookup"><span data-stu-id="a02ec-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a02ec-115">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a02ec-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a02ec-116">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="a02ec-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a02ec-117">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a02ec-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a02ec-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a02ec-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a02ec-119">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a02ec-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a02ec-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a02ec-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`