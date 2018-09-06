---
title: Tworzenie aplikacji usług systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: 2c7fb148b96d5ff9804bcb0bb7c842c475c0f117
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740833"
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="ede61-102">Tworzenie aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ede61-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="ede61-103">Za pomocą programu Microsoft Visual Studio lub Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawu SDK, możesz łatwo tworzyć usługi, tworząc aplikację, która jest instalowana jako usługa.</span><span class="sxs-lookup"><span data-stu-id="ede61-103">Using Microsoft Visual Studio or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="ede61-104">Ten typ aplikacji nosi nazwę usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="ede61-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="ede61-105">Dzięki funkcjom framework można tworzenie usług, ich zainstalowanie i uruchom, Zatrzymaj i kontrolować jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ede61-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ede61-106">Szablon usługi Windows dla języka C++ nie została uwzględniona w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="ede61-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="ede61-107">Aby utworzyć usługę Windows, możesz utworzyć usługi w kodzie zarządzanym w Visual C# lub Visual Basic, który może współdziałać z istniejącego kodu C++, jeśli jest to wymagane, lub utworzyć usługę Windows w natywnym kodzie C++ przy użyciu [Kreator projektów ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="ede61-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ede61-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ede61-108">In This Section</span></span>  
 [<span data-ttu-id="ede61-109">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ede61-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="ede61-110">Omówienie aplikacji usług Windows, okres istnienia usługi i jak aplikacji usług różni się od innych popularnych typów projektów.</span><span class="sxs-lookup"><span data-stu-id="ede61-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="ede61-111">Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="ede61-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="ede61-112">Stanowi przykład tworzenia usługi w języka Visual Basic i Visual C#.</span><span class="sxs-lookup"><span data-stu-id="ede61-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>  
  
 [<span data-ttu-id="ede61-113">Architektura programowania aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="ede61-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="ede61-114">Opisano elementy języka używany w programowaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="ede61-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="ede61-115">Instrukcje: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ede61-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="ede61-116">W tym artykule opisano proces tworzenia i konfigurowania usług Windows przy użyciu szablonu projektu usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="ede61-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ede61-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ede61-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="ede61-118">W tym artykule opisano główne funkcje <xref:System.ServiceProcess.ServiceBase> klasy, która jest używana do tworzenia usług.</span><span class="sxs-lookup"><span data-stu-id="ede61-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="ede61-119">W tym artykule opisano funkcje <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, która jest używana wraz z <xref:System.ServiceProcess.ServiceInstaller> klasy do instalowania i odinstalowywania usługi.</span><span class="sxs-lookup"><span data-stu-id="ede61-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="ede61-120">W tym artykule opisano funkcje <xref:System.ServiceProcess.ServiceInstaller> klasy, która jest używana wraz z <xref:System.ServiceProcess.ServiceProcessInstaller> klasy do instalowania i odinstalowywania usługi.</span><span class="sxs-lookup"><span data-stu-id="ede61-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="ede61-121">NIB tworzenie projektów z szablonów</span><span class="sxs-lookup"><span data-stu-id="ede61-121">NIB Creating Projects from Templates</span></span>](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="ede61-122">W tym artykule opisano projektów typów używanych w tym rozdziale oraz sposobu wybierania między nimi.</span><span class="sxs-lookup"><span data-stu-id="ede61-122">Describes the projects types used in this chapter and how to choose between them.</span></span>
