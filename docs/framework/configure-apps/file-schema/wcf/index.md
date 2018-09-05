---
title: Schemat konfiguracji programu WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 11123d30138e8e1e763af0a01245e774dfba14f6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508905"
---
# <a name="wcf-configuration-schema"></a>Schemat konfiguracji programu WCF
Windows Communication Foundation (WCF), elementy konfiguracji umożliwiają skonfigurowanie aplikacji usługi i klienta WCF. Możesz użyć [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pozwala tworzyć i modyfikować pliki konfiguracyjne dla klientów i usług. Ponieważ pliki konfiguracyjne są w formacie XML, należy zapoznać z danymi XML, jeśli chcesz ręcznie edytować za pomocą edytora tekstów. W przeciwnym razie może wystąpić problemy, takie jak unfound tagu elementu XML lub atrybut. Wynika to z tagów elementu XML i atrybutów jest rozróżniana wielkość liter.  
  
 System konfiguracji usługi WCF opiera się na <xref:System.Configuration> przestrzeni nazw. W związku z tym, można korzystać ze standardowych funkcji dostarczonych przez <xref:System.Configuration> przestrzeni nazw, takie jak konfiguracja, blokowanie, szyfrowania i scalania, aby zwiększyć bezpieczeństwo aplikacji i jego konfiguracji. Aby uzyskać więcej informacji dotyczących tych pojęć zobacz następujące tematy.  
  
 [Szyfrowanie informacji o konfiguracji](https://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Blokowanie ustawień konfiguracji](https://go.microsoft.com/fwlink/?LinkId=95338)  
  
 W tej sekcji opisano wszystkie możliwe wartości dla każdego elementu konfiguracji i sposób jej interakcji z innymi elementami konfiguracji usługi WCF. Poniższe mapy przedstawiono schemat konfiguracji programu WCF.  
  
 ![Schemat konfiguracji programu WCF](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")  
  
> [!CAUTION]
>  Należy chronić WCF sekcji konfiguracyjnych w plikach konfiguracji aplikacji (app.config) przy użyciu odpowiednich kontroli dostępu zawiera listę (ACL) aby zapobiec wszelkie potencjalne zagrożenia bezpieczeństwa.  Na przykład należy upewnić się, że odpowiednie osoby mogą uzyskać dostęp lub zmodyfikować ustawienia zabezpieczeń na powiązania aplikacji lub usługi w modelu części pliku konfiguracji dla usługi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 Opisuje `ServiceModel` elementu.  
  
 [\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 Konfiguruje narzędzia SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 Element najwyższego poziomu dla opcji ustawienia, korzystając z serializatory takich jak <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Konfigurowanie aplikacji programu Windows Communication Foundation](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 W tym artykule opisano sposób konfigurowania usługi WCF i klientów.
