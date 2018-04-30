---
title: Omówienie powiązań WCF (Windows Communication Foundation)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 58b3691c186dc6a33c94d9f8a1af96be488d67df
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="windows-communication-foundation-bindings-overview"></a>Omówienie powiązań WCF (Windows Communication Foundation)
Powiązania są obiekty, które są używane do określania szczegółów komunikacji, które są wymagane do nawiązania połączenia z punktów końcowych [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi. Każdy punkt końcowy w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi wymaga powiązania być poprawnie określona. W tym temacie przedstawiono typy komunikacji szczegóły definiujące powiązań, elementy powiązania, jakie powiązania są uwzględnione w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], jak można określić powiązanie dla punktu końcowego.  
  
## <a name="what-a-binding-defines"></a>Definiuje powiązanie  
 Informacje w powiązaniu może być bardzo podstawowe lub bardzo złożonych. Najbardziej podstawowa powiązanie określa tylko protokół transportu (np. HTTP), który musi być używany do łączenia się z punktem końcowym. Ogólnie rzecz biorąc powiązanie zawiera informacje o tym, jak nawiązać połączenia z punktem końcowym należy do jednej z następujących kategorii.  
  
 protokoły  
 Określa używany mechanizm zabezpieczeń: niezawodne możliwości komunikatów lub ustawienia przepływ kontekstu transakcji.  
  
 Kodowanie  
 Określa kodowanie komunikatu (na przykład tekst lub binarny).  
  
 Transportu  
 Określa podstawowy protokół transportu do użycia (np. TCP lub HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Elementy powiązania  
 Powiązanie zasadniczo składa się z uporządkowanej stosu powiązania elementów, z których każdy określa część komunikacji informacje wymagane do połączenia z punktem końcowym usługi. Znajdują się dwie warstwy najniższy w stosie wymagane. Na podstawie stosu jest element powiązania transportu i powyżej to jest element zawierający specyfikacje Kodowanie komunikatu. Elementy opcjonalne określające innych protokołów komunikacyjnych są warstwę ponad tych dwóch wymaganych elementów. Aby uzyskać więcej informacji na temat tych elementów powiązania i ich kolejności poprawne zobacz [powiązań niestandardowych](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Powiązania dostarczane przez system  
 Informacje w powiązaniu może być skomplikowane, a niektóre ustawienia mogą nie być zgodne z innymi osobami. Z tego powodu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zawiera zestaw powiązania dostarczane przez system. Te powiązania zostały zaprojektowane tak, aby pokrywał większość wymagań aplikacji. Następujące klasy reprezentują przykłady powiązania dostarczane przez system:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: Protokołu HTTP powiązanie odpowiednie dla łączących się z usługami sieci Web, który jest zgodny ze standardem WS-I Basic Profile specification (na przykład usług sieci Web ASP.NET opartego na usługach).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Interoperacyjne powiązanie odpowiednie do nawiązywania połączenia z punktami końcowymi, które odpowiadają WS-* protokołów.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Używa [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] połączyć się z innymi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] punktów końcowych na tym samym komputerze.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Używa [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] można utworzyć komunikatu w kolejce połączenia z innymi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] punktów końcowych.  
  
 Aby uzyskać pełną listę, z opisami wszystkich [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-pod warunkiem powiązania, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Przy użyciu własnego powiązań  
 Jeśli żaden z uwzględnione powiązania dostarczane przez system nie ma odpowiednie połączenie funkcji, które wymaga aplikacji usługi, można tworzyć własne powiązania. Istnieją dwa sposoby, w tym celu. Możesz utworzyć nowe powiązanie z istniejącym elementów powiązania za pomocą <xref:System.ServiceModel.Channels.CustomBinding> obiektu albo można utworzyć powiązania całkowicie zdefiniowane przez użytkownika przez pochodny <xref:System.ServiceModel.Channels.Binding> powiązania. Aby uzyskać więcej informacji na temat tworzenia własnych powiązanie, używając te dwie metody, zobacz [powiązań niestandardowych](../../../docs/framework/wcf/extending/custom-bindings.md) i [powiązania Creating User-Defined](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Przy użyciu powiązań  
 Przy użyciu powiązań pociąga za sobą dwa podstawowe kroki:  
  
1.  Wybierz lub zdefiniuj powiązania. Najprostszą jest można wybrać jeden z uwzględnionych w powiązania dostarczane przez system [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] i używać jej wraz z jego domyślnych ustawień. Możesz również wybrać powiązania dostarczane przez system i zresetować jej wartości właściwości ze swoimi potrzebami. Alternatywnie można utworzyć niestandardowego powiązania lub powiązania zdefiniowane przez użytkownika, mają wyższy stopień kontrolą i dostosowywaniem.  
  
2.  Tworzenie punktu końcowego, który używa powiązania zaznaczone lub zdefiniowany.  
  
## <a name="code-and-configuration"></a>Kod i Konfiguracja  
 Można zdefiniować powiązania na dwa sposoby: za pomocą kodu lub konfiguracji. Te dwie metody nie zależą od tego, czy za pomocą powiązania dostarczane przez system lub niestandardowego powiązania. Ogólnie rzecz biorąc przy użyciu kodu umożliwia pełną kontrolę nad definicji powiązania w czasie projektowania. Przy użyciu konfiguracji z drugiej strony, umożliwia administratorem systemu lub użytkownik [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi lub klienta, aby zmienić parametry powiązania bez konieczności ponownego kompilowania aplikacji usługi. Tego rodzaju elastyczności często jest pożądane, ponieważ nie można przewidzieć wymagania określonej maszyny, na którym [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji ma zostać wdrożona. Zachowanie wiązania (i adresowania) informacje o kodzie pozwala zmienić bez konieczności ponownej kompilacji lub ponownego wdrażania aplikacji. Należy pamiętać, że powiązań zdefiniowanych w kodzie są tworzone po powiązania określony w konfiguracji, dzięki czemu powiązań zdefiniowanych przez kod zastąpić powiązań zdefiniowanych w konfiguracji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
