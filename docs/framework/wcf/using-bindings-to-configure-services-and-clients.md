---
title: Konfigurowanie usług i klientów za pomocą wiązań
description: Powiązania zawierają informacje o konfiguracji używane przez klientów i usługi WFC. Dowiedz się, jak definiować powiązania i jak określać powiązanie dla punktu końcowego usługi.
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 60db37d4381191314e9d5588dd61015a7078e84d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245937"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Konfigurowanie usług i klientów za pomocą wiązań
Powiązania są obiektami, które określają szczegóły komunikacji wymagane do nawiązania połączenia z punktem końcowym. Dokładniej mówiąc, powiązania zawierają informacje o konfiguracji, które są używane do tworzenia klienta lub środowiska uruchomieniowego przez definiowanie określonych elementów transportowych, formatów połączeń (kodowanie komunikatów) i protokołów, które mają być używane dla odpowiedniego punktu końcowego lub kanału klienta. Aby utworzyć działającą usługę Windows Communication Foundation (WCF), każdy punkt końcowy w usłudze wymaga powiązania. W tym temacie wyjaśniono, jakie powiązania są zdefiniowane oraz jak określono określone powiązanie dla punktu końcowego.  
  
## <a name="what-a-binding-defines"></a>Co definiuje powiązanie  
 Informacje w powiązaniu mogą być bardzo proste lub bardzo złożone. Najbardziej podstawowe powiązanie określa tylko protokół transportowy (na przykład HTTP), który musi zostać użyty do nawiązania połączenia z punktem końcowym. Ogólnie rzecz biorąc, informacje, które wiążą się z tym, jak nawiązać połączenie z punktem końcowym, znajdują się w jednej z kategorii w poniższej tabeli.  
  
 Protokoły  
 Określa używany mechanizm zabezpieczeń, niezawodne możliwości obsługi komunikatów lub ustawienia przepływu kontekstu transakcji.  
  
 Transport  
 Określa podstawowy protokół transportowy do użycia (na przykład TCP lub HTTP).  
  
 Encoding  
 Określa kodowanie wiadomości, na przykład tekst/XML, binarny lub mechanizm optymalizacji transmisji wiadomości (MTOM), który określa sposób reprezentowania komunikatów jako strumienie bajtów w sieci.  
  
## <a name="system-provided-bindings"></a>Wiązania dostarczane przez system  
 Program WCF zawiera zestaw powiązań dostarczonych przez system, które zostały zaprojektowane w celu pokrycia większości wymagań i scenariuszy dotyczących aplikacji. Poniższe klasy reprezentują kilka przykładów powiązań dostarczonych przez system:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: Powiązanie protokołu HTTP odpowiednie do łączenia się z usługami sieci Web, które są zgodne ze specyfikacją WS-I Basic Profile 1,1 (na przykład usługi ASP.NET Web Services [ASMX]).  
  
- <xref:System.ServiceModel.WSHttpBinding>: Powiązanie protokołu HTTP odpowiednie do łączenia się z punktami końcowymi, które są zgodne z protokołami specyfikacji usług sieci Web.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Używa kodowania binarnego platformy .NET i technologii ramek w połączeniu z transportem nazwanych potoków systemu Windows, aby nawiązać połączenie z innymi punktami końcowymi WCF na tym samym komputerze.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Używa kodowania binarnego .NET i technologii ramek w połączeniu z kolejką komunikatów (znanej także jako MSMQ) do tworzenia połączeń komunikatów umieszczonych w kolejce z innymi punktami końcowymi WCF.  
  
 Aby uzyskać pełną listę powiązań dostarczanych przez system z opisami, zobacz [powiązania dostarczone przez system](system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe  
 Jeśli kolekcja powiązań udostępniona przez system nie ma poprawnej kombinacji funkcji wymaganych przez aplikację usługi, można utworzyć <xref:System.ServiceModel.Channels.CustomBinding> powiązanie. Aby uzyskać więcej informacji o elementach <xref:System.ServiceModel.Channels.CustomBinding> powiązania, zobacz [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) i [powiązania niestandardowe](./extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Używanie powiązań  
 Używanie powiązań obejmuje dwa podstawowe kroki:  
  
1. Wybierz lub Zdefiniuj powiązanie. Najprostszą metodą jest wybranie jednego z powiązań dostarczonych przez system i użycie jego ustawień domyślnych. Możesz również wybrać powiązanie dostarczone przez system i zresetować jego wartości właściwości zgodnie z wymaganiami. Alternatywnie można utworzyć niestandardowe powiązanie i ustawić każdą właściwość zgodnie z potrzebami.  
  
2. Utwórz punkt końcowy, który używa tego powiązania.  
  
## <a name="code-and-configuration"></a>Kod i konfiguracja  
 Można definiować lub konfigurować powiązania za poorednictwem kodu lub konfiguracji. Te dwa podejścia są niezależne od typu użytego powiązania, na przykład niezależnie od tego, czy używasz systemu, czy <xref:System.ServiceModel.Channels.CustomBinding> powiązania. Ogólnie rzecz biorąc, przy użyciu kodu zapewnia pełną kontrolę nad definicją powiązania podczas kompilowania. Przy użyciu konfiguracji, z drugiej strony, umożliwia administratorowi systemu lub użytkownikowi usługi lub klientowi WCF zmianę parametrów powiązań. Taka elastyczność jest często pożądana, ponieważ nie ma możliwości przewidywania konkretnych wymagań dotyczących maszyn i warunków sieci, w których ma zostać wdrożona aplikacja platformy WCF. Oddzielenie informacji o powiązaniach (i adresowania) od kodu pozwala administratorom zmieniać szczegóły powiązań bez konieczności ponownego kompilowania lub wdrażania aplikacji. Należy pamiętać, że jeśli powiązanie jest zdefiniowane w kodzie, zastępuje wszelkie definicje oparte na konfiguracji w pliku konfiguracji. Przykłady tych metod można znaleźć w następujących tematach:  
  
- [Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji](how-to-host-a-wcf-service-in-a-managed-application.md) zapewnia przykład tworzenia powiązań w kodzie.  
  
- [Samouczek: tworzenie klienta Windows Communication Foundation to](how-to-create-a-wcf-client.md) przykład tworzenia klienta za pomocą konfiguracji.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd tworzenia punktów końcowych](endpoint-creation-overview.md)
- [Instrukcje: określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md)
- [Instrukcje: określanie wiązań usługi w kodzie](how-to-specify-a-service-binding-in-code.md)
- [Instrukcje: określanie powiązań klienta w konfiguracji](how-to-specify-a-client-binding-in-configuration.md)
- [Instrukcje: określanie wiązania klienta w kodzie](how-to-specify-a-client-binding-in-code.md)
