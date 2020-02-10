---
title: Korelacja zapytania komunikatów LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: cd91a171f3242cfd7e8ac0404e24ac065919bcce
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094621"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="e6002-102">Korelacja zapytania komunikatów LINQ</span><span class="sxs-lookup"><span data-stu-id="e6002-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="e6002-103">Ten przykład pokazuje, jak przeprowadzić korelację opartą na zawartości przy użyciu niestandardowej implementacji <xref:System.ServiceModel.Dispatcher.MessageQuery>, w przeciwieństwie do <xref:System.ServiceModel.XPathMessageQuery>dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="e6002-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e6002-104">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="e6002-104">Demonstrates</span></span>  
 <span data-ttu-id="e6002-105"><xref:System.ServiceModel.Dispatcher.MessageQuery>niestandardowe, korelacja oparta na zawartości.</span><span class="sxs-lookup"><span data-stu-id="e6002-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e6002-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="e6002-106">Discussion</span></span>  
 <span data-ttu-id="e6002-107">Ten przykład pokazuje, jak rozłożyć z klasy bazowej <xref:System.ServiceModel.Dispatcher.MessageQuery> na potrzeby korelacji.</span><span class="sxs-lookup"><span data-stu-id="e6002-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="e6002-108">Implementacja niestandardowa, `LinqMessageQuery`, umożliwia użytkownikom podawanie XName do znajdowania w komunikacie przy użyciu XLinq.</span><span class="sxs-lookup"><span data-stu-id="e6002-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="e6002-109">Dane pobierane przez zapytanie są używane do tworzenia klucza korelacji do wysyłania komunikatów do odpowiedniego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e6002-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e6002-110">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="e6002-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e6002-111">Ten przykład uwidacznia usługę przepływu pracy za pomocą punktów końcowych HTTP.</span><span class="sxs-lookup"><span data-stu-id="e6002-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="e6002-112">Aby uruchomić ten przykład, należy dodać odpowiednie listy ACL adresów URL (zobacz [Konfigurowanie protokołu HTTP i https](../../wcf/feature-details/configuring-http-and-https.md) w celu uzyskania szczegółowych informacji), uruchamiając program Visual Studio jako administrator lub wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL.</span><span class="sxs-lookup"><span data-stu-id="e6002-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="e6002-113">Upewnij się, że Twoja domena i nazwa użytkownika zostały zastąpione.</span><span class="sxs-lookup"><span data-stu-id="e6002-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="e6002-114">Po dodaniu list ACL adresów URL wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="e6002-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="e6002-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e6002-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="e6002-116">Aby ustawić wiele projektów uruchomieniowych, kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Ustaw projekty startowe**.</span><span class="sxs-lookup"><span data-stu-id="e6002-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="e6002-117">Dodaj **usługę** i **klienta** (w tej kolejności) jako wiele projektów początkowych.</span><span class="sxs-lookup"><span data-stu-id="e6002-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="e6002-118">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="e6002-118">Run the application.</span></span> <span data-ttu-id="e6002-119">W konsoli klienta programu jest wyświetlany przepływ pracy, który wysyła zamówienie i pobiera identyfikator zamówienia zakupu, a następnie potwierdza zamówienie.</span><span class="sxs-lookup"><span data-stu-id="e6002-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="e6002-120">W oknie usługi zostaną wyświetlone żądania przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="e6002-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e6002-121">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e6002-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e6002-122">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="e6002-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e6002-123">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6002-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6002-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e6002-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
