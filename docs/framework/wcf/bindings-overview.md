---
title: Omówienie powiązań WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: 8c1e44609a0a20ffcec55af43e49ee62b0842378
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320755"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Omówienie powiązań WCF (Windows Communication Foundation)
Powiązania są obiektami, które są używane do określania szczegółów komunikacji, które są wymagane do nawiązania połączenia z punktem końcowym usługi Windows Communication Foundation (WCF). Każdy punkt końcowy w usłudze WCF wymaga, aby powiązanie było prawidłowo określone. W tym temacie opisano typy szczegółów komunikacji zdefiniowane przez powiązania, elementy powiązania, jakie powiązania są zawarte w programie WCF oraz jak można określić powiązanie dla punktu końcowego.  
  
## <a name="what-a-binding-defines"></a>Co definiuje powiązanie  
 Informacje w powiązaniu mogą być bardzo podstawowe lub bardzo złożone. Najbardziej podstawowe powiązanie określa tylko protokół transportowy (na przykład HTTP), który musi zostać użyty do nawiązania połączenia z punktem końcowym. Ogólnie rzecz biorąc, informacje, które wiążą się z tym, jak nawiązać połączenie z punktem końcowym, znajdują się w jednej z następujących kategorii:  
  
 **Protokołów**  
 Określa używany mechanizm zabezpieczeń: niezawodne możliwości obsługi komunikatów lub ustawienia przepływu kontekstu transakcji.  
  
 **Kody**  
 Określa kodowanie wiadomości (na przykład tekst lub binarny).  
  
 **Transportu**  
 Określa podstawowy protokół transportowy do użycia (na przykład TCP lub HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Elementy powiązania  
 Powiązanie zasadniczo składa się z uporządkowanego stosu elementów powiązania, z których każdy określa część informacji o komunikacji wymaganych do nawiązania połączenia z punktem końcowym usługi. Wymagane są dwie najniższe warstwy w stosie. Na początku stosu jest elementem powiązania transportu i tuż powyżej jest element, który zawiera specyfikacje kodowania komunikatów. Opcjonalne elementy powiązania, które określają inne protokoły komunikacyjne, są nakładane powyżej tych dwóch wymaganych elementów. Aby uzyskać więcej informacji na temat tych elementów powiązania i ich prawidłowej kolejności, zobacz [powiązania niestandardowe](./extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Wiązania dostarczane przez system  
 Informacje w powiązaniu mogą być złożone, a niektóre ustawienia mogą nie być zgodne z innymi. Z tego powodu WCF obejmuje zestaw powiązań dostarczonych przez system. Te powiązania zostały zaprojektowane w celu pokrycia większości wymagań aplikacji. Poniższe klasy reprezentują kilka przykładów powiązań dostarczonych przez system:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: powiązanie protokołu HTTP odpowiednie do łączenia się z usługami sieci Web, które są zgodne ze specyfikacją profilu usługi WS-I (na przykład ASP.NET usługi sieci Web).  
  
- <xref:System.ServiceModel.WSHttpBinding>: powiązanie interoperacyjne odpowiednie do łączenia się z punktami końcowymi, które są zgodne z protokołami WS-*.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: używa .NET Framework do nawiązywania połączenia z innymi punktami końcowymi WCF na tym samym komputerze.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: używa .NET Framework do tworzenia połączeń komunikatów umieszczonych w kolejce z innymi punktami końcowymi WCF.  

- <xref:System.ServiceModel.NetTcpBinding>: to powiązanie oferuje wyższą wydajność niż powiązania HTTP i jest idealnym rozwiązaniem do użycia w sieci lokalnej.
  
 Aby uzyskać pełną listę z opisami wszystkich powiązań dostarczonych przez funkcję WCF, zobacz [powiązania dostarczone przez system](system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Korzystanie z własnych powiązań  
 Jeśli żadne z dołączonych do systemu powiązań nie ma odpowiedniej kombinacji funkcji wymaganych przez aplikację usługi, możesz utworzyć własne powiązanie. Istnieją dwa sposoby, aby to zrobić. Można utworzyć nowe powiązanie z istniejących elementów powiązania przy użyciu obiektu <xref:System.ServiceModel.Channels.CustomBinding> lub można utworzyć całkowicie zdefiniowane przez użytkownika powiązanie, pobierając je z powiązania <xref:System.ServiceModel.Channels.Binding>. Aby uzyskać więcej informacji na temat tworzenia własnego powiązania przy użyciu tych dwóch metod, zobacz [niestandardowe powiązania](./extending/custom-bindings.md) i [Tworzenie powiązań zdefiniowanych przez użytkownika](./extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Używanie powiązań  
 Używanie powiązań obejmuje dwa podstawowe kroki:  
  
1. Wybierz lub Zdefiniuj powiązanie. Najprostszą metodą jest wybranie jednego z powiązań dostarczonych przez system z programem WCF i użycie go z ustawieniami domyślnymi. Możesz również wybrać powiązanie dostarczone przez system i zresetować jego wartości właściwości zgodnie z wymaganiami. Alternatywnie można utworzyć niestandardowe powiązanie lub powiązanie zdefiniowane przez użytkownika w celu uzyskania większej liczby stopni kontroli i dostosowywania.  
  
2. Utwórz punkt końcowy, który używa wybranego lub zdefiniowanego powiązania.  
  
## <a name="code-and-configuration"></a>Kod i konfiguracja  
 Powiązania można definiować na dwa sposoby: za poorednictwem kodu lub przez konfigurację. Te dwa podejścia nie zależą od tego, czy używasz powiązania dostarczonego przez system czy niestandardowego powiązania. Ogólnie rzecz biorąc, przy użyciu kodu zapewnia pełną kontrolę nad definicją powiązania w czasie projektowania. Przy użyciu konfiguracji, z drugiej strony, umożliwia administratorowi systemu lub użytkownikowi usługi lub klientowi WCF zmianę parametrów powiązania bez konieczności ponownego kompilowania aplikacji usługi. Taka elastyczność jest często pożądana, ponieważ nie ma możliwości przewidywania konkretnych wymagań dotyczących maszyn, na których ma zostać wdrożona aplikacja WCF. Przechowywanie informacji o powiązaniach (i adresowania) poza kodem pozwala im zmieniać bez konieczności ponownej kompilacji lub ponownego wdrożenia aplikacji. Należy zauważyć, że powiązania zdefiniowane w kodzie są tworzone po powiązaniach określonych w konfiguracji, umożliwiając powiązanie ze zdefiniowanymi kodem, aby zastąpić wszystkie powiązania zdefiniowane w konfiguracji.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
