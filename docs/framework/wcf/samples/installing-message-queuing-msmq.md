---
title: Instalowanie usługi kolejkowania komunikatów (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: e6d6a3a2e1bc0a0c936e4b8594eab836b559e5a7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344740"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="eb3aa-102">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="eb3aa-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="eb3aa-103">W poniższych procedurach pokazano, jak zainstalować usługę kolejkowania komunikatów 4,0 i kolejkowanie komunikatów 3,0.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb3aa-104">Usługa kolejkowania komunikatów 4,0 nie jest dostępna w systemach [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="eb3aa-105">Aby zainstalować usługę kolejkowania komunikatów 4,0 w systemie Windows Server 2008 lub Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="eb3aa-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="eb3aa-106">W Menedżer serwera kliknij pozycję **funkcje**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-106">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="eb3aa-107">W okienku po prawej stronie w obszarze **Podsumowanie funkcji**kliknij pozycję **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="eb3aa-108">W oknie wyników rozwiń węzeł **kolejkowanie komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="eb3aa-109">Rozwiń węzeł **usługi kolejkowania komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-109">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="eb3aa-110">Kliknij pozycję **Integracja usług katalogowych** (w przypadku komputerów przyłączonych do domeny), a następnie kliknij pozycję **Obsługa protokołu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="eb3aa-111">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Instaluj**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="eb3aa-112">Aby zainstalować usługę kolejkowania komunikatów 4,0 w systemie Windows 7 lub Windows Vista</span><span class="sxs-lookup"><span data-stu-id="eb3aa-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="eb3aa-113">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-113">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="eb3aa-114">Kliknij pozycję **programy** , a następnie w obszarze **programy i funkcje**kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="eb3aa-115">Rozwiń węzeł serwer usługi Microsoft Message Queue (MSMQ), rozwiń węzeł serwer usługi kolejkowania komunikatów (MSMQ) firmy Microsoft, a następnie zaznacz pola wyboru dla następujących funkcji usługi kolejkowania komunikatów, które mają zostać zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="eb3aa-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="eb3aa-116">Integracja z usługą MSMQ Active Directory Domain Services (dla komputerów przyłączonych do domeny).</span><span class="sxs-lookup"><span data-stu-id="eb3aa-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="eb3aa-117">Obsługa protokołu HTTP w usłudze MSMQ.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-117">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="eb3aa-118">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-118">Click **OK**.</span></span>  
  
5. <span data-ttu-id="eb3aa-119">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** , aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="eb3aa-120">Aby zainstalować usługę kolejkowania komunikatów 3,0 w systemach Windows XP i Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="eb3aa-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="eb3aa-121">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-121">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="eb3aa-122">Kliknij przycisk **Dodaj Usuń programy** , a następnie kliknij przycisk **Dodaj składniki systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="eb3aa-123">Wybierz pozycję Kolejkowanie komunikatów i kliknij pozycję **szczegóły**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="eb3aa-124">W przypadku korzystania z systemu Windows Server 2003 wybierz opcję serwer aplikacji, aby uzyskać dostęp do usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-124">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="eb3aa-125">Upewnij się, że opcja obsługa protokołu HTTP usługi MSMQ została wybrana na stronie szczegółów.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="eb3aa-126">Kliknij przycisk **OK** , aby zamknąć stronę szczegóły, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="eb3aa-127">Ukończ instalację.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-127">Complete the installation.</span></span>  
  
6. <span data-ttu-id="eb3aa-128">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** , aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="eb3aa-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb3aa-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb3aa-129">See also</span></span>

- [<span data-ttu-id="eb3aa-130">Instrukcje dotyczące konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eb3aa-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
