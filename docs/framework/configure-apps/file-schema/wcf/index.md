---
title: Schemat konfiguracji programu WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 8d7b4cbad1876888e7a22a92bdb28a17b880e159
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925392"
---
# <a name="wcf-configuration-schema"></a>Schemat konfiguracji programu WCF
Elementy konfiguracji programu Windows Communication Foundation (WCF) umożliwiają skonfigurowanie usług i aplikacji klienckich platformy WCF. Aby tworzyć i modyfikować pliki konfiguracji dla klientów i usług, można użyć [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) . Ponieważ pliki konfiguracji są sformatowane jako XML, należy zapoznać się z kodem XML, aby ręcznie edytować je za pomocą edytora tekstu. W przeciwnym razie może wystąpić problemy, takie jak unfound tagu elementu XML lub atrybut. Wynika to z tagów elementu XML i atrybutów jest rozróżniana wielkość liter.  
  
 System konfiguracji WCF jest oparty na <xref:System.Configuration> przestrzeni nazw. W związku z tym możesz użyć wszystkich funkcji standardowych dostępnych <xref:System.Configuration> w przestrzeni nazw, takich jak blokowanie konfiguracji, szyfrowanie i scalanie, aby zwiększyć bezpieczeństwo aplikacji i jej konfiguracji. Aby uzyskać więcej informacji na temat tych pojęć, zobacz następujące tematy.  
  
 [Szyfrowanie informacji o konfiguracji](https://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Blokowanie ustawień konfiguracji](https://go.microsoft.com/fwlink/?LinkId=95338)  
  
 W tej sekcji opisano wszystkie możliwe wartości poszczególnych elementów konfiguracji oraz sposób współdziałania z innymi elementami konfiguracji WCF. Poniższa mapa ilustruje Schemat konfiguracji programu WCF:  
  
 ![Diagram przedstawiający Schemat konfiguracji programu WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
>  Należy chronić sekcje konfiguracyjne programu WCF w plikach konfiguracji aplikacji (App. config) za pomocą odpowiednich list Access Control (ACL), aby zapobiec potencjalnym zagrożeniom bezpieczeństwa.  Należy na przykład upewnić się, że tylko odpowiednie osoby mają dostęp do ustawień zabezpieczeń powiązań aplikacji lub je modyfikować, a także w sekcji model usługi w pliku konfiguracji usługi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [\<system.serviceModel>](system-servicemodel.md)  
 Opisuje `ServiceModel` elementu.  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 Konfiguruje narzędzie SMSvcHost. exe.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 Element najwyższego poziomu służący do ustawiania opcji przy użyciu serializatorów, <xref:System.Runtime.Serialization.DataContractSerializer>takich jak.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Konfigurowanie aplikacji Windows Communication Foundation](../../../wcf/configuring-services.md)  
 Opisuje sposób konfigurowania usług i klientów programu WCF.
