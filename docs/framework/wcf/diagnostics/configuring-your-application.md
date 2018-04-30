---
title: Konfigurowanie własnej aplikacji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 170583239ed357904e723aebdaef9809938b5123
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-your-application"></a>Konfigurowanie własnej aplikacji
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] używa systemu konfiguracji platformy .NET i pozwala na skonfigurowanie usługi w zakresie komputera i aplikacji.  
  
 Konfiguracja ustawień zdefiniowanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] znajdują się w `<system.serviceModel>` grupy sekcji. Aby uzyskać więcej informacji o sposobie konfigurowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, zobacz następujące tematy:  
  
-   [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Ustawienia zdefiniowane przez aplikację konfiguracje są definiowane w `<appSettings>` grupy sekcji. Aby uzyskać więcej informacji o ustawieniach aplikacji w plikach konfiguracji platformy .NET, zobacz [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Za pomocą edytora konfiguracji  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umożliwia administratorów i deweloperów, tworzenie i modyfikowanie ustawień konfiguracji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług przy użyciu graficznego interfejsu użytkownika. Z tego narzędzia można zarządzać ustawieniami dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania zachowania, usług i diagnostyki bez konieczności bezpośredniego edytowania plików XML konfiguracji.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Edycję plików konfiguracyjnych w programie Visual Studio  
 Na edycję pliku konfiguracyjnego z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi projektu programu Visual Studio, kliknij prawym przyciskiem myszy w **Eksploratora rozwiązań** i wybierz polecenie **Edycja konfiguracji WCF** elementu menu kontekstowego. Spowoduje to uruchomienie [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Po zmodyfikowaniu pliku konfiguracyjnego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi sieci Web projektu programu Visual Studio, klikając go prawym przyciskiem myszy **Eksploratora rozwiązań**, zwróć uwagę, że **Edycja konfiguracji WCF** brakuje elementu menu kontekstowego. Obejście tego problemu, kliknij przycisk **narzędzia** menu i wybierz polecenie **Edytor konfiguracji usługi WCF**. Po tym, kliknij prawym przyciskiem myszy plik konfiguracji i użyj **Edycja konfiguracji WCF** elementu menu kontekstowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
