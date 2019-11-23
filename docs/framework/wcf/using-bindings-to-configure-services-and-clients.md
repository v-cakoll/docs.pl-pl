---
title: Konfigurowanie usług i klientów za pomocą wiązań
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: dd83072d3a1c76279fcc00ea5b0a4a41e278e10a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321509"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Konfigurowanie usług i klientów za pomocą wiązań
Powiązania są obiektami, które określają szczegóły komunikacji wymagane do nawiązania połączenia z punktem końcowym. Dokładniej mówiąc, powiązania zawierają informacje o konfiguracji, które są używane do tworzenia klienta lub środowiska uruchomieniowego przez definiowanie określonych elementów transportowych, formatów połączeń (kodowanie komunikatów) i protokołów, które mają być używane dla odpowiedniego punktu końcowego lub kanału klienta. Aby utworzyć działającą usługę Windows Communication Foundation (WCF), każdy punkt końcowy w usłudze wymaga powiązania. W tym temacie wyjaśniono, jakie powiązania są zdefiniowane oraz jak określono określone powiązanie dla punktu końcowego.  
  
## <a name="what-a-binding-defines"></a>Co definiuje powiązanie  
 Informacje w powiązaniu mogą być bardzo proste lub bardzo złożone. Najbardziej podstawowe powiązanie określa tylko protokół transportowy (na przykład HTTP), który musi zostać użyty do nawiązania połączenia z punktem końcowym. Ogólnie rzecz biorąc, informacje, które wiążą się z tym, jak nawiązać połączenie z punktem końcowym, znajdują się w jednej z kategorii w poniższej tabeli.  
  
 Protokoły  
 Określa używany mechanizm zabezpieczeń, niezawodne możliwości obsługi komunikatów lub ustawienia przepływu kontekstu transakcji.  
  
 Transportu  
 Określa podstawowy protokół transportowy do użycia (na przykład TCP lub HTTP).  
  
 Kodowanie  
 Określa kodowanie wiadomości, na przykład tekst/XML, binarny lub mechanizm optymalizacji transmisji wiadomości (MTOM), który określa sposób reprezentowania komunikatów jako strumienie bajtów w sieci.  
  
## <a name="system-provided-bindings"></a>Wiązania dostarczane przez system  
 Program WCF zawiera zestaw powiązań dostarczonych przez system, które zostały zaprojektowane w celu pokrycia większości wymagań i scenariuszy dotyczących aplikacji. Poniższe klasy reprezentują kilka przykładów powiązań dostarczonych przez system:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: powiązanie protokołu HTTP odpowiednie do łączenia się z usługami sieci Web, które są zgodne ze specyfikacją WS-I Basic Profile 1,1 (na przykład usługi ASP.NET Web Services [ASMX]).  
  
- <xref:System.ServiceModel.WSHttpBinding>: powiązanie protokołu HTTP odpowiednie do łączenia się z punktami końcowymi, które są zgodne z protokołami specyfikacji usług sieci Web.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: używa kodowania binarnego platformy .NET i technologii obsługi ramek w połączeniu z transportem nazwanych potoków systemu Windows, aby nawiązać połączenie z innymi punktami końcowymi WCF na tym samym komputerze.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: używa kodowania binarnego .NET i technologii ramek w połączeniu z kolejką komunikatów (znanej także jako MSMQ) do tworzenia połączeń komunikatów umieszczonych w kolejce z innymi punktami końcowymi WCF.  
  
 Aby uzyskać pełną listę powiązań dostarczanych przez system z opisami, zobacz [powiązania dostarczone przez system](system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe  
 Jeśli kolekcja powiązań udostępniona przez system nie ma poprawnej kombinacji funkcji wymaganych przez aplikację usługi, można utworzyć powiązanie <xref:System.ServiceModel.Channels.CustomBinding>. Aby uzyskać więcej informacji o elementach powiązania <xref:System.ServiceModel.Channels.CustomBinding>, zobacz [\<custombinding >](../configure-apps/file-schema/wcf/custombinding.md) i [powiązań niestandardowych](./extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Używanie powiązań  
 Używanie powiązań obejmuje dwa podstawowe kroki:  
  
1. Wybierz lub Zdefiniuj powiązanie. Najprostszą metodą jest wybranie jednego z powiązań dostarczonych przez system i użycie jego ustawień domyślnych. Możesz również wybrać powiązanie dostarczone przez system i zresetować jego wartości właściwości zgodnie z wymaganiami. Alternatywnie można utworzyć niestandardowe powiązanie i ustawić każdą właściwość zgodnie z potrzebami.  
  
2. Utwórz punkt końcowy, który używa tego powiązania.  
  
## <a name="code-and-configuration"></a>Kod i konfiguracja  
 Można definiować lub konfigurować powiązania za poorednictwem kodu lub konfiguracji. Te dwa podejścia są niezależne od typu użytego powiązania, na przykład niezależnie od tego, czy jest używane powiązanie dostarczone przez system czy <xref:System.ServiceModel.Channels.CustomBinding>. Ogólnie rzecz biorąc, przy użyciu kodu zapewnia pełną kontrolę nad definicją powiązania podczas kompilowania. Przy użyciu konfiguracji, z drugiej strony, umożliwia administratorowi systemu lub użytkownikowi usługi lub klientowi WCF zmianę parametrów powiązań. Taka elastyczność jest często pożądana, ponieważ nie ma możliwości przewidywania konkretnych wymagań dotyczących maszyn i warunków sieci, w których ma zostać wdrożona aplikacja platformy WCF. Oddzielenie informacji o powiązaniach (i adresowania) od kodu pozwala administratorom zmieniać szczegóły powiązań bez konieczności ponownego kompilowania lub wdrażania aplikacji. Należy pamiętać, że jeśli powiązanie jest zdefiniowane w kodzie, zastępuje wszelkie definicje oparte na konfiguracji w pliku konfiguracji. Przykłady tych metod można znaleźć w następujących tematach:  
  
- [Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji](how-to-host-a-wcf-service-in-a-managed-application.md) zapewnia przykład tworzenia powiązań w kodzie.  
  
- [Samouczek: tworzenie klienta Windows Communication Foundation to](how-to-create-a-wcf-client.md) przykład tworzenia klienta za pomocą konfiguracji.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd tworzenia punktów końcowych](endpoint-creation-overview.md)
- [Instrukcje: określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md)
- [Instrukcje: określanie wiązań usługi w kodzie](how-to-specify-a-service-binding-in-code.md)
- [Instrukcje: określanie powiązań klienta w konfiguracji](how-to-specify-a-client-binding-in-configuration.md)
- [Instrukcje: określanie wiązania klienta w kodzie](how-to-specify-a-client-binding-in-code.md)
