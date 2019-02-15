---
title: Konfigurowanie usług WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 2435d5c4592de60e07b60f1bf749f2421c798535
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303616"
---
# <a name="configuring-wcf-services"></a>Konfigurowanie usług WCF

Po zaprojektowane i zaimplementowane umowy serwisowej można przystąpić do konfigurowania usługi. Jest to, gdzie zdefiniujesz i dostosujesz, jak usługa jest narażony na klientów, łącznie z określeniem adresu, gdzie można je znaleźć, transport i kodowanie komunikatu, używanych do wysyłania i odbierania komunikatów i typ zabezpieczeń wymagane przez nią.  
  
 Konfiguracja tutaj obejmuje wszystkie sposoby obowiązkowo w kodzie lub za pomocą pliku konfiguracji, można zdefiniować i dostosować różnych aspektów usługi, takich jak określanie jego adresy punktów końcowych, transportów używane i jej programów zabezpieczeń. W praktyce Zapisywanie konfiguracji jest poważnym należą do programowania aplikacji WCF.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)  
 Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF, który jest dostarczany z nowy model konfiguracji domyślnej, który upraszcza wymagania dotyczące konfiguracji usługi WCF. Jeśli nie podano żadnej konfiguracji programu WCF dla określonej usługi, środowisko uruchomieniowe automatycznie konfiguruje usługi przy użyciu domyślnych punktów końcowych, powiązania i zachowania.  
  
 [Konfigurowanie usług za pomocą plików konfiguracji](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Usługa Windows Communication Foundation (WCF) jest, można skonfigurować przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji. Najczęściej XML elementy są dodawane do pliku Web.config dla witryny usług Internet Information Services (IIS), który hostuje usługę WCF. Elementy umożliwiają zmianę szczegóły, takie jak adresy punktów końcowych (rzeczywista adresy, używane do komunikacji z usługą) na podstawie maszyny według komputera.  
  
 [Powiązania](../../../docs/framework/wcf/bindings.md)  
 Ponadto WCF zawiera kilka typowych konfiguracji dostarczane przez system w postaci powiązania, które umożliwiają szybko wybrać najbardziej podstawowe funkcje dla sposób komunikacji klientów i usług, takich jak transportu, zabezpieczeń i używać kodowania komunikatu.  
  
 [Punkty końcowe](../../../docs/framework/wcf/endpoints.md)  
 Cała komunikacja z usługą WCF odbywa się przez *punktów końcowych* usługi. Punkty końcowe zawierać umowy, informacje o konfiguracji, który jest określony w powiązaniach i adresy, które wskazują, gdzie można znaleźć usługi lub gdzie można uzyskać informacji na temat usługi.  
  
 [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)  
 Przy użyciu usługi WCF i istniejące mechanizmy zabezpieczeń, można zaimplementować poufność, integralność, uwierzytelniania i autoryzacji do każdej usługi. Można również przeprowadzać inspekcję zabezpieczeń sukcesów i niepowodzeń.  
  
 [Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Wymagania dotyczące wdrażania usługi, która współdziała z usług i klientów na dowolnej platformie lub systemu operacyjnego zostały opisane w WS-I Basic Profile 1.1 specyfikacji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Podstawowy cykl życia programowania](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [Projektowanie i implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [Usługi hostingowe](../../../docs/framework/wcf/hosting-services.md)  
  
 [Kompilowanie klientów](../../../docs/framework/wcf/building-clients.md)  
  
 [Wprowadzenie do rozszerzalności](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [Administracja i diagnostyka](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a>Zobacz także
- [Podstawy programowania przy użyciu programu WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Omówienie pojęć](../../../docs/framework/wcf/conceptual-overview.md)
- [Szczegóły funkcji WCF](../../../docs/framework/wcf/feature-details/index.md)
