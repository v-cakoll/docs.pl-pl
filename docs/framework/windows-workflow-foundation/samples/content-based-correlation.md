---
title: "Korelacja na podstawie zawartości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0490dcc854a6686c69ebc480df42e6086d1fdc52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="content-based-correlation"></a><span data-ttu-id="f0c9c-102">Korelacja na podstawie zawartości</span><span class="sxs-lookup"><span data-stu-id="f0c9c-102">Content-Based Correlation</span></span>
<span data-ttu-id="f0c9c-103">W tym przykładzie przedstawiono sposób działania dotyczące komunikatów (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>) mogą być używane z wielu correlations.and na podstawie zawartości na podstawie zawartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>) can be used with multiple content-based correlations.and content-based correlation.</span></span> <span data-ttu-id="f0c9c-104">W tym scenariuszu korelacji jest najpierw zainicjować na podstawie Identyfikatora zamówienia zakupu, a następnie innego korelacji jest tworzone, później oparte na identyfikator klienta.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-104">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span> <span data-ttu-id="f0c9c-105">Oznacza to, jak <xref:System.ServiceModel.Activities.Receive> działania można wykonaj istniejących korelacji i inicjować korelację nowe na podstawie tego samego komunikatu przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-105">This shows how a <xref:System.ServiceModel.Activities.Receive> activity can both follow an existing correlation and initialize a new correlation based on the same incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f0c9c-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="f0c9c-106">Demonstrates</span></span>  
 <span data-ttu-id="f0c9c-107">Działania obsługi wiadomości i na podstawie zawartości korelacji</span><span class="sxs-lookup"><span data-stu-id="f0c9c-107">Messaging activities and content-based correlation</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="f0c9c-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f0c9c-108">Discussion</span></span>  
 <span data-ttu-id="f0c9c-109">Ten przykład przedstawia sposób użycia wielu korelacji na podstawie zawartości.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-109">This sample shows how to use multiple content-based correlations.</span></span>  <span data-ttu-id="f0c9c-110">W tym scenariuszu korelacji jest najpierw zainicjować na podstawie Identyfikatora zamówienia zakupu, a następnie innego korelacji jest tworzone, później oparte na identyfikator klienta.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-110">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span>  <span data-ttu-id="f0c9c-111">Korelacji są kaskadowych przy użyciu <xref:System.ServiceModel.Activities.Receive> działania zarówno istniejących korelacji (PurchaseOrderId) i inicjuje nowy korelacji (identyfikator klienta) oparte na ten sam komunikat przychodzący.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-111">The correlations are cascaded using a <xref:System.ServiceModel.Activities.Receive> activity that both follows an existing correlation (PurchaseOrderId) and initializes a new correlation (CustomerId) based on the same incoming message.</span></span>  <span data-ttu-id="f0c9c-112">Aby to osiągnąć, <xref:System.ServiceModel.Activities.Receive> używa działania <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> i <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-112">To accomplish this, the <xref:System.ServiceModel.Activities.Receive> activity uses the <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> and <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="f0c9c-113">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="f0c9c-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="f0c9c-114">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikony, jak i wybierając **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-114">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="f0c9c-115">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CascadingCorrelation.sln.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CascadingCorrelation.sln solution file.</span></span>  
  
3.  <span data-ttu-id="f0c9c-116">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="f0c9c-117">Aby uruchomić serwera, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-117">To run the server, press F5.</span></span>  
  
5.  <span data-ttu-id="f0c9c-118">Gdy usługa jest gotowa i nasłuchiwania dla wiadomości w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-118">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f0c9c-119">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f0c9c-120">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f0c9c-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f0c9c-121">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f0c9c-122">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f0c9c-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="f0c9c-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0c9c-123">See Also</span></span>
