---
title: "Porady: programowane pisanie usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: cdb9c7bba564b71bfba86076218e48610cf73076
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="c220b-102">Porady: programowane pisanie usług</span><span class="sxs-lookup"><span data-stu-id="c220b-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="c220b-103">Jeśli wybierzesz nie użyć szablonu projektu usługi systemu Windows, można napisać własny usług przez ustawienie dziedziczenia i inne elementy infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="c220b-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="c220b-104">Podczas tworzenia usługi programowo, należy wykonać kilka kroków, które szablonu może obsłużyć w inny sposób można:</span><span class="sxs-lookup"><span data-stu-id="c220b-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
-   <span data-ttu-id="c220b-105">Należy skonfigurować klasie usługi odziedziczone <xref:System.ServiceProcess.ServiceBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="c220b-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
-   <span data-ttu-id="c220b-106">Należy utworzyć `Main` metody dla projektu usługi, który definiuje działanie usług i wywołania <xref:System.ServiceProcess.ServiceBase.Run%2A> metody na nich.</span><span class="sxs-lookup"><span data-stu-id="c220b-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
-   <span data-ttu-id="c220b-107">Konieczne jest przesłonięcie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur i wypełnij żadnego kodu mają się uruchomić.</span><span class="sxs-lookup"><span data-stu-id="c220b-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="c220b-108">Programowo zapisu usługi</span><span class="sxs-lookup"><span data-stu-id="c220b-108">To write a service programmatically</span></span>  
  
1.  <span data-ttu-id="c220b-109">Utwórz pusty projekt i utworzyć odwołania do przestrzeni nazw niezbędne wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c220b-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1.  <span data-ttu-id="c220b-110">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł i kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="c220b-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="c220b-111">Na **.NET Framework** karcie, przewiń do **System.dll** i kliknij przycisk **wybierz**.</span><span class="sxs-lookup"><span data-stu-id="c220b-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3.  <span data-ttu-id="c220b-112">Przewiń do **System.ServiceProcess.dll** i kliknij przycisk **wybierz**.</span><span class="sxs-lookup"><span data-stu-id="c220b-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4.  <span data-ttu-id="c220b-113">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="c220b-113">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="c220b-114">Dodaj klasę i skonfigurować go, aby dziedziczyć z <xref:System.ServiceProcess.ServiceBase>:</span><span class="sxs-lookup"><span data-stu-id="c220b-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  <span data-ttu-id="c220b-115">Dodaj następujący kod, aby skonfigurować klasie usługi:</span><span class="sxs-lookup"><span data-stu-id="c220b-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  <span data-ttu-id="c220b-116">Utwórz `Main` metody dla klasy i użyj go do zdefiniowania usługi będzie zawierać klasy; `userService1` jest nazwą klasy:</span><span class="sxs-lookup"><span data-stu-id="c220b-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  <span data-ttu-id="c220b-117">Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody i zdefiniuj jakiegokolwiek przetwarzania, które ma być wykonywana po uruchomieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="c220b-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  <span data-ttu-id="c220b-118">Zastąpienie innych metod, które chcesz zdefiniować niestandardowe przetwarzania dla i napisać kod, aby określić akcje, które usługi należy wykonać w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="c220b-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7.  <span data-ttu-id="c220b-119">Dodanie niezbędnych instalatorów dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="c220b-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="c220b-120">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="c220b-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8.  <span data-ttu-id="c220b-121">Tworzenie projektu, wybierając **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="c220b-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c220b-122">Nie naciśnij klawisz F5, aby uruchomić projekt — nie można uruchomić projekt usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="c220b-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="c220b-123">Tworzenie projektu Instalatora i akcje niestandardowe, aby zainstalować usługi.</span><span class="sxs-lookup"><span data-stu-id="c220b-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="c220b-124">Na przykład zobacz [wskazówki: tworzenie aplikacji usługi systemu Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="c220b-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="c220b-125">Zainstaluj usługę.</span><span class="sxs-lookup"><span data-stu-id="c220b-125">Install the service.</span></span> <span data-ttu-id="c220b-126">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="c220b-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c220b-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c220b-127">See Also</span></span>  
 [<span data-ttu-id="c220b-128">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c220b-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="c220b-129">Instrukcje: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c220b-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="c220b-130">Instrukcje: dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="c220b-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="c220b-131">Instrukcje: rejestrowanie informacji o usługach</span><span class="sxs-lookup"><span data-stu-id="c220b-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="c220b-132">Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="c220b-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
