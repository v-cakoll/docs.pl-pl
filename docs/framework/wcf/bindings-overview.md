---
title: Omówienie powiązań WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: c450de0eb3eead3a2d3b21c3635caa71d92ce07f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212807"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Omówienie powiązań WCF (Windows Communication Foundation)
Powiązania to obiekty, które są używane do określania szczegółów komunikacji, które są wymagane do połączenia z punktem końcowym usługi Windows Communication Foundation (WCF). Każdy punkt końcowy usługi WCF wymaga powiązania do być poprawnie określona. W tym temacie opisano rodzaje komunikacji szczegółowe informacje, które definiują powiązania, elementy powiązania, jakie powiązania znajdują się w programie WCF i jak można określić powiązanie dla punktu końcowego.  
  
## <a name="what-a-binding-defines"></a>Definiuje powiązanie  
 Informacje przedstawione w powiązaniu może być bardzo podstawowe lub bardzo złożone. Podstawowe powiązanie określa tylko protokół transportu (np. HTTP) używany do łączenia z punktu końcowego. Ogólnie rzecz biorąc powiązanie zawiera informacje o tym, jak połączyć się z punktem końcowym należy do jednej z następujących kategorii.  
  
 Protokoły  
 Określa mechanizm zabezpieczeń używane: niezawodne możliwości obsługi komunikatów lub ustawienia przepływu kontekstu transakcji.  
  
 Kodowanie  
 Określa kodowanie komunikatu (na przykład tekst lub dane binarne).  
  
 Transport  
 Określa podstawowy protokół transportu do użycia (na przykład, TCP lub HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Elementy powiązania  
 Powiązanie po prostu składa się z uporządkowanej stosu powiązania elementów, z których każdy określa część informacji komunikacji wymagane do połączenia z punktu końcowego usługi. Dwie najniższej warstwy ze stosu są wymagane. Podstawową stosu jest element powiązania transportu i tuż nad tym jest elementem, który zawiera specyfikacje Kodowanie komunikatu. Elementy opcjonalne powiązania, określających inne protokoły komunikacyjne są warstwowe powyżej tych dwóch wymaganych elementów. Aby uzyskać więcej informacji o tych elementów powiązania i poprawne porządkowanie zobacz [niestandardowego powiązania](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Wiązania dostarczane przez system  
 Informacje przedstawione w powiązaniu może być złożonym procesem, a niektóre ustawienia mogą nie być zgodne z innymi osobami. Z tego powodu WCF zawiera zestaw powiązań dostarczanych przez system. Te powiązania są przeznaczone do obejmuje większość wymagań aplikacji. Następujące klasy reprezentują kilka przykładów powiązania dostarczane przez system:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: Protokół HTTP powiązanie odpowiednie do łączenia się z usługami sieci Web, który jest zgodny z WS-I specyfikacja profilu podstawowego (na przykład, sieci Web platformy ASP.NET opartego na usługach usługi).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Interoperacyjne powiązanie odpowiednie do nawiązywania połączenia z punktami końcowymi, które odpowiadają WS-* protokołów.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Używa [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] połączyć się z innymi punktami końcowymi programu WCF na tym samym komputerze.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Używa [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] do tworzenia komunikatu w kolejce połączeń z innymi punktami końcowymi WCF.  

- <xref:System.ServiceModel.NetTcpBinding>: To powiązanie oferuje wyższą wydajność niż powiązania protokołu HTTP i stanowi idealne rozwiązanie w sieci lokalnej.
  
 Aby uzyskać pełną listę, z opisami wszystkich dostarczone do usług WCF powiązań, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Za pomocą własnych powiązań.  
 Jeśli żaden z powiązań dostarczanych przez system, dołączone zawiera odpowiedniej kombinacji funkcje, których wymaga aplikacja usługi, możesz utworzyć własne powiązania. Istnieją dwa sposoby, aby to zrobić. Możesz utworzyć nowe powiązanie z istniejące elementy powiązania przy użyciu <xref:System.ServiceModel.Channels.CustomBinding> obiektu, albo można utworzyć powiązania całkowicie zdefiniowane przez użytkownika, wynikające z <xref:System.ServiceModel.Channels.Binding> powiązania. Aby uzyskać więcej informacji na temat tworzenia własnego powiązania, za pomocą tych dwóch metod, zobacz [niestandardowego powiązania](../../../docs/framework/wcf/extending/custom-bindings.md) i [powiązania Creating User-Defined](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Za pomocą powiązań  
 Za pomocą powiązań pociąga za sobą dwa podstawowe kroki:  
  
1.  Wybierz lub zdefiniuj powiązania. Jest to najłatwiejsza metoda wybierz jedno z powiązań dostarczanych przez system, dołączone do programu WCF i użyć go przy użyciu ustawień domyślnych. Możesz również wybrać powiązania dostarczane przez system i resetowania wartości właściwości ze swoimi potrzebami. Alternatywnie można utworzyć powiązania niestandardowego lub powiązania zdefiniowane przez użytkownika mają wyższy stopień kontroli i dostosowywania.  
  
2.  Tworzenie punktu końcowego, który używa powiązania wybrane lub zdefiniowany.  
  
## <a name="code-and-configuration"></a>Kod i Konfiguracja  
 Można zdefiniować powiązania na dwa sposoby: za pomocą kodu lub konfiguracji. Te dwie metody nie są zależne od tego, czy przy użyciu powiązania dostarczane przez system lub niestandardowego powiązania. Ogólnie rzecz biorąc przy użyciu kodu zapewnia pełną kontrolę nad definicji powiązania w czasie projektowania. Z drugiej strony, przy użyciu konfiguracji umożliwia administratora systemu lub użytkownika usługi WCF lub klienta w celu zmiany parametrów powiązania, bez konieczności ponownego kompilowania aplikacji usługi. Ta elastyczność często jest pożądane, ponieważ nie istnieje żaden sposób przewidzieć wymagania dotyczące określonego komputera, na których ma zostać wdrożona aplikacja WCF. Zachowanie powiązania (i adresowania) informacji z kodu pozwala im można zmienić bez konieczności ponownej kompilacji lub ponownego wdrażania aplikacji. Należy pamiętać, że powiązań zdefiniowanych w kodzie są tworzone po powiązania określone w konfiguracji, dzięki czemu powiązań zdefiniowanych przez kod zastąpić wszelkie powiązań zdefiniowanych przez konfigurację.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług i klientów za pomocą wiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
