---
title: 'Rozwiązywanie problemów: Debugowanie usług systemu Windows'
ms.date: 03/30/2017
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
author: ghogen
ms.openlocfilehash: cbedb0051cbb08c2875e145a2bad35ae4d02a74e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053510"
---
# <a name="troubleshooting-debugging-windows-services"></a>Rozwiązywanie problemów: Debugowanie usług systemu Windows
Gdy debugujesz aplikację usługi systemu Windows, usługa i **Service Manager systemu Windows** współpracują. **Service Manager** uruchamia usługę, wywołując <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę, a następnie czeka <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 30 sekund na zwrócenie metody. Jeśli metoda nie zwróci tego czasu, Menedżer pokazuje błąd, że nie można uruchomić usługi.  
  
 Podczas debugowania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody zgodnie z opisem w [temacie How to: Debuguj aplikacje](how-to-debug-windows-service-applications.md)usług systemu Windows, musisz mieć świadomość, że ten 30-sekundowy okres. Jeśli umieścisz punkt przerwania w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodzie i nie ustawisz go w ciągu 30 sekund, Menedżer nie uruchomi usługi.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Debuguj aplikacje usług systemu Windows](how-to-debug-windows-service-applications.md)
- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
