---
title: 'Instrukcje: Uruchamianie usług'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: db66e8a264bc0381a2ff4689c4427047a158eb32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913929"
---
# <a name="how-to-start-services"></a><span data-ttu-id="9fd5b-102">Instrukcje: Uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="9fd5b-102">How to: Start Services</span></span>
<span data-ttu-id="9fd5b-103">Po zainstalowaniu usługi musi być uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="9fd5b-104">Początkowo wywołań <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="9fd5b-105">Zazwyczaj <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda definiuje przydatnej pracy, wykona usługi.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="9fd5b-106">Po uruchomieniu usługi pozostaje aktywne do czasu jest ręcznie wstrzymana lub zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="9fd5b-107">Usługi można skonfigurować do uruchamiania automatycznie lub ręcznie.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="9fd5b-108">Usługa, która jest uruchamiana automatycznie zostanie uruchomiony, gdy komputer, na którym jest zainstalowany, jest ponownie uruchamiany lub najpierw jest włączona.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="9fd5b-109">Użytkownik musi uruchomić usługę, która jest uruchamiana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fd5b-110">Domyślnie usługi utworzone za pomocą programu Visual Studio są ustawione na uruchamianie ręczne.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-110">By default, services created with Visual Studio are set to start manually.</span></span>  
  
 <span data-ttu-id="9fd5b-111">Istnieje kilka sposobów, można ręcznie uruchomić usługę — od **Eksploratora serwera**, z **Menedżera sterowania usługami**, lub z kodu za pomocą składnika o nazwie <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="9fd5b-112">Możesz ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość <xref:System.ServiceProcess.ServiceInstaller> klasę, aby określić, czy należy uruchomić usługę ręcznie lub automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="9fd5b-113">Aby określić, jak usługa powinna być uruchamiana</span><span class="sxs-lookup"><span data-stu-id="9fd5b-113">To specify how a service should start</span></span>  
  
1. <span data-ttu-id="9fd5b-114">Po utworzeniu usługi, dodanie niezbędnych instalatorów dla niego.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="9fd5b-115">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="9fd5b-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="9fd5b-116">W Projektancie kliknij Instalatora usługi dla usługi, którą pracujesz.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3. <span data-ttu-id="9fd5b-117">W **właściwości** oknie <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwości do jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9fd5b-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="9fd5b-118">Aby zainstalować usługę</span><span class="sxs-lookup"><span data-stu-id="9fd5b-118">To have your service install</span></span>|<span data-ttu-id="9fd5b-119">Ustaw tę wartość</span><span class="sxs-lookup"><span data-stu-id="9fd5b-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="9fd5b-120">Po ponownym uruchomieniu komputera</span><span class="sxs-lookup"><span data-stu-id="9fd5b-120">When the computer is restarted</span></span>|<span data-ttu-id="9fd5b-121">**Automatyczne**</span><span class="sxs-lookup"><span data-stu-id="9fd5b-121">**Automatic**</span></span>|  
    |<span data-ttu-id="9fd5b-122">Po uruchomieniu usługi w jawna Akcja użytkownika</span><span class="sxs-lookup"><span data-stu-id="9fd5b-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="9fd5b-123">**Ręcznie**</span><span class="sxs-lookup"><span data-stu-id="9fd5b-123">**Manual**</span></span>|  
  
    > [!TIP]
    >  <span data-ttu-id="9fd5b-124">Aby zapobiec sytuacji, w której usługa jest uruchomiona na wszystkich, możesz ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwości **wyłączone**.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="9fd5b-125">Możesz to zrobić, jeśli chcesz ponownie uruchomić serwer, a chcesz zaoszczędzić czas, co uniemożliwia usług, które zwykle zaczyna się od uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9fd5b-126">Po zainstalowaniu usługi można zmienić tych i innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="9fd5b-127">Istnieje kilka sposobów, które można uruchomić usługi, która ma jego <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> zestawu procesu **ręczne** — od **Eksploratora serwera**, z **Menedżera sterowania usługami systemu Windows**, lub z kodu.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="9fd5b-128">Ważne jest, aby należy pamiętać, nie wszystkie te metody faktycznie uruchomić usługi w kontekście **Menedżera sterowania usługami**; **Eksploratora serwera** i programowe metod uruchamiania usługi faktycznie manipulowania kontrolera.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="9fd5b-129">Aby ręcznie uruchomić usługę z poziomu Eksploratora serwera</span><span class="sxs-lookup"><span data-stu-id="9fd5b-129">To manually start a service from Server Explorer</span></span>  
  
1. <span data-ttu-id="9fd5b-130">W **Eksploratora serwera**, dodać serwer, jeśli go nie ma już na liście.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="9fd5b-131">Aby uzyskać więcej informacji, zobacz jak: Uzyskiwanie dostępu oraz inicjowanie Eksploratora bazy danych Eksploratora serwera.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2. <span data-ttu-id="9fd5b-132">Rozwiń **usług** węzła, a następnie znajdź odpowiednią usługę, aby uruchomić.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3. <span data-ttu-id="9fd5b-133">Kliknij prawym przyciskiem myszy nazwę usługi, a następnie kliknij przycisk **Start**.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="9fd5b-134">Aby ręcznie uruchomić usługę z Menedżera sterowania usługami</span><span class="sxs-lookup"><span data-stu-id="9fd5b-134">To manually start a service from Services Control Manager</span></span>  
  
1. <span data-ttu-id="9fd5b-135">Otwórz **Menedżera sterowania usługami** , wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9fd5b-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    - <span data-ttu-id="9fd5b-136">Windows XP lub 2000 Professional, kliknij prawym przyciskiem myszy **Mój komputer** na pulpicie, a następnie kliknij **Zarządzaj**.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="9fd5b-137">W oknie dialogowym Rozwiń **usługi i aplikacje** węzła.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="9fd5b-138">\- lub —</span><span class="sxs-lookup"><span data-stu-id="9fd5b-138">\- or -</span></span>  
  
    - <span data-ttu-id="9fd5b-139">W systemie Windows Server 2003 i Windows 2000 Server, kliknij przycisk **Start**, wskaż polecenie **programy**, kliknij przycisk **narzędzia administracyjne**, a następnie kliknij przycisk **usług**.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9fd5b-140">W Windows NT 4.0, możesz otworzyć to okno dialogowe z **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="9fd5b-141">Powinien zostać wyświetlony na liście usługi **usług** okna.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2. <span data-ttu-id="9fd5b-142">Wybierz usługę na liście, kliknij go prawym przyciskiem myszy, a następnie kliknij **Start**.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="9fd5b-143">Aby ręcznie uruchomić usługę z kodu</span><span class="sxs-lookup"><span data-stu-id="9fd5b-143">To manually start a service from code</span></span>  
  
1. <span data-ttu-id="9fd5b-144">Utwórz wystąpienie obiektu <xref:System.ServiceProcess.ServiceController> klasy, a następnie skonfigurować go do interakcji z usługą, którą chcesz administrować.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2. <span data-ttu-id="9fd5b-145">Wywołaj <xref:System.ServiceProcess.ServiceController.Start%2A> metodę, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="9fd5b-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd5b-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fd5b-146">See also</span></span>

- [<span data-ttu-id="9fd5b-147">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9fd5b-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="9fd5b-148">Instrukcje: Tworzenie usług Windows</span><span class="sxs-lookup"><span data-stu-id="9fd5b-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="9fd5b-149">Instrukcje: Dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="9fd5b-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
