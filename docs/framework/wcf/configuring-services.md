---
title: Konfigurowanie usług
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 7718edaefbad18afa11b3e3680fac39da585a610
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803283"
---
# <a name="configuring-services"></a>Konfigurowanie usług
Po zaprojektowane i zaimplementowane umowy serwisowej, możesz przystąpić do konfigurowania usługi. To pozwala definiować i dostosowywać, jak usługa jest widoczne dla klientów, łącznie z określeniem adres, gdzie można je znaleźć, transport i kodowanie wiadomości używanych do wysyłania i odbierania wiadomości oraz typ zabezpieczeń, które wymaga.  
  
 Konfiguracja tutaj obejmuje wszystkich metod imperatively w kodzie, lub za pomocą pliku konfiguracji, w którym można zdefiniować i dostosować różne aspekty usług, takich jak określanie jego adresy punktów końcowych, transportów używane i jego systemów zabezpieczeń. W praktyce, zapisywanie konfiguracji jest poważnym należą do programowania aplikacji WCF.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)  
 Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF jest dostarczany z nowy model konfiguracji domyślnej, które upraszcza wymagania dotyczące konfiguracji usługi WCF. Jeśli nie zostanie określona żadna konfiguracja usługi WCF dla określonej usługi, środowisko uruchomieniowe automatycznie konfiguruje usługi domyślne punkty końcowe, powiązania i zachowania.  
  
 [Konfigurowanie usług za pomocą plików konfiguracji](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Usługa Windows Communication Foundation (WCF) to można skonfigurować przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji. Najczęściej elementy XML są dodawane do pliku Web.config dla witryny Internet Information Services (IIS), który jest hostem usługi WCF. Elementy umożliwiają zmianę szczegóły, takie jak adresy punktów końcowych (rzeczywiste adresy używane do komunikacji z usługą) na komputerze przez komputer.  
  
 [Powiązania](../../../docs/framework/wcf/bindings.md)  
 Ponadto WCF zawiera kilka typowych konfiguracji dostarczane przez system w postaci powiązania, które umożliwiają szybkie wybierz najbardziej podstawowa funkcje sposobu komunikacji między klientem a usługą, na przykład transportów, zabezpieczeń i używane kodowanie komunikatu.  
  
 [Punkty końcowe](../../../docs/framework/wcf/endpoints.md)  
 Cała komunikacja z usługą WCF odbywa się przez *punkty końcowe* usługi. Punkty końcowe zawiera kontrakt, informacje o konfiguracji, który jest określony w powiązaniach i adresy, wskazujące, gdzie można znaleźć usługi lub gdzie można uzyskać informacji o usłudze.  
  
 [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)  
 Za pomocą usługi WCF i istniejące mechanizmy zabezpieczeń, można zaimplementować poufność, integralność, uwierzytelniania i autoryzacji do dowolnej usługi. Można również przeprowadzać inspekcję dla zabezpieczeń sukcesy i niepowodzenia.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy programowania przy użyciu programu WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Omówienie pojęć](../../../docs/framework/wcf/conceptual-overview.md)  
 [Szczegóły funkcji WCF](../../../docs/framework/wcf/feature-details/index.md)
