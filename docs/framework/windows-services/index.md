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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053540"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="70046-102">Opracowywanie aplikacji usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="70046-102">Develop Windows service apps</span></span>

<span data-ttu-id="70046-103">Za pomocą programu Visual Studio lub zestawu SDK .NET Framework można łatwo tworzyć usługi, tworząc aplikację, która jest zainstalowana jako usługa.</span><span class="sxs-lookup"><span data-stu-id="70046-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="70046-104">Ten typ aplikacji nazywa się usługą systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="70046-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="70046-105">Dzięki funkcjom platformy można tworzyć usługi, instalować je, uruchamiać, zatrzymywać i kontrolować ich zachowanie.</span><span class="sxs-lookup"><span data-stu-id="70046-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="70046-106">W programie Visual Studio można utworzyć usługę w kodzie zarządzanym w wizualizacji C# lub Visual Basic, która może współdziałać z istniejącym C++ kodem, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="70046-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="70046-107">Lub można utworzyć usługę systemu Windows w trybie macierzystym C++ przy użyciu [Kreatora projektu ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="70046-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="70046-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="70046-108">In this section</span></span>

[<span data-ttu-id="70046-109">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="70046-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="70046-110">Zawiera omówienie aplikacji usług systemu Windows, okres istnienia usługi oraz sposób, w jaki aplikacje usług różnią się od innych typów projektów wspólnych.</span><span class="sxs-lookup"><span data-stu-id="70046-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="70046-111">Przewodnik: Tworzenie aplikacji usługi systemu Windows w projektancie składników</span><span class="sxs-lookup"><span data-stu-id="70046-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="70046-112">Zawiera przykład tworzenia usługi w Visual Basic i wizualizacji C#.</span><span class="sxs-lookup"><span data-stu-id="70046-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="70046-113">Architektura programowania aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="70046-113">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="70046-114">Wyjaśnia elementy języka używane w programowaniu usług.</span><span class="sxs-lookup"><span data-stu-id="70046-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="70046-115">Instrukcje: Tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="70046-115">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="70046-116">Opisuje proces tworzenia i konfigurowania usług systemu Windows przy użyciu szablonu projektu usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="70046-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="70046-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="70046-117">Related sections</span></span>

<span data-ttu-id="70046-118"><xref:System.ServiceProcess.ServiceBase>— Zawiera opis głównych funkcji <xref:System.ServiceProcess.ServiceBase> klasy, które są używane do tworzenia usług.</span><span class="sxs-lookup"><span data-stu-id="70046-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="70046-119"><xref:System.ServiceProcess.ServiceProcessInstaller>-Opisuje funkcje <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, która jest używana razem <xref:System.ServiceProcess.ServiceInstaller> z klasą do instalowania i odinstalowywania usług.</span><span class="sxs-lookup"><span data-stu-id="70046-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="70046-120"><xref:System.ServiceProcess.ServiceInstaller>-Opisuje funkcje <xref:System.ServiceProcess.ServiceInstaller> klasy, która jest używana razem <xref:System.ServiceProcess.ServiceProcessInstaller> z klasą do instalowania i odinstalowywania usługi.</span><span class="sxs-lookup"><span data-stu-id="70046-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="70046-121">[Tworzenie projektów z szablonów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) — zawiera opis typów projektów używanych w tym rozdziale oraz sposób wybierania między nimi.</span><span class="sxs-lookup"><span data-stu-id="70046-121">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
