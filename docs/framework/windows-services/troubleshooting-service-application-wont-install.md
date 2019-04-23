---
title: 'Rozwiązywanie problemów: Aplikacja usług nie instaluje się'
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
ms.openlocfilehash: f75a2f33ecde408d2d8e2f2343197ba56c4b8c21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143822"
---
# <a name="troubleshooting-service-application-wont-install"></a>Rozwiązywanie problemów: Aplikacja usług nie instaluje się
Jeśli Twoja aplikacja usługi nie zainstaluje się poprawnie, sprawdź, upewnij się, że <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość klasy usługi jest ustawiona na tę samą wartość, pokazane w Instalatorze za daną usługę. Wartość musi być taka sama w obu przypadkach, w kolejności dla usługi w taki sposób poprawnie zainstalować.  
  
> [!NOTE]
>  Można również przeglądać dzienniki instalacji, aby uzyskać opinie na temat procesu instalacji.  
  
 Również należy sprawdzić, czy masz inną usługę o takiej samej nazwie już zainstalowane. Nazwy usług musi być unikatowa instalacja się powiodła.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
