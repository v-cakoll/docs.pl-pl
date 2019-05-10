---
title: Korelacja zapytania komunikatów LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 5e979e6539d94d15b74f1da14f7082431ed2ff8c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622715"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="9c236-102">Korelacja zapytania komunikatów LINQ</span><span class="sxs-lookup"><span data-stu-id="9c236-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="9c236-103">W tym przykładzie pokazano, jak zrobić korelacja oparta na zawartości, przy użyciu niestandardowego <xref:System.ServiceModel.Dispatcher.MessageQuery> wdrożenia, a nie dostarczane przez system <xref:System.ServiceModel.XPathMessageQuery>.</span><span class="sxs-lookup"><span data-stu-id="9c236-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9c236-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="9c236-104">Demonstrates</span></span>  
 <span data-ttu-id="9c236-105">Niestandardowe <xref:System.ServiceModel.Dispatcher.MessageQuery>, na podstawie zawartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="9c236-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9c236-106">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="9c236-106">Discussion</span></span>  
 <span data-ttu-id="9c236-107">W tym przykładzie pokazano, jak rozszerzyć <xref:System.ServiceModel.Dispatcher.MessageQuery> klasy bazowej na potrzeby korelacji.</span><span class="sxs-lookup"><span data-stu-id="9c236-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="9c236-108">Implementacja niestandardowa `LinqMessageQuery`, umożliwia użytkownikom podanie XName można znaleźć w wiadomości przy użyciu XLinq.</span><span class="sxs-lookup"><span data-stu-id="9c236-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="9c236-109">Dane pobrane przez zapytanie jest używany w celu utworzenia klucza korelacji wysyłać komunikaty do wystąpienia przepływu pracy odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="9c236-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9c236-110">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="9c236-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9c236-111">Ten przykład przedstawia usługi przepływu pracy za pomocą punktów końcowych HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c236-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="9c236-112">Można dodać do uruchomienia tego przykładowego, odpowiednie listy ACL adresu URL (zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) szczegóły), albo przez uruchomienie programu Visual Studio jako Administrator, wykonując następujące polecenie w wierszu podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL.</span><span class="sxs-lookup"><span data-stu-id="9c236-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="9c236-113">Upewnij się, Twoja domena i nazwa użytkownika są zastępowane.</span><span class="sxs-lookup"><span data-stu-id="9c236-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="9c236-114">Po dodaniu listy ACL adresu URL, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="9c236-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="9c236-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="9c236-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="9c236-116">Ustawianie wielu projektów uruchamiania, kliknij prawym przyciskiem myszy rozwiązanie i wybierając **Ustaw projekty startowe**.</span><span class="sxs-lookup"><span data-stu-id="9c236-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="9c236-117">Dodaj **usługi** i **klienta** (w tej kolejności) jako wiele projektów uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="9c236-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="9c236-118">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="9c236-118">Run the application.</span></span> <span data-ttu-id="9c236-119">W konsoli klienta zawiera przepływu pracy, wysyłanie zamówienie i odbieranie identyfikator zamówienia zakupu oraz później potwierdzania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="9c236-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="9c236-120">Przedział czasu usługi pokaże przetwarzanych żądań.</span><span class="sxs-lookup"><span data-stu-id="9c236-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c236-121">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9c236-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9c236-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9c236-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9c236-123">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="9c236-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c236-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9c236-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
