---
title: Kanały programu WCF z obsługą elementu ReceiveContext
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: d7f80d0874606129876fbf7dfa30c0327680b922
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515933"
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="75239-102">Kanały programu WCF z obsługą elementu ReceiveContext</span><span class="sxs-lookup"><span data-stu-id="75239-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="75239-103">W tym przykładzie przedstawiono przydatność <xref:System.ServiceModel.Channels.ReceiveContext>— włączone kanały programu WCF.</span><span class="sxs-lookup"><span data-stu-id="75239-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="75239-104">Przykład implementuje usługi można znaleźć iloczyn dwóch liczb przy użyciu kanału NetMSMQ.</span><span class="sxs-lookup"><span data-stu-id="75239-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="75239-105"><xref:System.ServiceModel.Channels.ReceiveContext> Klasa umożliwia aplikacji zdecyduj, czy dostęp do wiadomości, lub pozostaw to pole w kolejce do dalszego przetwarzania, nawet po zakończeniu poddane treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="75239-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="75239-106">W tym przykładzie klient wysyła losowych liczb całkowitych do kolejkę transakcyjną.</span><span class="sxs-lookup"><span data-stu-id="75239-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="75239-107">`ProductCalculator` Usługa odbiera komunikaty i sprawdza treść wiadomości, które są liczbami całkowitymi, aby ustalić, czy produkt może zostać obliczony.</span><span class="sxs-lookup"><span data-stu-id="75239-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="75239-108">Jeśli operacja usługi nie może obliczyć produktu, komunikat jest ponownie umieszczone w kolejce i mogą być ponownie odbierane przez usługę nasłuchiwać kolejki.</span><span class="sxs-lookup"><span data-stu-id="75239-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75239-109">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="75239-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="75239-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="75239-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="75239-111">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="75239-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75239-112">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="75239-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="75239-113">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="75239-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="75239-114">Upewnij się, że zainstalowano program Microsoft usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="75239-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="75239-115">Aby zainstalować usługę MSMQ na [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="75239-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="75239-116">W **Menedżera serwera**, kliknij przycisk **funkcji**.</span><span class="sxs-lookup"><span data-stu-id="75239-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="75239-117">W okienku po prawej stronie w obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="75239-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="75239-118">W oknie wynikowy rozwiń **usługi kolejkowania komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="75239-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="75239-119">Rozwiń **usługi kolejkowania komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="75239-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="75239-120">Kliknij przycisk **integracji z usługami katalogu** (na komputerach przyłączonych do domeny), a następnie kliknij przycisk **obsługi protokołu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="75239-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="75239-121">Kliknij przycisk **dalej**, a następnie kliknij przycisk **zainstalować**.</span><span class="sxs-lookup"><span data-stu-id="75239-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="75239-122">Aby zainstalować usługę MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="75239-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="75239-123">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="75239-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="75239-124">Kliknij przycisk **programy** a następnie w obszarze **programy i funkcje**, kliknij przycisk **Włącz lub wyłącz funkcje Windows**.</span><span class="sxs-lookup"><span data-stu-id="75239-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="75239-125">Rozwiń **serwera Microsoft kolejki komunikatów (MSMQ)**, rozwiń węzeł **Microsoft kolejki komunikatów (MSMQ) Server Core**, a następnie zaznacz pola wyboru dla następujących funkcji usługi kolejkowania komunikatów do zainstalowania:</span><span class="sxs-lookup"><span data-stu-id="75239-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="75239-126">Serwer usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="75239-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="75239-127">Usługa MSMQ domeny integracji usług Active Directory (na komputery przyłączone do domeny)</span><span class="sxs-lookup"><span data-stu-id="75239-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="75239-128">Obsługa protokołu HTTP w usłudze MSMQ</span><span class="sxs-lookup"><span data-stu-id="75239-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="75239-129">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="75239-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="75239-130">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.</span><span class="sxs-lookup"><span data-stu-id="75239-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="75239-131">Upewnij się, że [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="75239-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="75239-132">Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania ReceiveContextProductGenerator.sln.</span><span class="sxs-lookup"><span data-stu-id="75239-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="75239-133">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="75239-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="75239-134">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="75239-134">To run the solution, press CTRL+F5.</span></span>
