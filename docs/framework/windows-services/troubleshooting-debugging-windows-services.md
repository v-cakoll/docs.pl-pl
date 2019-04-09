---
title: 'Rozwiązywanie problemów: Debugowanie usług Windows'
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
ms.openlocfilehash: 0552fc005a25e83065bb44e425770f9cef84f71b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082584"
---
# <a name="troubleshooting-debugging-windows-services"></a>Rozwiązywanie problemów: Debugowanie usług Windows
Podczas debugowania aplikacji usługi Windows, usługi i **Windows Service Manager** wchodzić w interakcje. **Programu Service Manager** uruchamia usługi, wywołując <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, a następnie czeka 30 sekund w przypadku <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody do zwrócenia. Jeśli metoda nie zwraca w tym okresie, Menedżer pokazuje błąd, nie można uruchomić usługi.  
  
 Podczas debugowania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda zgodnie z opisem w [jak: Debugowanie aplikacji usług Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), należy pamiętać o tym okresie 30 sekund. Jeśli umieścisz punkt przerwania w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody i nie wkraczaj przez nią w ciągu 30 sekund, nie można uruchomić Menedżera usługi.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Debugowanie aplikacji usług systemu Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
