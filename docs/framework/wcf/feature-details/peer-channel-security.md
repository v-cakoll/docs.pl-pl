---
title: "Zabezpieczenia kanału równorzędnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: afe4252a56802ff2796f947afa31a5871f29223e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="peer-channel-security"></a>Zabezpieczenia kanału równorzędnego
Kanał elementu równorzędnego umożliwia różnych typów aplikacji rozproszonej, które są zależne od wielopartyjnej wiadomości. Oto kilka przykładów skali Internet dystrybucji zawartości, której zaufane źródło dystrybucji zawartości (na przykład nośnik lub aktualizacji oprogramowania), grupą znajomych wymiany muzyka i zdjęcia lub zespołu współpracowników wspólnie edytowanie dokumentu. Każdy z tych scenariuszy wymaga modelu zabezpieczeń unikatowa. Model zabezpieczeń kanał elementu równorzędnego zaprojektowano w celu rozwiązania tych scenariuszy i oferuje model zabezpieczeń dźwięku dla indywidualnych potrzeb różne modele tożsamości, uwierzytelniania i autoryzacji.  
  
## <a name="security-scenarios"></a>Scenariusze zabezpieczeń  
 Scenariusz dystrybucja zawartości wymaga, że każdy odbiorca zawartości zidentyfikować źródła zawartości. Z powodu Rozproszony charakter tego scenariusza nie zawsze jest możliwe znanych i zaufanych pośredników tego procesu lub przechwycenia wiadomości. W celu wyeliminowania zagrożenia, które pośrednik niezaufanych może manipulować komunikaty, aplikacje można zabezpieczyć wiadomość na adres nadawcy tak, aby wszelkie prób manipulowania przy łatwo są wykrywane. W takim przypadku w zależności od poufność zawartość szyfrowania może być konieczne.  
  
 Współpraca scenariuszy, takich jak grupy współpracy nad dokumentami często wymagają, aby każdy element członkowski uczestniczących w sesji można indywidualnie zidentyfikowane i uwierzytelniony. Oznacza to, że mechanizm Definiowanie grup użytkowników i uwierzytelniania względem tych grup ma konieczne zabezpieczonych sesji. Ponadto aplikacje mogą wymagać śledzenie każdy komunikat uwierzytelniania na poziomie wiadomości. W tych typów aplikacji wydajności mogą zostać zachowane systemu silniejszych zabezpieczeń.  
  
 Sesja komunikacji między grupy zwykłych użytkowników może wymagać modele nieformalne zabezpieczeń, takich jak wiedzę na temat wspólnego klucza tajnego w grupie. W przypadku tych typów aplikacji o modelu zabezpieczeń, który jest wygodne i skonfigurować ma większe znaczenie niż posiadające najwyższy formy uwierzytelniania lub zapewnienie środków niemożność. W tych sytuacjach mechanizm uwierzytelniania opartego na hasłach pomaga zabezpieczyć warstwa komunikacji, umożliwiając uwierzytelniania wiadomości. Zabezpieczenia oparte na hasłach jest ustawieniem domyślnym dla kanału równorzędnego.  
  
## <a name="token-types"></a>Typy tokenów  
 Kanał elementu równorzędnego rozpoznaje jeden typ tokenu do identyfikacji silne certyfikatów X.509, które dostarczają oparty na typie uwierzytelniania i autoryzacji, które można wdrożyć modelu silnej tożsamości. Poufność i integralności łatwo znajdują się za pomocą certyfikatów. Jednak certyfikaty X.509 może być trudne do użycia i wdrażania.  
  
 Kanał elementu równorzędnego także zapewnia obsługę proste aplikacje przy użyciu hasła. Aplikacje można wybrać do skonfigurowania grup równorzędnych szybkie i proste, w oparciu o podane hasło. W takim przypadku właściciel grupy decyduje i komunikuje się hasło do elementów członkowskich. Każdy element członkowski musi Zaloguj się przy użyciu tego hasła, zanim one dołączyć do sesji. Hasła mogą być wykorzystywane tylko w celu wprowadzania z sesją; Nie można ich używany do uwierzytelniania wiadomości. Jest to spowodowane tokenu symetrycznego, który udział grupy elementów równorzędnych jest trudne i nieodpowiednie do użycia na potrzeby uwierzytelniania źródła.  
  
## <a name="security-model"></a>Model zabezpieczeń  
 Kanał elementu równorzędnego umożliwia zabezpieczanie poszczególnych łączy między komputerami równorzędnymi. Oznacza to, że komunikat nigdy nie przepływa łącze niezabezpieczona (z perspektywy aplikacji). Wewnętrznie każdego łącza (kanał transportu między dwoma komputerami) jest zabezpieczona przy użyciu zabezpieczeń TLS (Transport Layer). Oznacza to, że gdy nadawcy Redaguj i wysyła wiadomość jest wysyłana za pośrednictwem bezpiecznego transportu do każdego z jego natychmiastowego elementów równorzędnych, którzy dostępu do wiadomości, a to z kolei wysyła komunikat do natychmiastowego między sobą za pośrednictwem bezpiecznego połączenia. Zabezpieczeń działa tylko na transport poziomu i jest niezależna od modele zabezpieczeń wiadomości.  
  
 Kanał elementu równorzędnego umożliwia również Zabezpieczanie komunikatów niezależnie od użyć zabezpieczeń transportu. W tym modelu wiadomość jest zabezpieczona w źródle, przy użyciu tokenu zabezpieczającego źródła, chociaż obecnie tylko certyfikaty X.509 są obsługiwane. Zabezpieczoną wiadomość jest następnie transmisji w sieci równorzędnej. Każdy komputer odbierający można zweryfikować autentyczności źródła. Należy pamiętać, że wiadomość jest zabezpieczona, dzięki czemu pośredników manipulowanie nie można go.  
  
 Aby osiągnąć poufność, aplikacje można wdrożyć zabezpieczenia transportu z schematów członkostwa grup silne, aby uniemożliwić nieautoryzowany dostęp do wiadomości.  
  
 Kanał elementu równorzędnego nie wymaga modelu określonej tożsamości, tak długo, jak aplikacja wybierze jeden z obsługiwanych typów tokenu. Aplikacje całkowicie właścicielem cyklu życia tożsamości i decyzje dotyczące uwierzytelniania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji kanałów równorzędnych](../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Pojęcia kanałów równorzędnych](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
