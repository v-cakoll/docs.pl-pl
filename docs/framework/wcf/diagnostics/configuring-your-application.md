---
title: Konfigurowanie własnej aplikacji
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 6fc33e7b114bb78f823575a2b456d601ae75db94
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937640"
---
# <a name="configuring-your-application"></a>Konfigurowanie własnej aplikacji
Windows Communication Foundation (WCF) korzysta z systemu konfiguracji platformy .NET i umożliwia konfigurowanie usług zarówno w zakresie komputera, jak i aplikacji.  
  
 Ustawienia konfiguracji zdefiniowane przez funkcję WCF znajdują się w grupie sekcji `<system.serviceModel>`. Więcej informacji o sposobie konfigurowania usługi WCF znajduje się w następujących tematach:  
  
- [Konfigurowanie usług](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Ustawienia konfiguracji zdefiniowane przez aplikację są zdefiniowane w grupie sekcji `<appSettings>`. Aby uzyskać więcej informacji na temat ustawień aplikacji w plikach konfiguracji platformy .NET, zobacz [\<appSettings >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)).  
  
## <a name="using-the-configuration-editor"></a>Korzystanie z edytora konfiguracji  
 [Narzędzie Edytor konfiguracji WCF (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) umożliwia administratorom i deweloperom tworzenie i modyfikowanie ustawień konfiguracji usług WCF przy użyciu graficznego interfejsu użytkownika. Za pomocą tego narzędzia można zarządzać ustawieniami powiązań programu WCF, zachowań, usług i diagnostyki bez bezpośredniego edytowania plików konfiguracji XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Edytowanie plików konfiguracji w programie Visual Studio  
 Aby edytować plik konfiguracji projektu usługi WCF w programie Visual Studio, kliknij prawym przyciskiem myszy w **Eksplorator rozwiązań** i wybierz pozycję **Edytuj kontekst konfiguracji WCF** . Spowoduje to uruchomienie [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
> Jeśli edytujesz plik konfiguracyjny projektu usługi sieci Web WCF w programie Visual Studio, klikając go prawym przyciskiem myszy w **Eksplorator rozwiązań**, Zauważ, że brakuje elementu menu kontekstowego **konfiguracji WCF** . Aby obejść ten problem, kliknij menu **Narzędzia** , a następnie wybierz pozycję **Edytor konfiguracji usługi WCF**. Następnie możesz kliknąć prawym przyciskiem myszy plik konfiguracyjny i użyć elementu menu kontekstowego **edytowania konfiguracji WCF** .  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [Konfigurowanie usług](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
