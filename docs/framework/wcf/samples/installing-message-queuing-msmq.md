---
title: Instalowanie usługi kolejkowania komunikatów (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 1bf79ed5dbcb9f2ace903260cc440e77df3aef09
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592297"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="c7c60-102">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="c7c60-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="c7c60-103">W poniższych procedurach pokazano, jak zainstalować usługę kolejkowania komunikatów 4,0 i kolejkowanie komunikatów 3,0.</span><span class="sxs-lookup"><span data-stu-id="c7c60-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7c60-104">Usługa kolejkowania komunikatów 4,0 nie jest dostępna w systemach Windows XP i Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="c7c60-104">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="c7c60-105">Aby zainstalować usługę kolejkowania komunikatów 4,0 w systemie Windows Server 2008 lub Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c7c60-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="c7c60-106">W Menedżer serwera kliknij pozycję **funkcje**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-106">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="c7c60-107">W okienku po prawej stronie w obszarze **Podsumowanie funkcji**kliknij pozycję **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="c7c60-108">W oknie wyników rozwiń węzeł **kolejkowanie komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="c7c60-109">Rozwiń węzeł **usługi kolejkowania komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-109">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="c7c60-110">Kliknij pozycję **Integracja usług katalogowych** (w przypadku komputerów przyłączonych do domeny), a następnie kliknij pozycję **Obsługa protokołu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="c7c60-111">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Instaluj**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="c7c60-112">Aby zainstalować usługę kolejkowania komunikatów 4,0 w systemie Windows 7 lub Windows Vista</span><span class="sxs-lookup"><span data-stu-id="c7c60-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="c7c60-113">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-113">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="c7c60-114">Kliknij pozycję **programy** , a następnie w obszarze **programy i funkcje**kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="c7c60-115">Rozwiń węzeł serwer usługi Microsoft Message Queue (MSMQ), rozwiń węzeł serwer usługi kolejkowania komunikatów (MSMQ) firmy Microsoft, a następnie zaznacz pola wyboru dla następujących funkcji usługi kolejkowania komunikatów, które mają zostać zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="c7c60-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="c7c60-116">Integracja z usługą MSMQ Active Directory Domain Services (dla komputerów przyłączonych do domeny).</span><span class="sxs-lookup"><span data-stu-id="c7c60-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="c7c60-117">Obsługa protokołu HTTP w usłudze MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c7c60-117">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="c7c60-118">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-118">Click **OK**.</span></span>  
  
5. <span data-ttu-id="c7c60-119">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** , aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="c7c60-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="c7c60-120">Aby zainstalować usługę kolejkowania komunikatów 3,0 w systemach Windows XP i Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="c7c60-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="c7c60-121">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-121">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="c7c60-122">Kliknij przycisk **Dodaj Usuń programy** , a następnie kliknij przycisk **Dodaj składniki systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="c7c60-123">Wybierz pozycję Kolejkowanie komunikatów i kliknij pozycję **szczegóły**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c7c60-124">W przypadku korzystania z systemu Windows Server 2003 wybierz opcję serwer aplikacji, aby uzyskać dostęp do usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c7c60-124">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="c7c60-125">Upewnij się, że opcja obsługa protokołu HTTP usługi MSMQ została wybrana na stronie szczegółów.</span><span class="sxs-lookup"><span data-stu-id="c7c60-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="c7c60-126">Kliknij przycisk **OK** , aby zamknąć stronę szczegóły, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="c7c60-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="c7c60-127">Ukończ instalację.</span><span class="sxs-lookup"><span data-stu-id="c7c60-127">Complete the installation.</span></span>  
  
6. <span data-ttu-id="c7c60-128">Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** , aby zakończyć instalację.</span><span class="sxs-lookup"><span data-stu-id="c7c60-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c60-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7c60-129">See also</span></span>

- [<span data-ttu-id="c7c60-130">Instrukcje dotyczące konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c7c60-130">Set-Up Instructions</span></span>](set-up-instructions.md)
