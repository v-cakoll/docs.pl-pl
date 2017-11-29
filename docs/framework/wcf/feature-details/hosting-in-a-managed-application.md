---
title: "Hosting w aplikacji zarządzanej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 30d531d436937bf5183ac0c28d59425ea71762e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-in-a-managed-application"></a>Hosting w aplikacji zarządzanej
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]usługi mogą być hostowane w dowolnym [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji. Usługi hostingowe własnym jest najbardziej elastycznego opcja hostingu, ponieważ wymaga co najmniej infrastruktury do wdrożenia. Jednak jest również opcji hostingu najmniej niezawodne, ponieważ zarządzane aplikacje nie udostępniają zaawansowane funkcje obsługi i zarządzania inne opcje hostingu w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], takie jak usługi Internet Information Services (IIS) i usług systemu Windows.  
  
 Aby utworzyć samodzielnie hostowana usługa, Utwórz i otwórz wystąpienie <xref:System.ServiceModel.ServiceHost>, która uruchamia usługę nasłuchiwania dla wiadomości. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Pełny przykład na temat Definiowanie kontraktu, zaimplementować kontrakt i obsługiwać usługę wewnątrz zarządzanej aplikacji zobacz [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md) i [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md).  
  
 W poniższych sekcjach opisano typowe scenariusze, które używają tej opcji hostingu.  
  
## <a name="console-applications"></a>Aplikacje konsoli  
 Typowe scenariusze, które są własnym hostingu umożliwia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług uruchomionych w konsoli aplikacji. Hosting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa wewnątrz aplikacji konsoli jest zazwyczaj przydatne w fazie projektowania usługi. Z tego powodu łatwy do debugowania, łatwo uzyskać informacje o śledzeniu na, aby dowiedzieć się, co dzieje się wewnątrz aplikacji i łatwo przenosić, kopiując je do nowej lokalizacji.  
  
## <a name="rich-client-applications"></a>Aplikacje wzbogaconego klienta  
 Inne typowe scenariusze czy zaawansowanych aplikacji klienckich, takich jak zasoby oparte na własnym hostingu umożliwia [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] lub program Windows Forms (WinForms). Ta opcja hostingu ułatwia także dla zaawansowanych aplikacji klienckich, takich jak [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] i WinForms aplikacji, aby komunikować się na zewnątrz. Na przykład klient współpracy peer-to-peer, który używa [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] dla jego interfejsu użytkownika, a także hostów [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która umożliwia innym klientom nawiązania połączenia i udostępnianie informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)  
 [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md)
