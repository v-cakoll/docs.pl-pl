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
# <a name="developing-windows-service-applications"></a>Tworzenie aplikacji usług systemu Windows
Za pomocą programu Microsoft Visual Studio lub Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawu SDK, możesz łatwo tworzyć usługi, tworząc aplikację, która jest instalowana jako usługa. Ten typ aplikacji nosi nazwę usługi Windows. Dzięki funkcjom framework można tworzenie usług, ich zainstalowanie i uruchom, Zatrzymaj i kontrolować jego zachowanie.  
  
> [!WARNING]
>  Szablon usługi Windows dla języka C++ nie została uwzględniona w programie Visual Studio 2010. Aby utworzyć usługę Windows, możesz utworzyć usługi w kodzie zarządzanym w Visual C# lub Visual Basic, który może współdziałać z istniejącego kodu C++, jeśli jest to wymagane, lub utworzyć usługę Windows w natywnym kodzie C++ przy użyciu [Kreator projektów ATL](/cpp/atl/reference/atl-project-wizard).  
  
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
 <xref:System.ServiceProcess.ServiceBase>  
 W tym artykule opisano główne funkcje <xref:System.ServiceProcess.ServiceBase> klasy, która jest używana do tworzenia usług.  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 W tym artykule opisano funkcje <xref:System.ServiceProcess.ServiceProcessInstaller> klasy, która jest używana wraz z <xref:System.ServiceProcess.ServiceInstaller> klasy do instalowania i odinstalowywania usługi.  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 W tym artykule opisano funkcje <xref:System.ServiceProcess.ServiceInstaller> klasy, która jest używana wraz z <xref:System.ServiceProcess.ServiceProcessInstaller> klasy do instalowania i odinstalowywania usługi.  
  
 [NIB tworzenie projektów z szablonów](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 W tym artykule opisano projektów typów używanych w tym rozdziale oraz sposobu wybierania między nimi.
