---
title: 'Rozwiązywanie problemów: Usługi aplikacji kupione&#39;instalować'
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
ms.openlocfilehash: 0912ff0909ffa5b22bed07543a2e514de4fb1ff5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084491"
---
# <a name="troubleshooting-service-application-won39t-install"></a>Rozwiązywanie problemów: Usługi aplikacji kupione&#39;instalować
Jeśli Twoja aplikacja usługi nie zainstaluje się poprawnie, sprawdź, upewnij się, że <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość klasy usługi jest ustawiona na tę samą wartość, pokazane w Instalatorze za daną usługę. Wartość musi być taka sama w obu przypadkach, w kolejności dla usługi w taki sposób poprawnie zainstalować.  
  
> [!NOTE]
>  Można również przeglądać dzienniki instalacji, aby uzyskać opinie na temat procesu instalacji.  
  
 Również należy sprawdzić, czy masz inną usługę o takiej samej nazwie już zainstalowane. Nazwy usług musi być unikatowa instalacja się powiodła.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
