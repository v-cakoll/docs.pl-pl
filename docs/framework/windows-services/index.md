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
# <a name="develop-windows-service-apps"></a>Opracowywanie aplikacji usługi systemu Windows

Za pomocą programu Visual Studio lub zestawu SDK .NET Framework można łatwo tworzyć usługi, tworząc aplikację, która jest zainstalowana jako usługa. Ten typ aplikacji nazywa się usługą systemu Windows. Dzięki funkcjom platformy można tworzyć usługi, instalować je, uruchamiać, zatrzymywać i kontrolować ich zachowanie.

> [!NOTE]
> W programie Visual Studio można utworzyć usługę w kodzie zarządzanym w języku Visual C# lub Visual Basic, która może współdziałać z istniejącym kodem C++, jeśli jest to wymagane. Lub można utworzyć usługę systemu Windows w natywnym języku C++ przy użyciu [Kreatora projektu ATL](/cpp/atl/reference/atl-project-wizard).

## <a name="in-this-section"></a>W tej sekcji

[Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)

Zawiera omówienie aplikacji usług systemu Windows, okres istnienia usługi oraz sposób, w jaki aplikacje usług różnią się od innych typów projektów wspólnych.

[Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

Zawiera przykład tworzenia usługi w Visual Basic i Visual C#.

[Architektura programowania aplikacji usług](service-application-programming-architecture.md)

Wyjaśnia elementy języka używane w programowaniu usług.

[Porady: tworzenie usług systemu Windows](how-to-create-windows-services.md)

Opisuje proces tworzenia i konfigurowania usług systemu Windows przy użyciu szablonu projektu usługi systemu Windows.

## <a name="related-sections"></a>Sekcje pokrewne

<xref:System.ServiceProcess.ServiceBase>— Zawiera opis głównych funkcji <xref:System.ServiceProcess.ServiceBase> klasy, które są używane do tworzenia usług.

<xref:System.ServiceProcess.ServiceProcessInstaller>-Opisuje funkcje <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, która jest używana razem z <xref:System.ServiceProcess.ServiceInstaller> klasą do instalowania i odinstalowywania usług.

<xref:System.ServiceProcess.ServiceInstaller>-Opisuje funkcje <xref:System.ServiceProcess.ServiceInstaller> klasy, która jest używana razem z <xref:System.ServiceProcess.ServiceProcessInstaller> klasą do instalowania i odinstalowywania usługi.

[Tworzenie projektów z szablonów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) — zawiera opis typów projektów używanych w tym rozdziale oraz sposób wybierania między nimi.
