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
ms.openlocfilehash: af6e4bf7697b3139f6809295737fdd0d90b7f013
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="developing-windows-service-applications"></a>Tworzenie aplikacji usług systemu Windows
Za pomocą programu Microsoft Visual Studio lub Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawu SDK, można łatwo utworzyć usług przez utworzenie aplikacji, która jest zainstalowany jako usługa. Ten typ aplikacji nosi nazwę usługi systemu Windows. Z funkcjami framework można tworzenie usług, je zainstalować i uruchomić, zatrzymać i inny sposób kontroluje ich zachowanie.  
  
> [!WARNING]
>  Szablon usługi systemu Windows dla języka C++ nie została uwzględniona w programie Visual Studio 2010. Aby utworzyć usługi systemu Windows, możesz utworzyć usługi w kodzie zarządzanym w Visual C# lub Visual Basic, który może współpracować z istniejącego kodu C++, jeśli jest to wymagane, lub można utworzyć usługi systemu Windows w natywnym kodzie C++ za pomocą [Kreator projektu ATL](/cpp/atl/reference/atl-project-wizard).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 Zawiera omówienie aplikacji usług systemu Windows, okres istnienia usługi i jak aplikacje usług różnią się od innych typowych projektu.  
  
 [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 Przykład tworzenie usługi w języku Visual Basic i Visual C#.  
  
 [Architektura programowania aplikacji usług](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 Opisano elementy języka używany w programowaniu usługi.  
  
 [Instrukcje: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 W tym artykule opisano proces tworzenia i konfigurowania usług systemu Windows przy użyciu szablonu projektu usług systemu Windows.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 <xref:System.ServiceProcess.ServiceBase>  
 Zawiera opis głównych funkcji <xref:System.ServiceProcess.ServiceBase> klasy, która jest używana do tworzenia usług.  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 Zawiera opis funkcji <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, która jest używana wraz z programem <xref:System.ServiceProcess.ServiceInstaller> klasy do instalowania i odinstalowywania usług.  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 Zawiera opis funkcji <xref:System.ServiceProcess.ServiceInstaller> klasy, która jest używana wraz z programem <xref:System.ServiceProcess.ServiceProcessInstaller> klasy do instalowania i odinstalowywania usługi.  
  
 [NIB tworzenie projektów za pomocą szablonów](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 W tym artykule opisano projektów typów używanych w tym rozdziale oraz sposobu wybierania między nimi.
