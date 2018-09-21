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
ms.openlocfilehash: aa5e18f7e0ee1fc0836054b692872b18678106f3
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481731"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="01487-102">Tworzenie aplikacji usługi Windows</span><span class="sxs-lookup"><span data-stu-id="01487-102">Develop Windows service apps</span></span>

<span data-ttu-id="01487-103">Za pomocą programu Visual Studio lub zestawu SDK programu .NET Framework, można łatwo tworzyć usługi, tworząc aplikację, która jest instalowana jako usługa.</span><span class="sxs-lookup"><span data-stu-id="01487-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="01487-104">Ten typ aplikacji nosi nazwę usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="01487-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="01487-105">Dzięki funkcjom framework można tworzenie usług, ich zainstalowanie i uruchom, Zatrzymaj i kontrolować jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="01487-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="01487-106">W programie Visual Studio można utworzyć usługi w kodzie zarządzanym w Visual C# lub Visual Basic, który może współdziałać z istniejącego kodu C++, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="01487-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="01487-107">Lub można utworzyć usługi Windows w natywnym kodzie C++ za pomocą [Kreator projektów ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="01487-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="01487-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="01487-108">In this section</span></span>

[<span data-ttu-id="01487-109">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="01487-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

<span data-ttu-id="01487-110">Omówienie aplikacji usług Windows, okres istnienia usługi i jak aplikacji usług różni się od innych popularnych typów projektów.</span><span class="sxs-lookup"><span data-stu-id="01487-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="01487-111">Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="01487-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="01487-112">Stanowi przykład tworzenia usługi w języka Visual Basic i Visual C#.</span><span class="sxs-lookup"><span data-stu-id="01487-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="01487-113">Architektura programowania aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="01487-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)

<span data-ttu-id="01487-114">Opisano elementy języka używany w programowaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="01487-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="01487-115">Instrukcje: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="01487-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

<span data-ttu-id="01487-116">W tym artykule opisano proces tworzenia i konfigurowania usług Windows przy użyciu szablonu projektu usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="01487-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="01487-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="01487-117">Related sections</span></span>

<span data-ttu-id="01487-118"><xref:System.ServiceProcess.ServiceBase> — Zawiera opis najważniejszych funkcji <xref:System.ServiceProcess.ServiceBase> klasy, która jest używana do tworzenia usług.</span><span class="sxs-lookup"><span data-stu-id="01487-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="01487-119"><xref:System.ServiceProcess.ServiceProcessInstaller> — Opis funkcji <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, która jest używana wraz z <xref:System.ServiceProcess.ServiceInstaller> klasy do instalowania i odinstalowywania usługi.</span><span class="sxs-lookup"><span data-stu-id="01487-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="01487-120"><xref:System.ServiceProcess.ServiceInstaller> — Opis funkcji <xref:System.ServiceProcess.ServiceInstaller> klasy, która jest używana wraz z <xref:System.ServiceProcess.ServiceProcessInstaller> klasy do instalowania i odinstalowywania usługi.</span><span class="sxs-lookup"><span data-stu-id="01487-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="01487-121">[Twórz projekty na podstawie szablonów](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) — w tym artykule opisano projektów typów używanych w tym rozdziale oraz sposobu wybierania między nimi.</span><span class="sxs-lookup"><span data-stu-id="01487-121">[Create Projects from Templates](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
