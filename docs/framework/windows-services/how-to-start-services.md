---
title: "Porady: uruchamianie usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 8352edaa9386adc1fbf3057c6e98f5a9cf9ce4a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-start-services"></a><span data-ttu-id="a2a8b-102">Porady: uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="a2a8b-102">How to: Start Services</span></span>
<span data-ttu-id="a2a8b-103">Po zainstalowaniu usługi musi być uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="a2a8b-104">Uruchamianie wywołania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="a2a8b-105">Zazwyczaj <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda definiuje przydatne pracę, wykona usługi.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="a2a8b-106">Po uruchomieniu usługi pozostanie aktywne do czasu jest ręcznie wstrzymana lub zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="a2a8b-107">Usługi można zainstalowane do uruchamiania automatycznie lub ręcznie.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="a2a8b-108">Usługa, która jest uruchamiana automatycznie zostanie uruchomiony, gdy komputer, na którym jest zainstalowany jest ponowny rozruch lub włączany po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="a2a8b-109">Użytkownik musi uruchomić usługę, która jest uruchamiana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2a8b-110">Domyślnie usługi utworzone za pomocą [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] są ustawione na uruchamianie ręczne.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-110">By default, services created with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] are set to start manually.</span></span>  
  
 <span data-ttu-id="a2a8b-111">Istnieje kilka sposobów, można ręcznie uruchomić usługę — od **Eksploratora serwera**, z **Menedżera sterowania usługami**, lub z kodu za pomocą składnika o nazwie <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="a2a8b-112">Możesz ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość <xref:System.ServiceProcess.ServiceInstaller> klasę, aby określić, czy należy uruchomić usługę ręcznie lub automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="a2a8b-113">Aby określić, jak powinna zaczynać się usługi</span><span class="sxs-lookup"><span data-stu-id="a2a8b-113">To specify how a service should start</span></span>  
  
1.  <span data-ttu-id="a2a8b-114">Po utworzeniu usługi, należy dodać wymagane pliki instalacyjne dla niego.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="a2a8b-115">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="a2a8b-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="a2a8b-116">W Projektancie kliknij Instalatora usługi dla usługi, którą użytkownik pracuje z.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3.  <span data-ttu-id="a2a8b-117">W **właściwości** ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwości do jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a2a8b-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="a2a8b-118">Aby zainstalować usługi</span><span class="sxs-lookup"><span data-stu-id="a2a8b-118">To have your service install</span></span>|<span data-ttu-id="a2a8b-119">Ustaw tę wartość</span><span class="sxs-lookup"><span data-stu-id="a2a8b-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="a2a8b-120">Po ponownym uruchomieniu komputera</span><span class="sxs-lookup"><span data-stu-id="a2a8b-120">When the computer is restarted</span></span>|<span data-ttu-id="a2a8b-121">**Automatyczne**</span><span class="sxs-lookup"><span data-stu-id="a2a8b-121">**Automatic**</span></span>|  
    |<span data-ttu-id="a2a8b-122">Po uruchomieniu usługi przez jawną akcję użytkownika</span><span class="sxs-lookup"><span data-stu-id="a2a8b-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="a2a8b-123">**Ręcznie**</span><span class="sxs-lookup"><span data-stu-id="a2a8b-123">**Manual**</span></span>|  
  
    > [!TIP]
    >  <span data-ttu-id="a2a8b-124">Aby zapobiec ogóle uruchomić usługi, można ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwości **wyłączone**.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="a2a8b-125">Można to zrobić, jeśli mają być ponownego rozruchu serwera i aby zaoszczędzić czas, zapobiegając usług, które zwykle zaczyna się od uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a2a8b-126">Po zainstalowaniu usługi można zmienić tych i innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="a2a8b-127">Istnieje kilka sposobów, można uruchomić usługę, która ma jego <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> procesu ustawioną **ręcznego** — od **Eksploratora serwera**, z **Menedżera sterowania usługami systemu Windows**, lub z kodu.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="a2a8b-128">Należy pamiętać, nie wszystkie z tych metod faktycznie uruchomić usługę w kontekście jest **Menedżera sterowania usługami**; **Eksploratora serwera** i programowe metody uruchamiania usługi faktycznie manipulowania kontrolera.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="a2a8b-129">Aby ręcznie uruchomić usługę z Eksploratora serwera</span><span class="sxs-lookup"><span data-stu-id="a2a8b-129">To manually start a service from Server Explorer</span></span>  
  
1.  <span data-ttu-id="a2a8b-130">W **Eksploratora serwera**, dodać serwer, jeśli go nie ma już na liście.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="a2a8b-131">Aby uzyskać więcej informacji, zobacz porady: dostęp i zainicjować Eksploratora bazy danych Eksploratora serwera.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2.  <span data-ttu-id="a2a8b-132">Rozwiń węzeł **usług** węzeł, a następnie zlokalizuj usługi chcesz uruchomić.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3.  <span data-ttu-id="a2a8b-133">Kliknij prawym przyciskiem myszy nazwę usługi, a następnie kliknij przycisk **Start**.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="a2a8b-134">Aby ręcznie uruchomić usługę od menedżera kontroli usług</span><span class="sxs-lookup"><span data-stu-id="a2a8b-134">To manually start a service from Services Control Manager</span></span>  
  
1.  <span data-ttu-id="a2a8b-135">Otwórz **Menedżera sterowania usługami** wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a2a8b-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    -   <span data-ttu-id="a2a8b-136">W systemach Windows XP i 2000 Professional, kliknij prawym przyciskiem myszy **Mój komputer** na pulpicie, a następnie kliknij **Zarządzaj**.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="a2a8b-137">W oknie dialogowym Rozwiń **usługi i aplikacje** węzła.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="a2a8b-138">\-lub -</span><span class="sxs-lookup"><span data-stu-id="a2a8b-138">\- or -</span></span>  
  
    -   <span data-ttu-id="a2a8b-139">W systemie Windows Server 2003 i Windows 2000 Server kliknij **Start**, wskaż **programy**, kliknij przycisk **narzędzia administracyjne**, a następnie kliknij przycisk **usług**.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a2a8b-140">W systemie Windows NT 4.0, możesz otworzyć to okno dialogowe z **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="a2a8b-141">Powinien zostać wyświetlony na liście usługi **usług** okna.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2.  <span data-ttu-id="a2a8b-142">Wybierz usługę na liście, kliknij go prawym przyciskiem myszy, a następnie kliknij przycisk **Start**.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="a2a8b-143">Aby ręcznie uruchomić usługę z kodu</span><span class="sxs-lookup"><span data-stu-id="a2a8b-143">To manually start a service from code</span></span>  
  
1.  <span data-ttu-id="a2a8b-144">Utwórz wystąpienie <xref:System.ServiceProcess.ServiceController> klasy, a następnie skonfigurować go do interakcji z usługą, którą chcesz administrować.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2.  <span data-ttu-id="a2a8b-145">Wywołanie <xref:System.ServiceProcess.ServiceController.Start%2A> metodę, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="a2a8b-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a8b-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2a8b-146">See Also</span></span>  
 [<span data-ttu-id="a2a8b-147">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a2a8b-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="a2a8b-148">Instrukcje: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a2a8b-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="a2a8b-149">Instrukcje: dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="a2a8b-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
