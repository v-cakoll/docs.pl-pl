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
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583032"
---
# <a name="develop-windows-service-apps"></a>Tworzenie aplikacji usługi Windows

Za pomocą programu Visual Studio lub zestawu SDK programu .NET Framework, można łatwo tworzyć usługi, tworząc aplikację, która jest instalowana jako usługa. Ten typ aplikacji nosi nazwę usługi Windows. Dzięki funkcjom framework można tworzenie usług, ich zainstalowanie i uruchom, Zatrzymaj i kontrolować jego zachowanie.

> [!NOTE]
> W programie Visual Studio można utworzyć usługi w kodzie zarządzanym w Visual C# lub Visual Basic, który może współdziałać z istniejącego kodu C++, jeśli jest to wymagane. Lub można utworzyć usługi Windows w natywnym kodzie C++ za pomocą [Kreator projektów ATL](/cpp/atl/reference/atl-project-wizard).

## <a name="in-this-section"></a>W tej sekcji

[Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

Omówienie aplikacji usług Windows, okres istnienia usługi i jak aplikacji usług różni się od innych popularnych typów projektów.

[Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

Stanowi przykład tworzenia usługi w języka Visual Basic i Visual C#.

[Architektura programowania aplikacji usług](../../../docs/framework/windows-services/service-application-programming-architecture.md)

Opisano elementy języka używany w programowaniu usługi.

[Instrukcje: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)

W tym artykule opisano proces tworzenia i konfigurowania usług Windows przy użyciu szablonu projektu usługi Windows.

## <a name="related-sections"></a>Sekcje pokrewne

<xref:System.ServiceProcess.ServiceBase> — Zawiera opis najważniejszych funkcji <xref:System.ServiceProcess.ServiceBase> klasy, która jest używana do tworzenia usług.

<xref:System.ServiceProcess.ServiceProcessInstaller> — Opis funkcji <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, która jest używana wraz z <xref:System.ServiceProcess.ServiceInstaller> klasy do instalowania i odinstalowywania usługi.

<xref:System.ServiceProcess.ServiceInstaller> — Opis funkcji <xref:System.ServiceProcess.ServiceInstaller> klasy, która jest używana wraz z <xref:System.ServiceProcess.ServiceProcessInstaller> klasy do instalowania i odinstalowywania usługi.

[Twórz projekty na podstawie szablonów](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) — w tym artykule opisano projektów typów używanych w tym rozdziale oraz sposobu wybierania między nimi.
