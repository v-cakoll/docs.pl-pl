---
title: Hosting w aplikacji zarządzanej
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 0210f608be8ef7ff8b2af4b0cc36b308cd3ddbe8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617242"
---
# <a name="hosting-in-a-managed-application"></a>Hosting w aplikacji zarządzanej
Usługi Windows Communication Foundation (WCF) mogą być hostowane w dowolnym [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji. Usługi hostingowe własnym jest najbardziej elastyczna opcja hostingu, ponieważ wymaga co najmniej infrastruktury do wdrożenia. Jednak to również najmniej niezawodne opcji hostingu, ponieważ aplikacje zarządzane nie udostępniają zaawansowane hostingu i funkcji do zarządzania inne opcje hostingu w programie WCF, takimi jak usługi Internet Information Services (IIS) i Windows.  
  
 Można utworzyć samodzielnie hostowanej usługi, należy utworzyć i otworzyć wystąpienie <xref:System.ServiceModel.ServiceHost>, który uruchamia usługę nasłuchiwać komunikatów. Aby uzyskać więcej informacji, zobacz [jak: Hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Pełny przykład o tym, jak definiowanie kontraktu, zaimplementowaniu kontraktu i obsługi usługi wewnątrz aplikacji zarządzanej, zobacz [Samouczek wprowadzający](../../../../docs/framework/wcf/getting-started-tutorial.md) i [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Typowe scenariusze, które używają tej opcji hostingu można znaleźć w poniższych sekcjach.  
  
## <a name="console-applications"></a>Aplikacje konsoli  
 Typowe scenariusze, które hostingu samodzielnego są usług WCF uruchomionych aplikacji konsoli. Hostowanie usługi WCF w aplikacji konsoli jest zazwyczaj przydatne w fazie opracowywania usługi. To sprawia, że ich łatwe debugowanie, ułatwia uzyskanie informacji o śledzeniu, aby dowiedzieć się, co dzieje się w aplikacji i łatwe przenoszenie, kopiując je do nowej lokalizacji.  
  
## <a name="rich-client-applications"></a>Aplikacji wzbogaconego klienta  
 Innych typowych scenariuszy, które hostingu samodzielnego są zaawansowanych aplikacji klienckich, takich jak oparty na Windows Presentation Foundation (WPF) lub Windows Forms (WinForms). Ta opcja hostingu ułatwia także dla zaawansowanych aplikacji klienckich, takich jak [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] i aplikacji formularzy WinForms, do komunikowania się ze światem zewnętrznym. Na przykład klient współpracy peer-to-peer, który używa [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] interfejs użytkownika i hostuje również usługi WCF, która umożliwia innym klientom nawiązać z nim i udostępnianie informacji.  
  
## <a name="see-also"></a>Zobacz także
- [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)
- [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md)
