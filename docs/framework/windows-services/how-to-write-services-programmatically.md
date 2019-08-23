---
title: 'Instrukcje: Programowane pisanie usług'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 29e0b95ad91c93f3a23246daf2be128b10d7e2ce
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952405"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="dcfde-102">Instrukcje: Programowane pisanie usług</span><span class="sxs-lookup"><span data-stu-id="dcfde-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="dcfde-103">Jeśli zdecydujesz się nie używać szablonu projektu usługi systemu Windows, możesz napisać własne usługi, konfigurując dziedziczenie i inne elementy infrastruktury samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="dcfde-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="dcfde-104">W przypadku programistycznego tworzenia usługi należy wykonać kilka czynności, dla których szablon mógłby obsłużyć:</span><span class="sxs-lookup"><span data-stu-id="dcfde-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="dcfde-105">Należy skonfigurować klasę usługi, aby dziedziczyć z <xref:System.ServiceProcess.ServiceBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="dcfde-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="dcfde-106">Należy utworzyć `Main` metodę dla projektu usługi, który definiuje usługi do uruchomienia i <xref:System.ServiceProcess.ServiceBase.Run%2A> wywołuje metodę z nich.</span><span class="sxs-lookup"><span data-stu-id="dcfde-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="dcfde-107">Należy zastąpić <xref:System.ServiceProcess.ServiceBase.OnStart%2A> procedury i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> wprowadzić dowolny kod, który ma zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="dcfde-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="dcfde-108">Aby programowo napisać usługę</span><span class="sxs-lookup"><span data-stu-id="dcfde-108">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="dcfde-109">Utwórz pusty projekt i Utwórz odwołanie do odpowiednich przestrzeni nazw, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="dcfde-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="dcfde-110">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** i kliknij polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="dcfde-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="dcfde-111">Na karcie **.NET Framework** przewiń do **pliku System. dll** , a następnie kliknij przycisk **Wybierz**.</span><span class="sxs-lookup"><span data-stu-id="dcfde-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="dcfde-112">Przewiń do **pliku System. ServiceProcess. dll** , a następnie kliknij pozycję **Wybierz**.</span><span class="sxs-lookup"><span data-stu-id="dcfde-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="dcfde-113">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="dcfde-113">Click **OK**.</span></span>  
  
2. <span data-ttu-id="dcfde-114">Dodaj klasę i skonfiguruj ją, aby dziedziczyć <xref:System.ServiceProcess.ServiceBase>z:</span><span class="sxs-lookup"><span data-stu-id="dcfde-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="dcfde-115">Dodaj następujący kod, aby skonfigurować klasę usługi:</span><span class="sxs-lookup"><span data-stu-id="dcfde-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="dcfde-116">`Main` Utwórz metodę dla klasy i użyj jej do zdefiniowania usługi, która będzie zawierać Klasa; `userService1` jest nazwą klasy:</span><span class="sxs-lookup"><span data-stu-id="dcfde-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="dcfde-117">Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę i zdefiniuj wszelkie przetwarzanie, które mają być wykonywane, gdy usługa zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="dcfde-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="dcfde-118">Zastąp wszystkie inne metody, dla których chcesz zdefiniować niestandardowe przetwarzanie, i napisz kod, aby określić działania, które usługa powinna wykonać w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="dcfde-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="dcfde-119">Dodanie niezbędnych instalatorów dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="dcfde-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="dcfde-120">Aby uzyskać więcej informacji, zobacz [jak: Dodaj Instalatory do aplikacji](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)usługi.</span><span class="sxs-lookup"><span data-stu-id="dcfde-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="dcfde-121">Skompiluj projekt, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="dcfde-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="dcfde-122">Nie należy naciskać klawisza F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="dcfde-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="dcfde-123">Utwórz projekt konfiguracji i akcje niestandardowe w celu zainstalowania usługi.</span><span class="sxs-lookup"><span data-stu-id="dcfde-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="dcfde-124">Aby zapoznać się z przykładem, zobacz [Przewodnik: Tworzenie aplikacji usługi systemu Windows w projektancie](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)składników.</span><span class="sxs-lookup"><span data-stu-id="dcfde-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="dcfde-125">Zainstaluj usługę.</span><span class="sxs-lookup"><span data-stu-id="dcfde-125">Install the service.</span></span> <span data-ttu-id="dcfde-126">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)usług.</span><span class="sxs-lookup"><span data-stu-id="dcfde-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcfde-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcfde-127">See also</span></span>

- [<span data-ttu-id="dcfde-128">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dcfde-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="dcfde-129">Instrukcje: Tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dcfde-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="dcfde-130">Instrukcje: Dodawanie instalatorów do aplikacji usługi</span><span class="sxs-lookup"><span data-stu-id="dcfde-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="dcfde-131">Instrukcje: Rejestruj informacje o usługach</span><span class="sxs-lookup"><span data-stu-id="dcfde-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [<span data-ttu-id="dcfde-132">Przewodnik: Tworzenie aplikacji usługi systemu Windows w projektancie składników</span><span class="sxs-lookup"><span data-stu-id="dcfde-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
