---
title: Korelacja zapytania komunikatów LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 202d65914d32245952f308d3115ec93231f95f15
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989339"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="449ff-102">Korelacja zapytania komunikatów LINQ</span><span class="sxs-lookup"><span data-stu-id="449ff-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="449ff-103">Ten przykład pokazuje, jak przeprowadzić korelację opartą na zawartości przy <xref:System.ServiceModel.Dispatcher.MessageQuery> użyciu niestandardowej implementacji, w przeciwieństwie do dostarczonych <xref:System.ServiceModel.XPathMessageQuery>przez system.</span><span class="sxs-lookup"><span data-stu-id="449ff-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="449ff-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="449ff-104">Demonstrates</span></span>  
 <span data-ttu-id="449ff-105">Niestandardowa <xref:System.ServiceModel.Dispatcher.MessageQuery>korelacja oparta na zawartości.</span><span class="sxs-lookup"><span data-stu-id="449ff-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="449ff-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="449ff-106">Discussion</span></span>  
 <span data-ttu-id="449ff-107">Ten przykład pokazuje, <xref:System.ServiceModel.Dispatcher.MessageQuery> jak rozłożyć z klasy podstawowej na potrzeby korelacji.</span><span class="sxs-lookup"><span data-stu-id="449ff-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="449ff-108">Implementacja niestandardowa `LinqMessageQuery`, umożliwia użytkownikom udostępnianie XName w wiadomości przy użyciu XLinq.</span><span class="sxs-lookup"><span data-stu-id="449ff-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="449ff-109">Dane pobierane przez zapytanie są używane do tworzenia klucza korelacji do wysyłania komunikatów do odpowiedniego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="449ff-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="449ff-110">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="449ff-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="449ff-111">Ten przykład uwidacznia usługę przepływu pracy za pomocą punktów końcowych HTTP.</span><span class="sxs-lookup"><span data-stu-id="449ff-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="449ff-112">Aby uruchomić ten przykład, należy dodać odpowiednie listy ACL adresów URL (zobacz [Konfigurowanie protokołu HTTP i https](https://go.microsoft.com/fwlink/?LinkId=70353) w celu uzyskania szczegółowych informacji), uruchamiając program Visual Studio jako administrator lub wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL.</span><span class="sxs-lookup"><span data-stu-id="449ff-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="449ff-113">Upewnij się, że Twoja domena i nazwa użytkownika zostały zastąpione.</span><span class="sxs-lookup"><span data-stu-id="449ff-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="449ff-114">Po dodaniu list ACL adresów URL wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="449ff-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="449ff-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="449ff-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="449ff-116">Aby ustawić wiele projektów uruchomieniowych, kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Ustaw projekty startowe**.</span><span class="sxs-lookup"><span data-stu-id="449ff-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="449ff-117">Dodaj **usługę** i **klienta** (w tej kolejności) jako wiele projektów początkowych.</span><span class="sxs-lookup"><span data-stu-id="449ff-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="449ff-118">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="449ff-118">Run the application.</span></span> <span data-ttu-id="449ff-119">W konsoli klienta programu jest wyświetlany przepływ pracy, który wysyła zamówienie i pobiera identyfikator zamówienia zakupu, a następnie potwierdza zamówienie.</span><span class="sxs-lookup"><span data-stu-id="449ff-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="449ff-120">W oknie usługi zostaną wyświetlone żądania przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="449ff-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="449ff-121">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="449ff-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="449ff-122">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="449ff-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="449ff-123">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="449ff-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="449ff-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="449ff-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
