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
ms.openlocfilehash: f0affeabba90e1d4cdc559cb96dee2dafe0bea77
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073991"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="8b7c1-102">Instrukcje: Programowane pisanie usług</span><span class="sxs-lookup"><span data-stu-id="8b7c1-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="8b7c1-103">Jeśli nie chcesz użyć szablonu projektu usługi Windows, można napisać własne usługi, ustawiając dziedziczenia i inne elementy infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="8b7c1-104">Programowo utworzyć usługę, należy wykonać kilka kroków, które szablon w przeciwnym razie będzie obsługiwać dla Ciebie:</span><span class="sxs-lookup"><span data-stu-id="8b7c1-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
-   <span data-ttu-id="8b7c1-105">Należy zdefiniować klasie usługi, aby odziedziczyć po <xref:System.ServiceProcess.ServiceBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
-   <span data-ttu-id="8b7c1-106">Należy utworzyć `Main` metoda projekt usługi, który definiuje działanie usług i wywołania <xref:System.ServiceProcess.ServiceBase.Run%2A> metody na nich.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
-   <span data-ttu-id="8b7c1-107">Konieczne jest przesłonięcie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur i wypełnij jakiegokolwiek kodu, który ma ich wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="8b7c1-108">Aby programowane pisanie usług</span><span class="sxs-lookup"><span data-stu-id="8b7c1-108">To write a service programmatically</span></span>  
  
1.  <span data-ttu-id="8b7c1-109">Utwórz pusty projekt, a następnie utwórz odwołanie do przestrzeni nazw niezbędne wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8b7c1-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1.  <span data-ttu-id="8b7c1-110">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzła i kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="8b7c1-111">Na **.NET Framework** karty, przewiń do **System.dll** i kliknij przycisk **wybierz**.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3.  <span data-ttu-id="8b7c1-112">Przewiń do **System.ServiceProcess.dll** i kliknij przycisk **wybierz**.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4.  <span data-ttu-id="8b7c1-113">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-113">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="8b7c1-114">Dodaj klasę i skonfiguruj ją, aby dziedziczyć <xref:System.ServiceProcess.ServiceBase>:</span><span class="sxs-lookup"><span data-stu-id="8b7c1-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  <span data-ttu-id="8b7c1-115">Dodaj następujący kod, aby skonfigurować klasie usługi:</span><span class="sxs-lookup"><span data-stu-id="8b7c1-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  <span data-ttu-id="8b7c1-116">Utwórz `Main` metody dla swojej klasy i użyj go do zdefiniowania usługi będzie zawierać klasy; `userService1` jest nazwa klasy:</span><span class="sxs-lookup"><span data-stu-id="8b7c1-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  <span data-ttu-id="8b7c1-117">Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody i zdefiniuj jakiegokolwiek przetwarzania, które ma być wykonywana po uruchomieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  <span data-ttu-id="8b7c1-118">Zastąpienie wszelkich innych metod, które użytkownik chce zdefiniować niestandardowe przetwarzanie i pisanie kodu w celu ustalenia, jakie działania, które usługa należy wykonać w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7.  <span data-ttu-id="8b7c1-119">Dodanie niezbędnych instalatorów dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="8b7c1-120">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="8b7c1-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8.  <span data-ttu-id="8b7c1-121">Kompilowanie projektu przez wybranie **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b7c1-122">Nie wciskaj F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="8b7c1-123">Tworzenie projektu Instalatora i akcje niestandardowe, aby zainstalować usługę.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="8b7c1-124">Aby uzyskać przykład, zobacz [instruktażu: Tworzenie Windows usługi aplikacji w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="8b7c1-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="8b7c1-125">Zainstaluj usługę.</span><span class="sxs-lookup"><span data-stu-id="8b7c1-125">Install the service.</span></span> <span data-ttu-id="8b7c1-126">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="8b7c1-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7c1-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b7c1-127">See also</span></span>

- [<span data-ttu-id="8b7c1-128">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8b7c1-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="8b7c1-129">Instrukcje: Tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8b7c1-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="8b7c1-130">Instrukcje: Dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="8b7c1-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="8b7c1-131">Instrukcje: Rejestrowanie informacji o usługach</span><span class="sxs-lookup"><span data-stu-id="8b7c1-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [<span data-ttu-id="8b7c1-132">Przewodnik: Tworzenie aplikacji usługi Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="8b7c1-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
