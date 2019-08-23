---
title: Konfigurowanie własnej aplikacji
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: e096f4b64ada8b142e8b82c8877eec7f1b84637c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939811"
---
# <a name="configuring-your-application"></a>Konfigurowanie własnej aplikacji
Windows Communication Foundation (WCF) korzysta z systemu konfiguracji platformy .NET i umożliwia konfigurowanie usług zarówno w zakresie komputera, jak i aplikacji.  
  
 Ustawienia konfiguracji zdefiniowane przez funkcję WCF znajdują się `<system.serviceModel>` w grupie sekcji. Więcej informacji o sposobie konfigurowania usługi WCF znajduje się w następujących tematach:  
  
- [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
  
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Ustawienia konfiguracji zdefiniowane przez aplikację są zdefiniowane w `<appSettings>` grupie sekcji. Aby uzyskać więcej informacji na temat ustawień aplikacji w plikach konfiguracji platformy .NET, zobacz [ \<AppSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Korzystanie z edytora konfiguracji  
 [Narzędzie Edytor konfiguracji WCF (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umożliwia administratorom i deweloperom tworzenie i modyfikowanie ustawień konfiguracji usług WCF przy użyciu graficznego interfejsu użytkownika. Za pomocą tego narzędzia można zarządzać ustawieniami powiązań programu WCF, zachowań, usług i diagnostyki bez bezpośredniego edytowania plików konfiguracji XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Edytowanie plików konfiguracji w programie Visual Studio  
 Aby edytować plik konfiguracji projektu usługi WCF w programie Visual Studio, kliknij prawym przyciskiem myszy w **Eksplorator rozwiązań** i wybierz pozycję **Edytuj kontekst konfiguracji WCF** . Spowoduje to uruchomienie [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
> Jeśli edytujesz plik konfiguracyjny projektu usługi sieci Web WCF w programie Visual Studio, klikając go prawym przyciskiem myszy w **Eksplorator rozwiązań**, Zauważ, że brakuje elementu menu kontekstowego **konfiguracji WCF** . Aby obejść ten problem, kliknij menu **Narzędzia** , a następnie wybierz pozycję **Edytor konfiguracji usługi WCF**. Następnie możesz kliknąć prawym przyciskiem myszy plik konfiguracyjny i użyć elementu menu kontekstowego **edytowania konfiguracji WCF** .  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
