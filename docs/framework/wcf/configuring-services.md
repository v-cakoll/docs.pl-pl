---
title: "Konfigurowanie usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 857ec77e54d6a55bde1a94fd9fd5758ef7a24309
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-services"></a>Konfigurowanie usług
Po zaprojektowane i zaimplementowane umowy serwisowej, możesz przystąpić do konfigurowania usługi. To pozwala definiować i dostosowywać, jak usługa jest widoczne dla klientów, łącznie z określeniem adres, gdzie można je znaleźć, transport i kodowanie wiadomości używanych do wysyłania i odbierania wiadomości oraz typ zabezpieczeń, które wymaga.  
  
 Konfiguracja tutaj obejmuje wszystkich metod imperatively w kodzie, lub za pomocą pliku konfiguracji, w którym można zdefiniować i dostosować różne aspekty usług, takich jak określanie jego adresy punktów końcowych, transportów używane i jego systemów zabezpieczeń. W praktyce, zapisywanie konfiguracji to główne programowania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)  
 Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] jest dostarczany z nowy model konfiguracji domyślne, które upraszcza [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] wymagania dotyczące konfiguracji. Jeśli nie podano żadnego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfiguracji dla określonej usługi, środowisko uruchomieniowe automatycznie konfiguruje usługi przy użyciu domyślnych punktów końcowych, powiązania i zachowania.  
  
 [Konfigurowanie usług za pomocą plików konfiguracji](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługa jest można skonfigurować przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji. Najczęściej, elementy XML są dodawane do pliku Web.config dla witryny Internet Information Services (IIS), który jest hostem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi. Elementy umożliwiają zmianę szczegóły, takie jak adresy punktów końcowych (rzeczywiste adresy używane do komunikacji z usługą) na komputerze przez komputer.  
  
 [Powiązania](../../../docs/framework/wcf/bindings.md)  
 Ponadto [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obejmuje kilka typowych konfiguracji dostarczane przez system w postaci powiązania, które umożliwiają szybkie wybranie najbardziej podstawowe funkcje klienta i usługi komunikowania, takich jak transportów, zabezpieczeń i kodowanie komunikatu używane.  
  
 [Punkty końcowe](../../../docs/framework/wcf/endpoints.md)  
 Cała komunikacja z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi odbywa się przez *punkty końcowe* usługi. Punkty końcowe zawiera kontrakt, informacje o konfiguracji, który jest określony w powiązaniach i adresy, wskazujące, gdzie można znaleźć usługi lub gdzie można uzyskać informacji o usłudze.  
  
 [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)  
 Przy użyciu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] i istniejące mechanizmy zabezpieczeń, można zaimplementować poufność, integralność, uwierzytelniania i autoryzacji do dowolnej usługi. Można również przeprowadzać inspekcję dla zabezpieczeń sukcesy i niepowodzenia.  
  
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
