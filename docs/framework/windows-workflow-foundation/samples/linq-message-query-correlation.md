---
title: Korelacja zapytania komunikatów LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 507001b165efdcbe7c1e27a07749dbe2eafb468f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182807"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="6b003-102">Korelacja zapytania komunikatów LINQ</span><span class="sxs-lookup"><span data-stu-id="6b003-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="6b003-103">W tym przykładzie pokazano, jak wykonać korelację <xref:System.ServiceModel.Dispatcher.MessageQuery> opartą na zawartości przy <xref:System.ServiceModel.XPathMessageQuery>użyciu implementacji niestandardowej, w przeciwieństwie do dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="6b003-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6b003-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="6b003-104">Demonstrates</span></span>  
 <span data-ttu-id="6b003-105">Niestandardowa <xref:System.ServiceModel.Dispatcher.MessageQuery>korelacja oparta na zawartości.</span><span class="sxs-lookup"><span data-stu-id="6b003-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="6b003-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="6b003-106">Discussion</span></span>  
 <span data-ttu-id="6b003-107">W tym przykładzie pokazano, jak rozszerzyć z klasy podstawowej <xref:System.ServiceModel.Dispatcher.MessageQuery> na potrzeby korelacji.</span><span class="sxs-lookup"><span data-stu-id="6b003-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="6b003-108">Implementacja niestandardowa, `LinqMessageQuery`umożliwia użytkownikom zapewnienie XName znaleźć w wiadomości przy użyciu XLinq.</span><span class="sxs-lookup"><span data-stu-id="6b003-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="6b003-109">Dane pobrane przez kwerendę jest używany do tworzenia klucza korelacji do wysyłania komunikatów do wystąpienia przepływu pracy odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="6b003-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6b003-110">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="6b003-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6b003-111">W tym przykładzie udostępnia usługę przepływu pracy przy użyciu punktów końcowych HTTP.</span><span class="sxs-lookup"><span data-stu-id="6b003-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="6b003-112">Aby uruchomić ten przykład, należy dodać odpowiednie listy ACL adresów URL (zobacz [Konfigurowanie protokołu HTTP i HTTPS](../../wcf/feature-details/configuring-http-and-https.md) w celu uzyskania szczegółowych informacji), uruchamiając program Visual Studio jako administrator lub wykonując następujące polecenie z podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL.</span><span class="sxs-lookup"><span data-stu-id="6b003-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="6b003-113">Upewnij się, że twoja domena i nazwa użytkownika są podstawione.</span><span class="sxs-lookup"><span data-stu-id="6b003-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="6b003-114">Po dodaniu list ACL url należy wykonać następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="6b003-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="6b003-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6b003-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="6b003-116">Ustaw wiele projektów start-upów, klikając prawym przyciskiem myszy rozwiązanie i wybierając **pozycję Ustaw projekty startowe**.</span><span class="sxs-lookup"><span data-stu-id="6b003-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="6b003-117">Dodaj **usługę** i **klienta** (w tej kolejności) jako wiele projektów startowych.</span><span class="sxs-lookup"><span data-stu-id="6b003-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="6b003-118">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="6b003-118">Run the application.</span></span> <span data-ttu-id="6b003-119">Konsola klienta pokazuje przepływ pracy wysyłający zamówienie i odbierający identyfikator zamówienia zakupu, a następnie potwierdzający zamówienie.</span><span class="sxs-lookup"><span data-stu-id="6b003-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="6b003-120">Okno Usługa wyświetli przetwarzane żądania.</span><span class="sxs-lookup"><span data-stu-id="6b003-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b003-121">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6b003-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b003-122">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="6b003-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6b003-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="6b003-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b003-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b003-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
