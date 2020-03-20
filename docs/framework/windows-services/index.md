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
ms.openlocfilehash: 61f969c22ac06bd6ed20ccfa9124db3bb35d0692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71053540"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="a62b0-102">Tworzenie aplikacji usługowych systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a62b0-102">Develop Windows service apps</span></span>

<span data-ttu-id="a62b0-103">Za pomocą programu Visual Studio lub .NET Framework SDK, można łatwo tworzyć usługi, tworząc aplikację, która jest zainstalowana jako usługa.</span><span class="sxs-lookup"><span data-stu-id="a62b0-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="a62b0-104">Ten typ aplikacji jest nazywany usługą systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a62b0-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="a62b0-105">Za pomocą funkcji struktury można tworzyć usługi, instalować je i uruchamiać, zatrzymywać i w inny sposób kontrolować ich zachowanie.</span><span class="sxs-lookup"><span data-stu-id="a62b0-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="a62b0-106">W programie Visual Studio można utworzyć usługę w kodzie zarządzanym w języku Visual C# lub Visual Basic, która może współpracować z istniejącym kodem języka C++, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="a62b0-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="a62b0-107">Można też utworzyć usługę systemu Windows w natywnym języku C++ za pomocą [Kreatora projektów ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="a62b0-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a62b0-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a62b0-108">In this section</span></span>

[<span data-ttu-id="a62b0-109">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a62b0-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="a62b0-110">Zawiera omówienie aplikacji usługi systemu Windows, okres istnienia usługi i jak aplikacje usługi różnią się od innych typowych typów projektów.</span><span class="sxs-lookup"><span data-stu-id="a62b0-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="a62b0-111">Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="a62b0-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="a62b0-112">Zawiera przykład tworzenia usługi w języku Visual Basic i Visual C#.</span><span class="sxs-lookup"><span data-stu-id="a62b0-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="a62b0-113">Architektura programowania aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="a62b0-113">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="a62b0-114">W tym artykule wyjaśniono elementy języka używane w programowaniu usług.</span><span class="sxs-lookup"><span data-stu-id="a62b0-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="a62b0-115">Porady: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a62b0-115">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="a62b0-116">W tym artykule opisano proces tworzenia i konfigurowania usług systemu Windows przy użyciu szablonu projektu usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a62b0-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a62b0-117">Powiązane sekcje</span><span class="sxs-lookup"><span data-stu-id="a62b0-117">Related sections</span></span>

<span data-ttu-id="a62b0-118"><xref:System.ServiceProcess.ServiceBase>- Opisuje główne cechy <xref:System.ServiceProcess.ServiceBase> klasy, który jest używany do tworzenia usług.</span><span class="sxs-lookup"><span data-stu-id="a62b0-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="a62b0-119"><xref:System.ServiceProcess.ServiceProcessInstaller>- Opisuje funkcje <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, który jest <xref:System.ServiceProcess.ServiceInstaller> używany wraz z klasy, aby zainstalować i odinstalować usługi.</span><span class="sxs-lookup"><span data-stu-id="a62b0-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="a62b0-120"><xref:System.ServiceProcess.ServiceInstaller>- Opisuje funkcje <xref:System.ServiceProcess.ServiceInstaller> klasy, który jest <xref:System.ServiceProcess.ServiceProcessInstaller> używany wraz z klasy, aby zainstalować i odinstalować usługę.</span><span class="sxs-lookup"><span data-stu-id="a62b0-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="a62b0-121">[Utwórz projekty z szablonów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) — opisuje typy projektów używane w tym rozdziale i jak wybrać między nimi.</span><span class="sxs-lookup"><span data-stu-id="a62b0-121">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
