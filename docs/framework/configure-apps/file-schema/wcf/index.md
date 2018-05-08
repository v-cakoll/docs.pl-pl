---
title: Schemat konfiguracji programu WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: bcbc12d35dae59fcd43d5fbf2d4c936c8e4a4423
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-configuration-schema"></a>Schemat konfiguracji programu WCF
Elementy konfiguracji systemu Windows Communication Foundation (WCF) umożliwiają skonfigurowanie WCF usługi i aplikacje klienckie. Można użyć [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pozwala tworzyć i modyfikować pliki konfiguracyjne dla klientów i usług. Ponieważ pliki konfiguracji są w formacie XML, należy zapoznać się z XML, jeśli chcesz ręcznie edytować za pomocą edytora tekstu. W przeciwnym razie może wystąpić problemy, takie jak unfound tagu elementu XML lub atrybut. Wynika to z tagów elementu XML i atrybutów jest rozróżniana wielkość liter.  
  
 System konfiguracji usługi WCF jest oparty na <xref:System.Configuration> przestrzeni nazw. W takim przypadku używane standardowe funkcje oferowane przez <xref:System.Configuration> przestrzeni nazw, takie jak konfiguracja, blokowanie, szyfrowania i scalanie, aby zwiększyć bezpieczeństwo aplikacji i jej konfiguracji. Aby uzyskać więcej informacji dotyczących tych pojęć zobacz następujące tematy.  
  
 [Szyfrowanie informacji o konfiguracji](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Ustawienia konfiguracji blokowania](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 W tej sekcji opisano wszystkie możliwe wartości poszczególnych elementów konfiguracji i jak współdziała z innymi elementami konfiguracji usługi WCF. Następujące mapy przedstawiono schemat konfiguracji usługi WCF.  
  
 ![Schemat konfiguracji programu WCF](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")  
  
> [!CAUTION]
>  Należy chronić WCF sekcji konfiguracyjnych w plikach konfiguracji aplikacji (app.config) z odpowiednią kontroli dostępu zawiera listę (ACL) aby uniemożliwić wszystkie potencjalne zagrożenia bezpieczeństwa.  Należy na przykład upewnij się, że odpowiednie osoby mogą uzyskać dostęp lub zmodyfikować ustawienia zabezpieczeń na powiązania aplikacji lub modelu usługi części pliku konfiguracji dla usługi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 Opisuje `ServiceModel` elementu.  
  
 [\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 Konfiguruje narzędzia SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 Element najwyższego poziomu do ustawiania opcji, gdy przy użyciu serializatorów, takich jak <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Konfigurowanie systemu Windows Communication Foundation aplikacji](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 Opisuje sposób konfigurowania usług WCF i klientów.
