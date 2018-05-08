---
title: 'Rozwiązywanie problemów: Usługa aplikacji kupione&#39;instalacji t'
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
manager: douge
ms.openlocfilehash: 1f3e5674f9a52627efdc24d6c70c0ab16dcdbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-service-application-won39t-install"></a>Rozwiązywanie problemów: Usługa aplikacji kupione&#39;instalacji t
Jeśli aplikacja usługi nie zainstaluje się poprawnie, sprawdź, upewnij się, że <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość klasy usługi jest ustawiona na tę samą wartość, przedstawioną w Instalatorze dla tej usługi. Wartość musi być taka sama w obu przypadkach, aby poprawnie zainstalować usługi.  
  
> [!NOTE]
>  Można również obejrzeć dzienniki instalacji, aby uzyskać opinię na temat procesu instalacji.  
  
 Należy także sprawdzić, czy masz inną usługę o takiej samej nazwie już zainstalowana. Nazwy usługi musi być unikatowa instalacja się powiodła.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
