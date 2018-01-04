---
title: "Rozwiązywanie problemów: Kupione aplikacji usługi &#39; instalacji t"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 43c973d83d2d1b614cf0ce49ba8d4af24123b47e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-service-application-won39t-install"></a>Rozwiązywanie problemów: Kupione aplikacji usługi &#39; instalacji t
Jeśli aplikacja usługi nie zainstaluje się poprawnie, sprawdź, upewnij się, że <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość klasy usługi jest ustawiona na tę samą wartość, przedstawioną w Instalatorze dla tej usługi. Wartość musi być taka sama w obu przypadkach, aby poprawnie zainstalować usługi.  
  
> [!NOTE]
>  Można również obejrzeć dzienniki instalacji, aby uzyskać opinię na temat procesu instalacji.  
  
 Należy także sprawdzić, czy masz inną usługę o takiej samej nazwie już zainstalowana. Nazwy usługi musi być unikatowa instalacja się powiodła.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
