---
title: Znajdowanie asynchroniczne — przykład
ms.date: 03/30/2017
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
ms.openlocfilehash: ed900ba3cd1b55f4e35ec0d2b92ef6b7283b498e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500301"
---
# <a name="asynchronous-find-sample"></a><span data-ttu-id="2caad-102">Znajdowanie asynchroniczne — przykład</span><span class="sxs-lookup"><span data-stu-id="2caad-102">Asynchronous Find Sample</span></span>
<span data-ttu-id="2caad-103">Ten przykład przedstawia sposób użycia operację znajdowanie asynchroniczne w aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="2caad-103">This sample shows how to use the asynchronous find operation from a client application.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="2caad-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="2caad-104">Sample Details</span></span>  
 <span data-ttu-id="2caad-105">Zaletą tego wzorca projektu po to, czy klient jest powiadamiany o asynchronicznie punktów końcowych, znajduje się w wyniku żądania wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="2caad-105">The benefit of following this design pattern is that the client is notified asynchronously of the endpoints located as a result of the find request.</span></span> <span data-ttu-id="2caad-106">Aby zobaczyć, jak to działa, otwórz plik Client.cs.</span><span class="sxs-lookup"><span data-stu-id="2caad-106">To see how this works, open the Client.cs file.</span></span> <span data-ttu-id="2caad-107">Uwaga <xref:System.ServiceModel.Discovery.DiscoveryClient> obiekt ma dwa obiekty delegowane dołączony do jego obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2caad-107">Note the <xref:System.ServiceModel.Discovery.DiscoveryClient> object has two delegates attached to its event handlers.</span></span> <span data-ttu-id="2caad-108">Jednego delegata jest wywoływane, gdy <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> zdarzenia i inny jest wywoływana za każdym razem <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2caad-108">One delegate is called when a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is raised and another is called each time a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> event is raised.</span></span> <span data-ttu-id="2caad-109">Przykład pokazuje, jak możesz użyć tego wzorca w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2caad-109">The sample shows how you can utilize this pattern in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2caad-110">W przykładzie użyto punktów końcowych HTTP i do uruchomienia, muszą zostać dodane odpowiednie listy ACL adresu URL.</span><span class="sxs-lookup"><span data-stu-id="2caad-110">This sample uses HTTP endpoints and to run, proper URL ACLs must be added.</span></span> <span data-ttu-id="2caad-111">Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="2caad-111">For more information, see [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="2caad-112">Następujące polecenie w pełnych uprawnień do wykonania należy dodać odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="2caad-112">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="2caad-113">Można zastąpić użytkownika domena i nazwa użytkownika dla następujących argumentów, jeśli polecenie nie działa, ponieważ jest.</span><span class="sxs-lookup"><span data-stu-id="2caad-113">You may want to substitute your domain and username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2caad-114">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="2caad-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2caad-115">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AsyncFind.sln.</span><span class="sxs-lookup"><span data-stu-id="2caad-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the AsyncFind.sln.</span></span>  
  
2.  <span data-ttu-id="2caad-116">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2caad-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="2caad-117">Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz polecenia i przejdź do katalogu \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug lub \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug i uruchom Service.exe.</span><span class="sxs-lookup"><span data-stu-id="2caad-117">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug or \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug directory and run Service.exe.</span></span>  
  
4.  <span data-ttu-id="2caad-118">Po uruchomieniu usługi, przejdź do \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug lub WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug katalogu i uruchom Client.exe.</span><span class="sxs-lookup"><span data-stu-id="2caad-118">After the service has started, navigate to the \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug or WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug directory and run Client.exe.</span></span>  
  
5.  <span data-ttu-id="2caad-119">Sprawdź, czy klient jest w stanie zlokalizować i wywołania tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2caad-119">Observe the client is able to locate and call the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2caad-120">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2caad-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2caad-121">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2caad-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2caad-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="2caad-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2caad-123">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2caad-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a><span data-ttu-id="2caad-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2caad-124">See Also</span></span>
