---
title: 'Rozwiązywanie problemów: Aplikacja usług nie instaluje'
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
ms.openlocfilehash: ecbaa3b2fb0e0fc85ed383385368617bf361f497
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289442"
---
# <a name="troubleshooting-service-application-wont-install"></a>Rozwiązywanie problemów: Aplikacja usług nie instaluje
Jeśli Twoja aplikacja usługi nie zainstaluje się poprawnie, sprawdź, upewnij się, że <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość klasy usługi jest ustawiona na tę samą wartość, pokazane w Instalatorze za daną usługę. Wartość musi być taka sama w obu przypadkach, w kolejności dla usługi w taki sposób poprawnie zainstalować.  
  
> [!NOTE]
>  Można również przeglądać dzienniki instalacji, aby uzyskać opinie na temat procesu instalacji.  
  
 Również należy sprawdzić, czy masz inną usługę o takiej samej nazwie już zainstalowane. Nazwy usług musi być unikatowa instalacja się powiodła.  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
