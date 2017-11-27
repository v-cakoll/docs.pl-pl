---
title: "Korelacja kwerendy komunikatów LINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3239d14ce8213b719305b5e32204569a8105997a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="45503-102">Korelacja kwerendy komunikatów LINQ</span><span class="sxs-lookup"><span data-stu-id="45503-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="45503-103">W tym przykładzie pokazano, jak wykonać korelacji na podstawie zawartości przy użyciu niestandardowego <xref:System.ServiceModel.Dispatcher.MessageQuery> implementacji, a nie dostarczane przez system <xref:System.ServiceModel.XPathMessageQuery>.</span><span class="sxs-lookup"><span data-stu-id="45503-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="45503-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="45503-104">Demonstrates</span></span>  
 <span data-ttu-id="45503-105">Niestandardowe <xref:System.ServiceModel.Dispatcher.MessageQuery>, na podstawie zawartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="45503-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="45503-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="45503-106">Discussion</span></span>  
 <span data-ttu-id="45503-107">W tym przykładzie pokazano, jak rozszerzyć z <xref:System.ServiceModel.Dispatcher.MessageQuery> klasy podstawowej na potrzeby korelacji.</span><span class="sxs-lookup"><span data-stu-id="45503-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="45503-108">Implementacja niestandardowa `LinqMessageQuery`, umożliwia użytkowników w celu zapewnienia XName można znaleźć w komunikacie przy użyciu XLinq.</span><span class="sxs-lookup"><span data-stu-id="45503-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="45503-109">Dane pobrane przez zapytanie służy do wysłania wiadomości do wystąpienia przepływu pracy odpowiednie klucz korelacji.</span><span class="sxs-lookup"><span data-stu-id="45503-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="45503-110">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="45503-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="45503-111">Ten przykład przedstawia usługi przepływu pracy przy użyciu punktów końcowych HTTP.</span><span class="sxs-lookup"><span data-stu-id="45503-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="45503-112">Można dodać do uruchomienia, to przykładowa, odpowiednich list ACL adresu URL (zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje), uruchamiając program Visual Studio jako Administrator lub, wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, aby dodać odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="45503-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="45503-113">Upewnij się, czy użytkownika domena i nazwa użytkownika są zastępowane.</span><span class="sxs-lookup"><span data-stu-id="45503-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="45503-114">Po dodaniu listy ACL adresu URL, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="45503-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="45503-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="45503-115">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="45503-116">Ustawianie wielu projektów uruchamiania prawym przyciskiem myszy rozwiązanie i wybierając **Ustaw projekty startowe**.</span><span class="sxs-lookup"><span data-stu-id="45503-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="45503-117">Dodaj **usługi** i **klienta** (w tej kolejności) jako wiele projektów rozruchu.</span><span class="sxs-lookup"><span data-stu-id="45503-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3.  <span data-ttu-id="45503-118">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="45503-118">Run the application.</span></span> <span data-ttu-id="45503-119">W konsoli klienta przedstawia przepływ pracy zamówienia wysyłanie i odbieranie identyfikator zamówienia zakupu oraz następnie potwierdzenie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="45503-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="45503-120">W oknie usługi są wyświetlane aktualnie przetwarzanych żądań.</span><span class="sxs-lookup"><span data-stu-id="45503-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="45503-121">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="45503-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45503-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="45503-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="45503-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="45503-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45503-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="45503-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
