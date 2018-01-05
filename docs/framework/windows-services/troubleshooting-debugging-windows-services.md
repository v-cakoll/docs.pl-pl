---
title: "Rozwiązywanie problemów: debugowanie usług systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: f38e65e93d4e6668795bf254573993d5100e2328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-debugging-windows-services"></a>Rozwiązywanie problemów: debugowanie usług systemu Windows
Podczas debugowania aplikacji usługi systemu Windows, usługi i **Windows Service Manager** interakcji. **Programu Service Manager** uruchamia usługi przez wywołanie metody <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, a następnie czeka 30 sekund na <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody do zwrócenia. Jeśli metoda nie zwraca w tym okresie, Menedżer pokazuje błąd, nie można uruchomić usługi.  
  
 Podczas debugowania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody zgodnie z opisem w [porady: debugowanie aplikacji usług systemu Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), należy pamiętać o tym okres 30 sekund. Jeśli punkt przerwania w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> — metoda i przy jego użyciu nie krok w ciągu 30 sekund, nie można uruchomić Menedżera usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: debugowanie aplikacji usług systemu Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
