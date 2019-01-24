---
title: Konfigurowanie usług i klientów za pomocą powiązań
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 8aed2b2efa0408371a8da47fef64340fd30fffcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577103"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Konfigurowanie usług i klientów za pomocą powiązań
Powiązania są obiekty, które określają szczegółów komunikacji wymagane do połączenia z punktem końcowym. W szczególności powiązania zawierają informacje o konfiguracji, który jest używany do tworzenia środowiska uruchomieniowego klienta lub usługę, definiując szczegółowe informacje na temat transportu, formatów łańcuchowych (kodowanie komunikatu) i protokoły używane dla odpowiednich klienta lub punktu końcowego kanału. Aby utworzyć funkcjonalności usługi Windows Communication Foundation (WCF), każdy punkt końcowy usługi wymaga powiązania. W tym temacie opisano powiązania są, jak są one definiowane i jak określonego powiązania jest określony dla punktu końcowego.  
  
## <a name="what-a-binding-defines"></a>Definiuje powiązanie  
 Informacje przedstawione w powiązaniu może być bardzo podstawowe lub bardzo złożone. Podstawowe powiązanie określa tylko protokół transportu (np. HTTP) używany do łączenia z punktu końcowego. Ogólnie rzecz biorąc powiązanie zawiera informacje o tym, jak połączyć się z punktem końcowym należy do jednej z kategorii w poniższej tabeli.  
  
 Protokoły  
 Określa mechanizmu zabezpieczeń jest używane, niezawodne możliwości obsługi komunikatów lub ustawienia przepływu kontekstu transakcji.  
  
 Transport  
 Określa podstawowy protokół transportu do użycia (na przykład, TCP lub HTTP).  
  
 Kodowanie  
 Określa kodowanie komunikatu, na przykład, tekstu/XML, binarne lub komunikat transmisji optymalizacji mechanizm (MTOM), określający, jak wiadomości są reprezentowane jako strumienie bajtów na potrzeby przesyłu.  
  
## <a name="system-provided-bindings"></a>Powiązania dostarczane przez system  
 Usługi WCF zawiera zestaw powiązań dostarczanych przez system, które są przeznaczone do większości wymagań aplikacji i scenariuszy. Następujące klasy reprezentują kilka przykładów powiązania dostarczane przez system:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: Protokół HTTP powiązanie odpowiednie do łączenia się z usługami sieci Web, który jest zgodny z WS-I Basic Profile 1.1 specyfikacji (na przykład ASP.NET Web services [ASMX]-na podstawie usług).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Protokół HTTP, powiązanie odpowiednie do nawiązywania połączenia z punktami końcowymi, które są zgodne z sieci Web usług specyfikacje protokołów.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Używa binarne .NET, kodowanie i ramek technologii w połączeniu z Windows o nazwie transportu potoku połączyć się z innymi punktami końcowymi programu WCF na tym samym komputerze.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Używa binarne .NET, kodowanie i ramek technologii w połączeniu z MSMQ (MSMQ) w celu utworzenia komunikatu w kolejce połączenia z innymi punktami końcowymi WCF.  
  
 Aby uzyskać pełną listę powiązania dostarczane przez system, z opisami, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe  
 Jeśli kolekcja powiązania dostarczane przez system nie ma poprawnej kombinacji funkcje, których wymaga aplikacja usługi, możesz utworzyć <xref:System.ServiceModel.Channels.CustomBinding> powiązania. Aby uzyskać więcej informacji o elementach <xref:System.ServiceModel.Channels.CustomBinding> powiązań, zobacz [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) i [niestandardowego powiązania](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Za pomocą powiązań  
 Za pomocą powiązań pociąga za sobą dwa podstawowe kroki:  
  
1.  Wybierz lub zdefiniuj powiązania. Jest to najłatwiejsza metoda wybierz jedno z powiązań dostarczanych przez system i użyj jej ustawień domyślnych. Możesz również wybrać powiązania dostarczane przez system i resetowania wartości właściwości ze swoimi potrzebami. Możesz też Tworzenie niestandardowego powiązania i ustawić dla każdej właściwości zgodnie z potrzebami.  
  
2.  Tworzenie punktu końcowego, który używa tego powiązania.  
  
## <a name="code-and-configuration"></a>Kod i Konfiguracja  
 Można zdefiniować lub skonfigurować powiązania za pomocą kodu lub konfiguracji. Te dwie metody są niezależne od typ powiązania używanego, na przykład, czy używane są dostarczane przez system lub <xref:System.ServiceModel.Channels.CustomBinding> powiązania. Ogólnie rzecz biorąc przy użyciu kodu zapewnia pełną kontrolę nad definicji powiązania podczas kompilowania. Z drugiej strony, przy użyciu konfiguracji umożliwia administratora systemu lub użytkownika usługi WCF lub klienta w celu zmiany parametrów powiązania. Ta elastyczność często jest pożądane, ponieważ nie istnieje żaden sposób przewidzieć wymagania dotyczące określonego komputera i sieci warunków, w których ma zostać wdrożona aplikacja WCF. Oddzielenie informacji wiążące (i adresowania) od kodu, umożliwia administratorom zmiany szczegółów powiązania bez konieczności ponownego kompilowania lub ponownego wdrażania aplikacji. Należy pamiętać, że jeśli wiązanie jest definiowana w kodzie, zastępuje on żadnych definicji oparta na konfiguracji w pliku konfiguracji. Przykłady tych metod zobacz następujące tematy:  
  
-   [Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) stanowi przykład tworzenia powiązania w kodzie.  
  
-   [Instrukcje: Konfigurowanie klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md) stanowi przykład tworzenia klienta za pomocą konfiguracji.  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Instrukcje: Określanie wiązań usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Instrukcje: Określanie wiązań usługi w kodzie](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
- [Instrukcje: Określanie wiązania klienta w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
- [Instrukcje: Określanie wiązania klienta w kodzie](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
