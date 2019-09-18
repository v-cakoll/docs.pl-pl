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
ms.openlocfilehash: c45ab03ec4577d88953b0e43531082a46c29e8fd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053535"
---
# <a name="troubleshooting-service-application-wont-install"></a>Rozwiązywanie problemów: Aplikacja usług nie instaluje się
Jeśli aplikacja usługi nie zostanie prawidłowo zainstalowana, upewnij się, że <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość klasy usługi jest ustawiona na taką samą wartość jak w instalatorze dla tej usługi. Wartość musi być taka sama w obu wystąpieniach, aby można było poprawnie zainstalować usługę.  
  
> [!NOTE]
> Możesz również zapoznać się z dziennikami instalacji, aby uzyskać informacje na temat procesu instalacji.  
  
 Należy również sprawdzić, czy masz już zainstalowaną inną usługę o tej samej nazwie. Aby instalacja powiodła się, nazwy usług muszą być unikatowe.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
