---
title: Zabezpieczenia kanału równorzędnego
ms.date: 03/30/2017
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
ms.openlocfilehash: bc17c35bf088472cfbf36b2c6d7c868c8cc85f20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129457"
---
# <a name="peer-channel-security"></a>Zabezpieczenia kanału równorzędnego
Kanał elementu równorzędnego umożliwia różne typy aplikacji rozproszonych, które są zależne od wielostronnej komunikatów. Niektóre przykłady skali Internetu dystrybucji zawartości, gdzie zaufanego źródła dystrybuuje zawartość (np. aktualizacji oprogramowania lub nośników), grupa znajomych programu exchange, muzyka czy zdjęcia lub zespół współpracowników zespołowe przeprowadzanie edytowania dokumentu. Każdy z tych scenariuszy wymaga modelu zabezpieczeń unikatowy. Kanał elementu równorzędnego model zabezpieczeń jest przeznaczona dla tych scenariuszy i oferuje model zabezpieczeń dźwięk dla indywidualnych potrzeb różnych modeli tożsamości, uwierzytelniania i autoryzacji.  
  
## <a name="security-scenarios"></a>Scenariusze zabezpieczeń  
 Scenariusz dystrybucja zawartości wymaga, że każdy adresat zawartości zidentyfikować źródło zawartości. Ze względu na charakter rozproszonego scenariusza nie zawsze jest możliwe znasz i którym ufasz pośredników tego procesu lub intercept wiadomości. W celu wyeliminowania zagrożenia pośrednik niezaufanych może manipulować komunikaty, aplikacje można zabezpieczyć komunikat wyświetlany u nadawcy tak, aby wszelkie mieszczące manipulacją łatwo są wykrywane. W takich przypadkach w zależności od poufności zawartość szyfrowania może być konieczne.  
  
 Scenariuszy obejmujących współpracę, takich jak grupy współpracy nad dokumentami często wymagają, aby każdy członek udział w sesji można indywidualnie zidentyfikowane i uwierzytelniony. Oznacza, że mechanizm do definiowania grup użytkowników i uwierzytelniać tych grup konieczne zabezpieczonych sesji. Ponadto aplikacje mogą wymagać śledzenie każdego komunikatu przez uwierzytelnianie na poziomie komunikatu. W tego rodzaju aplikacje wydajności można było poświęcić silniejsze schematu zabezpieczeń.  
  
 Sesję komunikacji między grupą zwykłych użytkowników może wymagać modeli nieformalne zabezpieczeń, na przykład wiedzę na temat wspólnego klucza tajnego w grupie. Dla tych typów aplikacji model zabezpieczeń, który jest wygodne ustanowić i skonfigurować posiadające jest ważniejsza niż posiadanie najsilniejszych formy uwierzytelniania albo udostępniające środki Niemożność wyparcia. W tych scenariuszach mechanizm uwierzytelniania opartego na hasłach pomaga zabezpieczyć warstwa komunikacji, wciąż zezwalając uwierzytelniania wiadomości. Zabezpieczenia oparte na hasłach jest ustawieniem domyślnym dla elementu równorzędnego kanału.  
  
## <a name="token-types"></a>Typy tokenów  
 Kanał elementu równorzędnego rozpoznaje jeden typ tokenu do identyfikacji silne certyfikatów X.509, które dostarczają modelu silna tożsamość na podstawie typu uwierzytelniania i autoryzacji, które można zaimplementować. Poufności i integralności łatwo znajdują się za pomocą certyfikatów. Jednak może być trudne do używania i wdrożenie certyfikatów X.509.  
  
 Kanał elementu równorzędnego zapewnia również obsługę prostej aplikacji przy użyciu hasła. Aplikacje można skonfigurować grup równorzędnych szybkie i proste, w oparciu o podane hasło. W takim przypadku właścicielem grupy decyduje i komunikuje się hasło do elementów członkowskich. Każdy element członkowski musi Zaloguj się przy użyciu tego hasła, aby mogły one dołączyć do sesji. Hasła mogą być wykorzystywane tylko w celu wprowadzania do sesji; one nie można przeprowadzić uwierzytelniania wiadomości. Jest to spowodowane to token symetryczny udziale, do grupy obiektów równorzędnych, jest trudne i nieodpowiednich treści na potrzeby uwierzytelniania źródła.  
  
## <a name="security-model"></a>Model zabezpieczeń  
 Kanał elementu równorzędnego zapewnia możliwość dbania o poszczególnych łączy między elementami równorzędnymi. Oznacza to, że komunikat nigdy nie przepływy łączem niezabezpieczone (z perspektywy aplikacji). Wewnętrznie każdy link (kanał transportu między dwoma komputerami) jest zabezpieczona za pomocą zabezpieczeń TLS (Transport Layer). Oznacza to, że gdy nadawcę Redaguj i wysyła wiadomość wysyłana w bezpiecznym transportem do każdego z jego natychmiastowego elementami równorzędnymi, którzy dostępu do wiadomości, a z kolei wysyła komunikat do natychmiastowego między sobą za pośrednictwem bezpiecznego połączenia. Ta działa tylko na transport poziomu i zabezpieczeń jest niezależna od modeli zabezpieczeń wiadomości.  
  
 Kanał elementu równorzędnego umożliwia również Zabezpieczanie komunikatów, niezależnie od zabezpieczeń transportu używane. W tym modelu wiadomość jest zabezpieczona na poziomie źródła przy użyciu tokenu zabezpieczeń źródłowego, są obsługiwane obecnie tylko certyfikaty X.509. Zabezpieczoną wiadomość następnie jest przesyłane za pośrednictwem sieci elementów równorzędnych. Każdy komputer odbierający można zweryfikować autentyczności źródła. Należy pamiętać, że wiadomość jest zabezpieczona, aby pośredników nie będą mogli zmodyfikować go.  
  
 Uzyskanie poufności, aplikacji można stosować zabezpieczenia transportu ze schematami członkostwa silne grupy, aby uniemożliwić nieautoryzowany dostęp do wiadomości.  
  
 Kanał elementu równorzędnego nie wymaga modelu określonej tożsamości, tak długo, jak aplikacja wybiera jeden z obsługiwanych typów tokenu. Aplikacje całkowicie właścicielem cyklu życia tych tożsamości i decyzje dotyczące uwierzytelniania.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji kanałów równorzędnych](../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [Pojęcia kanałów równorzędnych](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
