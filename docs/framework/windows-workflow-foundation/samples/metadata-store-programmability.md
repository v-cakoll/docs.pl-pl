---
title: Programowalność Store metadanych
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 4ea6117686b985a9ea18ce4e5cc4ea2b5c25524c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45998919"
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="12572-102">Programowalność Store metadanych</span><span class="sxs-lookup"><span data-stu-id="12572-102">Metadata Store Programmability</span></span>
<span data-ttu-id="12572-103">Magazyn metadanych jest [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] funkcja, która umożliwia skojarzenie dowolnego metadanych w formie atrybuty CLR typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="12572-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="12572-104">Pozwala to na tym luźne powiązanie składniki czasu wykonywania i ich odpowiedniki w czasie projektowania, a także możliwość zmiany składniki czasu projektowania, bez wywierania wpływu na środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="12572-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="12572-105">Przykład pokazuje, jak programować przy użyciu magazynu metadanych przez zastosowanie atrybutów do typu run-time, źródło, dla którego mamy żadnej kontroli nad.</span><span class="sxs-lookup"><span data-stu-id="12572-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="12572-106">Zazwyczaj terminologią to, że aplikacji macierzystej rejestruje metadanych dla zestawu typów.</span><span class="sxs-lookup"><span data-stu-id="12572-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="12572-107">W danych wyjściowych, możesz zauważyć atrybut dodatkowa, Nieoczekiwana <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="12572-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="12572-108">To jest dodawany, gdy za pomocą interfejsu API metadanych i nie ma wpływu na uruchomione próbki.</span><span class="sxs-lookup"><span data-stu-id="12572-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="12572-109">W tym przykładzie przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="12572-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="12572-110">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="12572-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="12572-111">Iniekcja atrybutu przy użyciu metadanych przechowywać interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="12572-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="12572-112">Przy użyciu mechanizmu wywołania zwrotnego, które mają być odroczone rejestracji metadane.</span><span class="sxs-lookup"><span data-stu-id="12572-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="12572-113">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="12572-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="12572-114">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ProgrammingMetadataStore.sln.</span><span class="sxs-lookup"><span data-stu-id="12572-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="12572-115">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="12572-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="12572-116">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="12572-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="12572-117">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="12572-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="12572-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="12572-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="12572-119">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="12572-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="12572-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="12572-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`