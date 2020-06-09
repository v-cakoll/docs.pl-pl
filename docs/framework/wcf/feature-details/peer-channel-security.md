---
title: Zabezpieczenia kanału równorzędnego
ms.date: 03/30/2017
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
ms.openlocfilehash: f8015f41254d17f908f3665db65af3d82eaa2b6a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576086"
---
# <a name="peer-channel-security"></a>Zabezpieczenia kanału równorzędnego
Kanał równorzędny umożliwia korzystanie z różnych typów aplikacji rozproszonych, które są zależne od obsługi komunikatów wieloczęściowych. Niektóre przykłady obejmują dystrybucję zawartości w skali internetowej, w której zaufane źródło dystrybuuje zawartość (na przykład aktualizacje multimedialne lub programowe), grupę przyjaciół muzycznych i fotografie oraz zespół współpracowników wspólnie edytujący dokument. Każdy z tych scenariuszy wymaga unikatowego modelu zabezpieczeń. Model zabezpieczeń kanału równorzędnego został zaprojektowany tak, aby spełniał te scenariusze i oferuje dźwiękowy model zabezpieczeń dla odpowiednich potrzeb różnych tożsamości, uwierzytelniania i modeli autoryzacji.  
  
## <a name="security-scenarios"></a>Scenariusze zabezpieczeń  
 Scenariusz dystrybucji zawartości wymaga, aby każdy odbiorca zawartości zidentyfikował źródło zawartości. Ze względu na dystrybuowany charakter scenariusza nie zawsze jest możliwe poznanie i ufanie pośrednikom, które przetwarzają lub przechwytuje komunikaty. Aby skutecznie ograniczyć zagrożenie, że niezaufanego pośrednika może naruszać komunikaty, aplikacje mogą zabezpieczyć komunikat na nadawcy, aby umożliwić łatwe wykrywanie wszelkich prób naruszenia. W takim przypadku, w zależności od poufności zawartości, może być konieczne szyfrowanie.  
  
 Scenariusze współpracy, takie jak współpraca dokumentów grup, często wymagają, aby każdy członek uczestniczący w sesji był indywidualnie identyfikowany i uwierzytelniony. Oznacza to, że mechanizm definiowania grup użytkowników i uwierzytelniania w odniesieniu do tych grup jest niezbędny do posiadania zabezpieczonej sesji. Ponadto aplikacje mogą wymagać śledzenia poszczególnych komunikatów przez uwierzytelnianie na poziomie wiadomości. W przypadku tych typów aplikacji można wykluczać wydajność dla silniejszego schematu zabezpieczeń.  
  
 Sesja komunikacji między grupą użytkowników niezawodnych może wymagać nieformalnych modeli zabezpieczeń, takich jak znajomość wspólnego wpisu tajnego między grupą. W przypadku tych typów aplikacji model zabezpieczeń, który jest wygodny do ustanowienia i skonfigurowania, jest ważniejszy niż najwyższy sposób uwierzytelniania lub zapewniający środki. W tych scenariuszach mechanizm uwierzytelniania oparty na hasłach pomaga zabezpieczyć warstwę komunikacji i nadal zezwala na uwierzytelnianie komunikatów. Zabezpieczenia oparte na hasłach są ustawieniem domyślnym kanału równorzędnego.  
  
## <a name="token-types"></a>Typy tokenów  
 Kanał równorzędny rozpoznaje typ pojedynczego tokenu dla silnej identyfikacji, certyfikaty X. 509, które zapewniają silny model tożsamości na podstawie typu uwierzytelniania i autoryzacji, które mogą być implementowane. Poufność i integralność można łatwo zapewnić przy użyciu certyfikatów. Jednak certyfikaty X. 509 mogą być trudne do użycia i wdrożenia.  
  
 Kanał równorzędny zapewnia również obsługę prostych aplikacji przy użyciu haseł. Aplikacje mogą zdecydować się na skonfigurowanie szybkich i prostych grup równorzędnych na podstawie podanego hasła. W takim przypadku właściciel grupy decyduje o haśle i przekazuje je do członków. Każdy element członkowski musi zalogować się przy użyciu tego hasła, aby można było dołączyć do sesji. Haseł można używać tylko w celu zezwalania na wpis w sesji; nie można ich używać do uwierzytelniania wiadomości. Jest to spowodowane tym, że symetryczny token, który jest używany przez grupę elementów równorzędnych, jest trudny i nieodpowiedni do uwierzytelniania źródłowego.  
  
## <a name="security-model"></a>Model zabezpieczeń  
 Kanał równorzędny zapewnia możliwość zabezpieczenia poszczególnych linków między elementami równorzędnymi. Oznacza to, że komunikat nigdy nie jest przesyłany w niezabezpieczonym łączu (z perspektywy aplikacji). Wewnętrznie każde łącze (kanał transportowy między dwoma elementami równorzędnymi) jest zabezpieczone przy użyciu Transport Layer Security (TLS). Oznacza to, że gdy nadawca redaguje i wyśle wiadomość, jest wysyłana za pośrednictwem bezpiecznego transportu do każdego z jego bezpośrednich elementów równorzędnych, który uzyskuje dostęp do wiadomości i z kolei wysyła komunikat do bezpośrednich elementów równorzędnych przez bezpieczne połączenia. Zabezpieczenia te działają tylko na poziomie transportu i są niezależne od modeli zabezpieczeń komunikatów.  
  
 Kanał równorzędny zapewnia również sposób zabezpieczania komunikatów niezależnie od używanego zabezpieczenia transportu. W tym modelu komunikat jest zabezpieczony za pomocą tokenu zabezpieczającego źródła, chociaż obsługiwane są tylko certyfikaty X. 509. Zabezpieczony komunikat jest następnie przesyłany za pośrednictwem sieci równorzędnej. Każdy element równorzędny odbiorczej może zweryfikować autentyczność źródła. Należy pamiętać, że komunikat jest zabezpieczony, dzięki czemu pośrednicy nie może go zmodyfikować.  
  
 Aby zapewnić poufność, aplikacje mogą stosować zabezpieczenia transportu z silnymi schematami członkostwa w grupach, aby zapobiec nieautoryzowanemu dostępowi do wiadomości.  
  
 Kanał równorzędny nie wymaga określonego modelu tożsamości, dopóki aplikacja wybierze jeden z obsługiwanych typów tokenów. Aplikacje pełnią w cyklu życia te tożsamości i decyzje dotyczące uwierzytelniania.  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie aplikacji kanałów równorzędnych](securing-peer-channel-applications.md)
- [Pojęcia kanałów równorzędnych](peer-channel-concepts.md)
- [Tworzenie aplikacji kanału równorzędnego](building-a-peer-channel-application.md)
