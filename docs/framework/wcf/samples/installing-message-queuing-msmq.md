---
title: Instalowanie usługi kolejkowania komunikatów (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 118143f2d434e9f4399c3e9141743fc0254b61ab
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039626"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="c301a-102">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="c301a-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="c301a-103">W poniższych procedurach pokazano, jak zainstalować usługę kolejkowania komunikatów 4,0 i kolejkowanie komunikatów 3,0.</span><span class="sxs-lookup"><span data-stu-id="c301a-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c301a-104">Usługa kolejkowania komunikatów 4,0 nie jest dostępna w [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c301a-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="c301a-105">Aby zainstalować usługę kolejkowania komunikatów 4,0 w systemie Windows Server 2008 lub Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c301a-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="c301a-106">W Menedżer serwera kliknij pozycję **funkcje**.</span><span class="sxs-lookup"><span data-stu-id="c301a-106">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="c301a-107">W okienku po prawej stronie w obszarze **Podsumowanie funkcji**kliknij pozycję **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="c301a-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="c301a-108">W oknie wyników rozwiń węzeł **kolejkowanie komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="c301a-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="c301a-109">Rozwiń węzeł **usługi kolejkowania komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="c301a-109">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="c301a-110">Kliknij pozycję **Integracja usług katalogowych** (w przypadku komputerów przyłączonych do domeny), a następnie kliknij pozycję **Obsługa protokołu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="c301a-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="c301a-111">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Instaluj**.</span><span class="sxs-lookup"><span data-stu-id="c301a-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="c301a-112">Aby zainstalować usługę kolejkowania komunikatów 4,0 w systemie Windows 7 lub Windows Vista</span><span class="sxs-lookup"><span data-stu-id="c301a-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="c301a-113">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="c301a-113">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="c301a-114">Kliknij pozycję **programy** , a następnie w obszarze **programy i funkcje**kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="c301a-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="c301a-115">Rozwiń węzeł serwer usługi Microsoft Message Queue (MSMQ), rozwiń węzeł serwer usługi kolejkowania komunikatów (MSMQ) firmy Microsoft, a następnie zaznacz pola wyboru dla następujących funkcji usługi kolejkowania komunikatów, które mają zostać zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="c301a-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="c301a-116">Integracja z usługą MSMQ Active Directory Domain Services (dla komputerów przyłączonych do domeny).</span><span class="sxs-lookup"><span data-stu-id="c301a-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="c301a-117">Obsługa protokołu HTTP w usłudze MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c301a-117">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="c301a-118">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="c301a-118">Click **OK**.</span></span>  
  
5. <span data-ttu-id="c301a-119">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** , aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="c301a-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="c301a-120">Aby zainstalować usługę kolejkowania komunikatów 3,0 w systemach Windows XP i Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="c301a-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="c301a-121">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="c301a-121">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="c301a-122">Kliknij przycisk **Dodaj Usuń programy** , a następnie kliknij przycisk **Dodaj składniki systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="c301a-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="c301a-123">Wybierz pozycję Kolejkowanie komunikatów i kliknij pozycję **szczegóły**.</span><span class="sxs-lookup"><span data-stu-id="c301a-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c301a-124">Jeśli używasz programu, wybierz opcję serwer aplikacji, aby uzyskać dostęp do usługi kolejkowania komunikatów. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c301a-124">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="c301a-125">Upewnij się, że opcja obsługa protokołu HTTP usługi MSMQ została wybrana na stronie szczegółów.</span><span class="sxs-lookup"><span data-stu-id="c301a-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="c301a-126">Kliknij przycisk **OK** , aby zamknąć stronę szczegóły, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="c301a-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="c301a-127">Ukończ instalację.</span><span class="sxs-lookup"><span data-stu-id="c301a-127">Complete the installation.</span></span>  
  
6. <span data-ttu-id="c301a-128">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** , aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="c301a-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c301a-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c301a-129">See also</span></span>

- [<span data-ttu-id="c301a-130">Instrukcje dotyczące konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c301a-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
