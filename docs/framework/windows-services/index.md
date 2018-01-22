---
title: "Tworzenie aplikacji usług systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 325e43f4b1734bc6ab8753285e5069f36b0fda51
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="865da-102">Tworzenie aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="865da-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="865da-103">Za pomocą programu Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] lub Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawu SDK, można łatwo utworzyć usług przez utworzenie aplikacji, która jest zainstalowany jako usługa.</span><span class="sxs-lookup"><span data-stu-id="865da-103">Using Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="865da-104">Ten typ aplikacji nosi nazwę usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="865da-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="865da-105">Z funkcjami framework można tworzenie usług, je zainstalować i uruchomić, zatrzymać i inny sposób kontroluje ich zachowanie.</span><span class="sxs-lookup"><span data-stu-id="865da-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="865da-106">Szablon usługi systemu Windows dla języka C++ nie została uwzględniona w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="865da-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="865da-107">Aby utworzyć usługi systemu Windows, możesz utworzyć usługi w kodzie zarządzanym w Visual C# lub Visual Basic, który może współpracować z istniejącego kodu C++, jeśli jest to wymagane, lub można utworzyć usługi systemu Windows w natywnym kodzie C++ za pomocą [Kreator projektu ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="865da-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="865da-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="865da-108">In This Section</span></span>  
 [<span data-ttu-id="865da-109">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="865da-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="865da-110">Zawiera omówienie aplikacji usług systemu Windows, okres istnienia usługi i jak aplikacje usług różnią się od innych typowych projektu.</span><span class="sxs-lookup"><span data-stu-id="865da-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="865da-111">Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="865da-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="865da-112">Stanowi przykład tworzenia usługi w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] i Visual C#.</span><span class="sxs-lookup"><span data-stu-id="865da-112">Provides an example of creating a service in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] and Visual C#.</span></span>  
  
 [<span data-ttu-id="865da-113">Architektura programowania aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="865da-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="865da-114">Opisano elementy języka używany w programowaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="865da-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="865da-115">Instrukcje: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="865da-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="865da-116">W tym artykule opisano proces tworzenia i konfigurowania usług systemu Windows przy użyciu szablonu projektu usług systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="865da-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="865da-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="865da-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="865da-118">Zawiera opis głównych funkcji <xref:System.ServiceProcess.ServiceBase> klasy, która jest używana do tworzenia usług.</span><span class="sxs-lookup"><span data-stu-id="865da-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="865da-119">Zawiera opis funkcji <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, która jest używana wraz z programem <xref:System.ServiceProcess.ServiceInstaller> klasy do instalowania i odinstalowywania usług.</span><span class="sxs-lookup"><span data-stu-id="865da-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="865da-120">Zawiera opis funkcji <xref:System.ServiceProcess.ServiceInstaller> klasy, która jest używana wraz z programem <xref:System.ServiceProcess.ServiceProcessInstaller> klasy do instalowania i odinstalowywania usługi.</span><span class="sxs-lookup"><span data-stu-id="865da-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="865da-121">NIB tworzenie projektów za pomocą szablonów</span><span class="sxs-lookup"><span data-stu-id="865da-121">NIB Creating Projects from Templates</span></span>](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="865da-122">W tym artykule opisano projektów typów używanych w tym rozdziale oraz sposobu wybierania między nimi.</span><span class="sxs-lookup"><span data-stu-id="865da-122">Describes the projects types used in this chapter and how to choose between them.</span></span>
