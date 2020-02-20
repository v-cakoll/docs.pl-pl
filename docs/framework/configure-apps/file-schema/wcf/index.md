---
title: Schemat konfiguracji programu WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 866b0639f4391e1898bbe36e458df87e3c24bfff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448662"
---
# <a name="wcf-configuration-schema"></a>Schemat konfiguracji programu WCF
Elementy konfiguracji programu Windows Communication Foundation (WCF) umożliwiają skonfigurowanie usług i aplikacji klienckich platformy WCF. Aby tworzyć i modyfikować pliki konfiguracji dla klientów i usług, można użyć [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) . Ponieważ pliki konfiguracji są sformatowane jako XML, należy zapoznać się z kodem XML, aby ręcznie edytować je za pomocą edytora tekstu. W przeciwnym razie może wystąpić problemy, takie jak unfound tagu elementu XML lub atrybut. Wynika to z tagów elementu XML i atrybutów jest rozróżniana wielkość liter.  
  
 System konfiguracji WCF jest oparty na przestrzeni nazw <xref:System.Configuration>. W związku z tym możesz użyć wszystkich funkcji standardowych dostępnych w przestrzeni nazw <xref:System.Configuration>, takich jak blokowanie konfiguracji, szyfrowanie i scalanie, aby zwiększyć bezpieczeństwo aplikacji i jej konfiguracji. Aby uzyskać więcej informacji na temat tych pojęć, zobacz następujące tematy.  
  
 [Szyfrowanie informacji o konfiguracji](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))  
  
 [Blokowanie ustawień konfiguracji](https://docs.microsoft.com/previous-versions/aspnet/55th21y4(v=vs.100))  
  
 W tej sekcji opisano wszystkie możliwe wartości poszczególnych elementów konfiguracji oraz sposób współdziałania z innymi elementami konfiguracji WCF. Poniższa mapa ilustruje Schemat konfiguracji programu WCF:  
  
 ![Diagram przedstawiający Schemat konfiguracji programu WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> Należy chronić sekcje konfiguracyjne programu WCF w plikach konfiguracji aplikacji (App. config) za pomocą odpowiednich list Access Control (ACL), aby zapobiec potencjalnym zagrożeniom bezpieczeństwa.  Należy na przykład upewnić się, że tylko odpowiednie osoby mają dostęp do ustawień zabezpieczeń powiązań aplikacji lub je modyfikować, a także w sekcji model usługi w pliku konfiguracji usługi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [\<system. serviceModel >](system-servicemodel.md)  
 Opisuje `ServiceModel` elementu.  
  
 [\<system. serviceModel. Activation >](system-servicemodel-activation.md)  
 Konfiguruje narzędzie SMSvcHost. exe.  
  
 [\<system. Runtime. Serialization >](system-runtime-serialization.md)  
 Element najwyższego poziomu służący do ustawiania opcji przy użyciu serializatorów, takich jak <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Konfigurowanie aplikacji Windows Communication Foundation](../../../wcf/configuring-services.md)  
 Opisuje sposób konfigurowania usług i klientów programu WCF.
