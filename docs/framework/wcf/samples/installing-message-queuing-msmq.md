---
title: Instalowanie usługi kolejkowania komunikatów (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: b54fab13d644cafda8a070280d672c60cf71b675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="4d219-102">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="4d219-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="4d219-103">Poniższe procedury pokazują, jak zainstalować w usłudze MSMQ 4.0 i 3.0 usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4d219-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d219-104">Komunikatów usługi kolejkowania wiadomości 4.0 nie jest dostępna w [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d219-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="4d219-105">Aby zainstalować usłudze MSMQ 4.0 w systemie Windows Server 2008 lub Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="4d219-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="4d219-106">W Menedżerze serwera kliknij **funkcji**.</span><span class="sxs-lookup"><span data-stu-id="4d219-106">In Server Manager, click **Features**.</span></span>  
  
2.  <span data-ttu-id="4d219-107">W prawym okienku w obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="4d219-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3.  <span data-ttu-id="4d219-108">W oknie wynikowy rozwiń **usługi kolejkowania komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="4d219-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4.  <span data-ttu-id="4d219-109">Rozwiń węzeł **komunikatów usługi kolejkowania wiadomości**.</span><span class="sxs-lookup"><span data-stu-id="4d219-109">Expand **Message Queuing Services**.</span></span>  
  
5.  <span data-ttu-id="4d219-110">Kliknij przycisk **integracji z usługami katalogu** (komputery przyłączone do domeny), a następnie kliknij przycisk **obsługi protokołu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="4d219-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6.  <span data-ttu-id="4d219-111">Kliknij przycisk **dalej**, następnie kliknij przycisk **zainstalować**.</span><span class="sxs-lookup"><span data-stu-id="4d219-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="4d219-112">Aby zainstalować usłudze MSMQ 4.0 w systemie Windows 7 lub Windows Vista</span><span class="sxs-lookup"><span data-stu-id="4d219-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1.  <span data-ttu-id="4d219-113">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="4d219-113">Open **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="4d219-114">Kliknij przycisk **programy** , a następnie w obszarze **programy i funkcje**, kliknij przycisk **włączyć lub wyłączyć funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="4d219-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3.  <span data-ttu-id="4d219-115">Rozwiń węzeł serwera Microsoft kolejki komunikatów (MSMQ), rozwiń Microsoft kolejki komunikatów (MSMQ) Server Core, a następnie zaznacz pola wyboru dla następujące funkcje usługi kolejkowania komunikatów do zainstalowania:</span><span class="sxs-lookup"><span data-stu-id="4d219-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    -   <span data-ttu-id="4d219-116">Usługa MSMQ domeny integracji usług Active Directory (na komputerach przyłączonych do domeny).</span><span class="sxs-lookup"><span data-stu-id="4d219-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    -   <span data-ttu-id="4d219-117">Obsługa protokołu HTTP w usłudze MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4d219-117">MSMQ HTTP Support.</span></span>  
  
4.  <span data-ttu-id="4d219-118">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4d219-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="4d219-119">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.</span><span class="sxs-lookup"><span data-stu-id="4d219-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="4d219-120">Aby zainstalować MSMQ 3.0 w systemie Windows XP i Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="4d219-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1.  <span data-ttu-id="4d219-121">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="4d219-121">Open **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="4d219-122">Kliknij przycisk **Dodaj Usuń programy** , a następnie kliknij przycisk **dodać składniki systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="4d219-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3.  <span data-ttu-id="4d219-123">Wybierz usługi kolejkowania komunikatów, a następnie kliknij przycisk **szczegóły**.</span><span class="sxs-lookup"><span data-stu-id="4d219-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d219-124">Jeśli używasz [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], wybierz serwer aplikacji można uzyskać dostępu do usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4d219-124">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], select Application Server to access Message Queuing.</span></span>  
  
4.  <span data-ttu-id="4d219-125">Upewnij się, że opcji wybranych na stronie Szczegóły dotyczące obsługi protokołu HTTP usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4d219-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5.  <span data-ttu-id="4d219-126">Kliknij przycisk **OK** zakończyć strony szczegółów, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="4d219-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="4d219-127">Ukończ instalację.</span><span class="sxs-lookup"><span data-stu-id="4d219-127">Complete the installation.</span></span>  
  
6.  <span data-ttu-id="4d219-128">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.</span><span class="sxs-lookup"><span data-stu-id="4d219-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d219-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d219-129">See Also</span></span>  
 [<span data-ttu-id="4d219-130">Instrukcje dotyczące konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4d219-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
