---
title: "Obsługą elementu ReceiveContext kanały programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 729bf8bd1371bf64b9b05a235331120608824083
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="b8f71-102">Obsługą elementu ReceiveContext kanały programu WCF</span><span class="sxs-lookup"><span data-stu-id="b8f71-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="b8f71-103">W tym przykładzie pokazano przydatność <xref:System.ServiceModel.Channels.ReceiveContext>— włączone kanały programu WCF.</span><span class="sxs-lookup"><span data-stu-id="b8f71-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="b8f71-104">Przykład implementuje usługi można znaleźć iloczyn dwóch liczb za pomocą kanału NetMSMQ.</span><span class="sxs-lookup"><span data-stu-id="b8f71-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="b8f71-105"><xref:System.ServiceModel.Channels.ReceiveContext> Klasa umożliwia aplikacji zdecyduj, czy dostęp do wiadomości lub pozostaw w kolejce dla dalszego przetwarzania, nawet po sprawdzeniu treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b8f71-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="b8f71-106">W tym przykładzie klient wysyła losowych liczb całkowitych do kolejką transakcyjną.</span><span class="sxs-lookup"><span data-stu-id="b8f71-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="b8f71-107">`ProductCalculator` Usługa odbiera komunikaty i sprawdza treść wiadomości, które są liczbami całkowitymi, aby określić, czy można obliczyć produktu.</span><span class="sxs-lookup"><span data-stu-id="b8f71-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="b8f71-108">Jeśli operacja usługi nie zawiera produktu, wiadomość jest przywracane do kolejki i mogą być ponownie odbierane przez usługę nasłuchiwania w kolejce.</span><span class="sxs-lookup"><span data-stu-id="b8f71-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8f71-109">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b8f71-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b8f71-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="b8f71-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8f71-111">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b8f71-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8f71-112">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="b8f71-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b8f71-113">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="b8f71-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="b8f71-114">Upewnij się, że zainstalowano usługi kolejkowania wiadomości firmy Microsoft (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="b8f71-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="b8f71-115">Aby zainstalować usługi MSMQ na [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b8f71-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="b8f71-116">W **Menedżera serwera**, kliknij przycisk **funkcji**.</span><span class="sxs-lookup"><span data-stu-id="b8f71-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="b8f71-117">W prawym okienku w obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="b8f71-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="b8f71-118">W oknie wynikowy rozwiń **usługi kolejkowania komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="b8f71-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="b8f71-119">Rozwiń węzeł **komunikatów usługi kolejkowania wiadomości**.</span><span class="sxs-lookup"><span data-stu-id="b8f71-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="b8f71-120">Kliknij przycisk **integracji z usługami katalogu** (na komputerach przyłączonych do domeny), a następnie kliknij przycisk **obsługi protokołu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="b8f71-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="b8f71-121">Kliknij przycisk **dalej**, a następnie kliknij przycisk **zainstalować**.</span><span class="sxs-lookup"><span data-stu-id="b8f71-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="b8f71-122">Aby zainstalować usługi MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b8f71-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="b8f71-123">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="b8f71-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="b8f71-124">Kliknij przycisk **programy** , a następnie w obszarze **programy i funkcje**, kliknij przycisk **włączyć lub wyłączyć funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="b8f71-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="b8f71-125">Rozwiń węzeł **serwera Microsoft kolejki komunikatów (MSMQ)**, rozwiń węzeł **Microsoft kolejki komunikatów (MSMQ) Server Core**, a następnie zaznacz pola wyboru dla następujące funkcje usługi kolejkowania komunikatów do zainstalowania:</span><span class="sxs-lookup"><span data-stu-id="b8f71-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="b8f71-126">Serwer usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="b8f71-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="b8f71-127">Usługa MSMQ domeny integracji usług Active Directory (na komputerach przyłączonych do domeny)</span><span class="sxs-lookup"><span data-stu-id="b8f71-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="b8f71-128">Obsługa protokołu HTTP w usłudze MSMQ</span><span class="sxs-lookup"><span data-stu-id="b8f71-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="b8f71-129">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b8f71-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="b8f71-130">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.</span><span class="sxs-lookup"><span data-stu-id="b8f71-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="b8f71-131">Upewnij się, że [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b8f71-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="b8f71-132">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania ReceiveContextProductGenerator.sln.</span><span class="sxs-lookup"><span data-stu-id="b8f71-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="b8f71-133">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b8f71-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="b8f71-134">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="b8f71-134">To run the solution, press CTRL+F5.</span></span>
