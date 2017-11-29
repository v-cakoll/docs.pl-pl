---
title: "Konfigurowanie własnej aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f22fac02616070ecd6498ad0e158782001681ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-your-application"></a>Konfigurowanie własnej aplikacji
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]używa systemu konfiguracji platformy .NET i pozwala na skonfigurowanie usługi w zakresie komputera i aplikacji.  
  
 Konfiguracja ustawień zdefiniowanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] znajdują się w `<system.serviceModel>` grupy sekcji. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, zobacz następujące tematy:  
  
-   [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Ustawienia zdefiniowane przez aplikację konfiguracje są definiowane w `<appSettings>` grupy sekcji. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Ustawienia aplikacji w plikach konfiguracji platformy .NET, zobacz [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Za pomocą edytora konfiguracji  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umożliwia administratorów i deweloperów, tworzenie i modyfikowanie ustawień konfiguracji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług przy użyciu graficznego interfejsu użytkownika. Z tego narzędzia można zarządzać ustawieniami dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania zachowania, usług i diagnostyki bez konieczności bezpośredniego edytowania plików XML konfiguracji.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Edycję plików konfiguracyjnych w programie Visual Studio  
 Na edycję pliku konfiguracyjnego z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projekt usługi w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], kliknij prawym przyciskiem myszy w **Eksploratora rozwiązań** i wybierz polecenie **Edycja konfiguracji WCF** elementu menu kontekstowego. Spowoduje to uruchomienie [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Po zmodyfikowaniu pliku konfiguracyjnego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projekt usługi sieci Web w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] klikając prawym przyciskiem myszy w **Eksploratora rozwiązań**, zwróć uwagę, że **Edycja konfiguracji WCF** brakuje elementu menu kontekstowego . Obejście tego problemu, kliknij przycisk **narzędzia** menu i wybierz polecenie **Edytor konfiguracji usługi WCF**. Po tym, kliknij prawym przyciskiem myszy plik konfiguracji i użyj **Edycja konfiguracji WCF** elementu menu kontekstowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
