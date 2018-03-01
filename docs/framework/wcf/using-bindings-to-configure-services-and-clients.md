---
title: "Konfigurowanie usług i klientów za pomocą powiązań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e63bb0b44e19ec9186096a819801ea05195b5523
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Konfigurowanie usług i klientów za pomocą powiązań
Powiązania są obiekty, które Określ szczegóły komunikacji wymagane do połączenia z punktem końcowym. W szczególności powiązania zawierają informacje o konfiguracji, który jest używany do tworzenia środowiska uruchomieniowego klienta lub usługę, definiując specyfice transportów, formatów łańcuchowych (kodowania wiadomości) i protokoły dla odpowiednich kanału klienta lub punktu końcowego. Aby utworzyć działanie [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi, powiązanie wymaga każdego punktu końcowego w usłudze. W tym temacie opisano powiązania są, jak są definiowane i jak określono konkretnego powiązanie dla punktu końcowego.  
  
## <a name="what-a-binding-defines"></a>Definiuje powiązanie  
 Informacje w powiązaniu mogą być bardzo podstawowe lub bardzo złożone. Najbardziej podstawowa powiązanie określa tylko protokół transportu (np. HTTP), który musi być używany do łączenia się z punktem końcowym. Ogólnie rzecz biorąc powiązanie zawiera informacje o tym, jak nawiązać połączenia z punktem końcowym należy do jednej kategorii w poniższej tabeli.  
  
 protokoły  
 Określa mechanizm zabezpieczeń jest używany, niezawodne możliwości komunikatów lub ustawienia przepływ kontekstu transakcji.  
  
 Transportu  
 Określa podstawowy protokół transportu do użycia (np. TCP lub HTTP).  
  
 Kodowanie  
 Określa, kodowania wiadomości, na przykład, text/XML, binarne lub komunikat transmisji optymalizacji mechanizmu (MTOM), określający, jak komunikaty są reprezentowane jako strumienie bajtów umieszczonego w.  
  
## <a name="system-provided-bindings"></a>Powiązania dostarczane przez system  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]zawiera zestaw powiązania dostarczane przez system, które są zaprojektowane tak, aby pokrywał większość wymagań aplikacji i scenariuszy. Następujące klasy reprezentują przykłady powiązania dostarczane przez system:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: Protokołu HTTP powiązanie odpowiednie dla łączących się z usługami sieci Web, który jest zgodny ze standardem WS-I Basic Profile 1.1 specyfikacji (na przykład ASP.NET Web services [ASMX] — na podstawie usługi).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Protokołu HTTP powiązanie odpowiednie do nawiązywania połączenia z punktami końcowymi, zgodnych ze standardami sieci Web usług specyfikacje protokołów.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Używa binarne .NET, kodowanie i framing technologii w połączeniu z systemu Windows o nazwie transportu potoku połączyć się z innymi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] punktów końcowych na tym samym komputerze.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Używa plik binarny .NET, kodowanie i framing technologii w połączeniu z MSMQ (MSMQ) do utworzenia w kolejce wiadomości połączenia z innymi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] punktów końcowych.  
  
 Aby uzyskać pełną listę powiązania dostarczane przez system, z opisami, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe  
 Jeśli kolekcja powiązania dostarczane przez system nie ma poprawnej kombinacji funkcji, które wymaga aplikacji usługi, możesz utworzyć <xref:System.ServiceModel.Channels.CustomBinding> powiązania. [!INCLUDE[crabout](../../../includes/crabout-md.md)]elementy <xref:System.ServiceModel.Channels.CustomBinding> powiązanie, zobacz [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) i [powiązań niestandardowych](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Przy użyciu powiązań  
 Przy użyciu powiązań pociąga za sobą dwa podstawowe kroki:  
  
1.  Wybierz lub zdefiniuj powiązania. Najprostszą jest wybierz jedną z powiązania dostarczane przez system i użyj ustawień domyślnych. Możesz również wybrać powiązania dostarczane przez system i zresetować jej wartości właściwości ze swoimi potrzebami. Alternatywnie możesz utworzyć niestandardowego powiązania i ustawić dla każdej właściwości zgodnie z potrzebami.  
  
2.  Tworzenie punktu końcowego, który używa tego powiązania.  
  
## <a name="code-and-configuration"></a>Kod i Konfiguracja  
 Można zdefiniować lub skonfiguruj powiązania za pomocą kodu lub konfiguracji. Te dwie metody są niezależne od typ powiązania używanego, na przykład, czy używane są dostarczane przez system, czy na <xref:System.ServiceModel.Channels.CustomBinding> powiązania. Ogólnie rzecz biorąc przy użyciu kodu umożliwia pełną kontrolę nad definicji powiązania podczas kompilowania. Przy użyciu konfiguracji z drugiej strony, umożliwia administratorem systemu lub użytkownik [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi lub klienta, aby zmienić parametry powiązania. Tego rodzaju elastyczności często jest pożądane, ponieważ nie można przewidzieć wymagania dotyczące określonego komputera i sieci warunków, w której [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji ma zostać wdrożona. Oddzielanie informacji powiązania (i adresowania) z kodu umożliwia administratorom zmienić szczegóły powiązanie bez konieczności ponowne skompilowanie lub ponownego wdrażania aplikacji. Należy pamiętać, że jeśli powiązanie jest zdefiniowany w kodzie, zastępuje on definicje oparta na konfiguracji w pliku konfiguracji. Przykłady z tych metod zobacz następujące tematy:  
  
-   [Porady: hostowanie usługi WCF w zarządzanej aplikacji](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) stanowi przykład tworzenia powiązania w kodzie.  
  
-   [Porady: Konfigurowanie klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md) stanowi przykład tworzenia klienta przy użyciu konfiguracji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Instrukcje: określanie powiązania usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Instrukcje: określanie wiązań usługi w kodzie](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)  
 [Instrukcje: określanie powiązań klienta w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)  
 [Instrukcje: określanie wiązania klienta w kodzie](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
