---
title: 'Instrukcje: Uruchamianie usług'
description: Poznaj kilka sposobów uruchamiania usług. Po zainstalowaniu usługi należy ją uruchomić. Rozpoczynanie wywoływania metody OnStart w klasie usługi.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 4a2f9b291e60b12b1465fbb6bbbd1604572359a7
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925725"
---
# <a name="how-to-start-services"></a><span data-ttu-id="05be6-105">Instrukcje: Uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="05be6-105">How to: Start Services</span></span>

<span data-ttu-id="05be6-106">Po zainstalowaniu usługi należy ją uruchomić.</span><span class="sxs-lookup"><span data-stu-id="05be6-106">After a service is installed, it must be started.</span></span> <span data-ttu-id="05be6-107">Rozpoczęcie wywołuje <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="05be6-107">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="05be6-108">Zwykle <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda definiuje przydatną służbę wykonywaną przez usługę.</span><span class="sxs-lookup"><span data-stu-id="05be6-108">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="05be6-109">Po uruchomieniu usługa pozostaje aktywna, dopóki nie zostanie ręcznie wstrzymana lub zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="05be6-109">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="05be6-110">Usługi można skonfigurować do automatycznego uruchamiania lub ręcznie.</span><span class="sxs-lookup"><span data-stu-id="05be6-110">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="05be6-111">Usługa uruchamiana automatycznie zostanie uruchomiona, gdy komputer, na którym jest zainstalowany, jest ponownie uruchamiana lub włączona.</span><span class="sxs-lookup"><span data-stu-id="05be6-111">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="05be6-112">Użytkownik musi uruchomić usługę, która jest uruchamiana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="05be6-112">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="05be6-113">Domyślnie usługi utworzone za pomocą programu Visual Studio są ustawiane jako uruchamiane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="05be6-113">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="05be6-114">Istnieje kilka sposobów, aby ręcznie uruchomić usługę — od **Eksplorator serwera**, z **Menedżera sterowania usługami**lub z kodu przy użyciu składnika o nazwie <xref:System.ServiceProcess.ServiceController> .</span><span class="sxs-lookup"><span data-stu-id="05be6-114">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="05be6-115">Należy ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> Właściwość w klasie, <xref:System.ServiceProcess.ServiceInstaller> Aby określić, czy usługa powinna być uruchamiana ręcznie czy automatycznie.</span><span class="sxs-lookup"><span data-stu-id="05be6-115">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="05be6-116">Aby określić sposób uruchamiania usługi</span><span class="sxs-lookup"><span data-stu-id="05be6-116">To specify how a service should start</span></span>

1. <span data-ttu-id="05be6-117">Po utworzeniu usługi należy dodać do niej niezbędne Instalatory.</span><span class="sxs-lookup"><span data-stu-id="05be6-117">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="05be6-118">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów do aplikacji usługi](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="05be6-118">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="05be6-119">W projektancie kliknij Instalatora usługi dla usługi, z którą pracujesz.</span><span class="sxs-lookup"><span data-stu-id="05be6-119">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="05be6-120">W oknie **Właściwości** Ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> Właściwość na jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="05be6-120">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="05be6-121">Aby zainstalować usługę</span><span class="sxs-lookup"><span data-stu-id="05be6-121">To have your service install</span></span>|<span data-ttu-id="05be6-122">Ustaw tę wartość</span><span class="sxs-lookup"><span data-stu-id="05be6-122">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="05be6-123">Po ponownym uruchomieniu komputera</span><span class="sxs-lookup"><span data-stu-id="05be6-123">When the computer is restarted</span></span>|<span data-ttu-id="05be6-124">**Automatyczne**</span><span class="sxs-lookup"><span data-stu-id="05be6-124">**Automatic**</span></span>|
    |<span data-ttu-id="05be6-125">Po uruchomieniu przez jawną akcję użytkownika</span><span class="sxs-lookup"><span data-stu-id="05be6-125">When an explicit user action starts the service</span></span>|<span data-ttu-id="05be6-126">**Ręczne**</span><span class="sxs-lookup"><span data-stu-id="05be6-126">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="05be6-127">Aby zapobiec uruchamianiu usługi w ogóle, można ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> Właściwość na wartość **wyłączone**.</span><span class="sxs-lookup"><span data-stu-id="05be6-127">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="05be6-128">Można to zrobić, jeśli zamierzasz ponownie uruchomić serwer kilka razy i chcesz zaoszczędzić czas, zapobiegając usługom, które normalnie zaczynają się od uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="05be6-128">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="05be6-129">Te i inne właściwości można zmienić po zainstalowaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="05be6-129">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="05be6-130">Istnieje kilka sposobów, w których można uruchomić usługę, która ma swój <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> proces ustawiony na **ręczny** — od **Eksplorator serwera**, z **Menedżera sterowania usługami systemu Windows**lub z kodu.</span><span class="sxs-lookup"><span data-stu-id="05be6-130">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="05be6-131">Należy pamiętać, że nie wszystkie te metody faktycznie uruchamiają usługę w kontekście **Menedżera kontroli usług**. **Eksplorator serwera** i programowe metody uruchamiania usługi faktycznie manipulują kontrolerem.</span><span class="sxs-lookup"><span data-stu-id="05be6-131">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="05be6-132">Aby ręcznie uruchomić usługę z Eksplorator serwera</span><span class="sxs-lookup"><span data-stu-id="05be6-132">To manually start a service from Server Explorer</span></span>

1. <span data-ttu-id="05be6-133">W **Eksplorator serwera**Dodaj serwer, którego chcesz użyć, jeśli nie jest jeszcze wymieniony.</span><span class="sxs-lookup"><span data-stu-id="05be6-133">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="05be6-134">Aby uzyskać więcej informacji, zobacz How to: Access and Initialize Eksplorator serwera-Eksplorator bazy danych.</span><span class="sxs-lookup"><span data-stu-id="05be6-134">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="05be6-135">Rozwiń węzeł **usługi** , a następnie Znajdź usługę, którą chcesz uruchomić.</span><span class="sxs-lookup"><span data-stu-id="05be6-135">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="05be6-136">Kliknij prawym przyciskiem myszy nazwę usługi, a następnie kliknij przycisk **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="05be6-136">Right-click the name of the service, and click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="05be6-137">Aby ręcznie uruchomić usługę za pomocą Menedżera kontroli usług</span><span class="sxs-lookup"><span data-stu-id="05be6-137">To manually start a service from Services Control Manager</span></span>

1. <span data-ttu-id="05be6-138">Otwórz **Menedżera kontroli usług** , wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="05be6-138">Open the **Services Control Manager** by doing one of the following:</span></span>

    - <span data-ttu-id="05be6-139">W systemach Windows XP i 2000 Professional kliknij prawym przyciskiem myszy ikonę **mój komputer** na pulpicie, a następnie kliknij polecenie **Zarządzaj**.</span><span class="sxs-lookup"><span data-stu-id="05be6-139">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="05be6-140">W wyświetlonym oknie dialogowym Rozwiń węzeł **usługi i aplikacje** .</span><span class="sxs-lookup"><span data-stu-id="05be6-140">In the dialog box that appears, expand the **Services and Applications** node.</span></span>

      <span data-ttu-id="05be6-141">\-oraz</span><span class="sxs-lookup"><span data-stu-id="05be6-141">\- or -</span></span>

    - <span data-ttu-id="05be6-142">W systemie Windows Server 2003 i Windows 2000 Server, kliknij przycisk **Start**, wskaż polecenie **programy**, kliknij polecenie **Narzędzia administracyjne**, a następnie kliknij pozycję **usługi**.</span><span class="sxs-lookup"><span data-stu-id="05be6-142">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="05be6-143">W systemie Windows NT w wersji 4,0 można otworzyć to okno dialogowe z **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="05be6-143">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>

    <span data-ttu-id="05be6-144">Twoja usługa powinna zostać wyświetlona w sekcji **usługi** okna.</span><span class="sxs-lookup"><span data-stu-id="05be6-144">You should now see your service listed in the **Services** section of the window.</span></span>

2. <span data-ttu-id="05be6-145">Wybierz usługę na liście, kliknij ją prawym przyciskiem myszy, a następnie kliknij przycisk **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="05be6-145">Select your service in the list, right-click it, and then click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="05be6-146">Aby ręcznie uruchomić usługę z kodu</span><span class="sxs-lookup"><span data-stu-id="05be6-146">To manually start a service from code</span></span>

1. <span data-ttu-id="05be6-147">Utwórz wystąpienie <xref:System.ServiceProcess.ServiceController> klasy i skonfiguruj je do współpracy z usługą, którą chcesz administrować.</span><span class="sxs-lookup"><span data-stu-id="05be6-147">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="05be6-148">Wywołaj <xref:System.ServiceProcess.ServiceController.Start%2A> metodę, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="05be6-148">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="05be6-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05be6-149">See also</span></span>

- [<span data-ttu-id="05be6-150">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="05be6-150">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="05be6-151">Instrukcje: Tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="05be6-151">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="05be6-152">Instrukcje: Dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="05be6-152">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
