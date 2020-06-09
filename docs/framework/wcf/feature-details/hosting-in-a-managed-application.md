---
title: Hosting w aplikacji zarządzanej
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 759257edf89d1af5c453bb98f41361b54cf113ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597348"
---
# <a name="hosting-in-a-managed-application"></a>Hosting w aplikacji zarządzanej
Usługi Windows Communication Foundation (WCF) mogą być hostowane w dowolnej aplikacji .NET Framework. Samoobsługowe usługi to najbardziej elastyczna opcja hostingu, ponieważ wymaga najmniejszej ilości infrastruktury do wdrożenia. Jest to jednak również najmniej niezawodna opcja hostingu, ponieważ aplikacje zarządzane nie zapewniają zaawansowanych funkcji hostingu i zarządzania innych opcji hostingu w programie WCF, takich jak Internet Information Services (IIS) i usługi systemu Windows.  
  
 Aby utworzyć usługę samoobsługową, Utwórz i Otwórz wystąpienie <xref:System.ServiceModel.ServiceHost> , które uruchamia usługę nasłuchuje komunikatów. Aby uzyskać więcej informacji, zobacz [jak: Hostowanie usługi WCF w zarządzanej aplikacji](../how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Aby zapoznać się z kompletnym przykładem sposobu definiowania kontraktu, wdrożenia kontraktu i hostowania usługi w aplikacji zarządzanej, zobacz [samouczek wprowadzenie](../getting-started-tutorial.md) i [samodzielnego hosta](../samples/self-host.md).  
  
 W poniższych sekcjach opisano typowe scenariusze używające tej opcji hostingu.  
  
## <a name="console-applications"></a>Aplikacje konsolowe  
 Typowymi scenariuszami, które włączają samohosting, są usługi WCF działające w aplikacjach konsolowych. Hosting usługi WCF w aplikacji konsolowej jest zwykle przydatny w fazie tworzenia usługi. Dzięki temu można łatwo debugować, łatwo uzyskać informacje o śledzeniu z usługi, aby dowiedzieć się, co się dzieje w aplikacji, i łatwo poruszać się, kopiując je do nowych lokalizacji.  
  
## <a name="rich-client-applications"></a>Rozbudowane aplikacje klienckie  
 Innymi typowymi scenariuszami, które są włączane przez samohosting, są rozbudowane aplikacje klienckie, takie jak te oparte na Windows Presentation Foundation (WPF) lub Windows Forms (WinForms). Ta opcja hostingu ułatwia również rozbudowane aplikacje klienckie, takie jak aplikacje WPF i WinForms, do komunikowania się ze światem zewnętrznym. Na przykład klient współpracy równorzędnej, który korzysta z platformy WPF dla interfejsu użytkownika, a także obsługuje usługę WCF, która umożliwia innym klientom łączenie się z działem IT i udostępnianie informacji.  
  
## <a name="see-also"></a>Zobacz też

- [Usługi hostingowe](../hosting-services.md)
- [Wprowadzenie — samouczek](../getting-started-tutorial.md)
