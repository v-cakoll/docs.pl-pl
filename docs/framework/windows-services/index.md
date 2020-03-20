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
# <a name="develop-windows-service-apps"></a>Tworzenie aplikacji usługowych systemu Windows

Za pomocą programu Visual Studio lub .NET Framework SDK, można łatwo tworzyć usługi, tworząc aplikację, która jest zainstalowana jako usługa. Ten typ aplikacji jest nazywany usługą systemu Windows. Za pomocą funkcji struktury można tworzyć usługi, instalować je i uruchamiać, zatrzymywać i w inny sposób kontrolować ich zachowanie.

> [!NOTE]
> W programie Visual Studio można utworzyć usługę w kodzie zarządzanym w języku Visual C# lub Visual Basic, która może współpracować z istniejącym kodem języka C++, jeśli jest to wymagane. Można też utworzyć usługę systemu Windows w natywnym języku C++ za pomocą [Kreatora projektów ATL](/cpp/atl/reference/atl-project-wizard).

## <a name="in-this-section"></a>W tej sekcji

[Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)

Zawiera omówienie aplikacji usługi systemu Windows, okres istnienia usługi i jak aplikacje usługi różnią się od innych typowych typów projektów.

[Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

Zawiera przykład tworzenia usługi w języku Visual Basic i Visual C#.

[Architektura programowania aplikacji usług](service-application-programming-architecture.md)

W tym artykule wyjaśniono elementy języka używane w programowaniu usług.

[Porady: tworzenie usług systemu Windows](how-to-create-windows-services.md)

W tym artykule opisano proces tworzenia i konfigurowania usług systemu Windows przy użyciu szablonu projektu usługi systemu Windows.

## <a name="related-sections"></a>Powiązane sekcje

<xref:System.ServiceProcess.ServiceBase>- Opisuje główne cechy <xref:System.ServiceProcess.ServiceBase> klasy, który jest używany do tworzenia usług.

<xref:System.ServiceProcess.ServiceProcessInstaller>- Opisuje funkcje <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, który jest <xref:System.ServiceProcess.ServiceInstaller> używany wraz z klasy, aby zainstalować i odinstalować usługi.

<xref:System.ServiceProcess.ServiceInstaller>- Opisuje funkcje <xref:System.ServiceProcess.ServiceInstaller> klasy, który jest <xref:System.ServiceProcess.ServiceProcessInstaller> używany wraz z klasy, aby zainstalować i odinstalować usługę.

[Utwórz projekty z szablonów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) — opisuje typy projektów używane w tym rozdziale i jak wybrać między nimi.
