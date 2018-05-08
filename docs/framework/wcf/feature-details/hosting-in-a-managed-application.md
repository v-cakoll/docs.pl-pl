---
title: Hosting w aplikacji zarządzanej
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: f374c199fb1982ab8854e41c0c8308f46451d9d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-in-a-managed-application"></a>Hosting w aplikacji zarządzanej
Usługi Windows Communication Foundation (WCF) może być hostowana w żadnym [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji. Usługi hostingowe własnym jest najbardziej elastycznego opcja hostingu, ponieważ wymaga co najmniej infrastruktury do wdrożenia. Jednak jest również opcji hostingu najmniej niezawodne, ponieważ zarządzane aplikacje nie udostępniają zaawansowane hosting i funkcji do zarządzania inne opcje hostingu w programie WCF, takie jak usługi Internet Information Services (IIS) i systemu Windows.  
  
 Aby utworzyć samodzielnie hostowana usługa, Utwórz i otwórz wystąpienie <xref:System.ServiceModel.ServiceHost>, która uruchamia usługę nasłuchiwania dla wiadomości. Aby uzyskać więcej informacji, zobacz [porady: hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Pełny przykład na temat Definiowanie kontraktu, zaimplementować kontrakt i obsługiwać usługę wewnątrz zarządzanej aplikacji zobacz [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md) i [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md).  
  
 W poniższych sekcjach opisano typowe scenariusze, które używają tej opcji hostingu.  
  
## <a name="console-applications"></a>Aplikacje konsoli  
 Typowe scenariusze, które umożliwia hostingu samodzielnego są usług WCF uruchomionych w aplikacji konsoli. Hosting usługi WCF w aplikacji konsoli jest zazwyczaj przydatne w fazie projektowania usługi. Z tego powodu łatwy do debugowania, łatwo uzyskać informacje o śledzeniu na, aby dowiedzieć się, co dzieje się wewnątrz aplikacji i łatwo przenosić, kopiując je do nowej lokalizacji.  
  
## <a name="rich-client-applications"></a>Aplikacje wzbogaconego klienta  
 Inne typowe scenariusze, które umożliwia hostingu samodzielnego są zaawansowanych aplikacji klienckich, takich jak zasoby oparte na Windows Presentation Foundation (WPF) lub program Windows Forms (WinForms). Ta opcja hostingu ułatwia także dla zaawansowanych aplikacji klienckich, takich jak [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] i WinForms aplikacji, aby komunikować się na zewnątrz. Na przykład klient współpracy peer-to-peer, który używa [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] interfejs użytkownika, a także obsługuje usługi WCF, która umożliwia innym klientom nawiązania połączenia i udostępnianie informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)  
 [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md)
