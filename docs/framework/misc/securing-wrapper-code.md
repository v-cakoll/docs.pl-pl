---
title: Zabezpieczanie kodu otoki
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
ms.openlocfilehash: 3d38a4d4fd33798cf5987f5ce67305725ad9daec
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215847"
---
# <a name="securing-wrapper-code"></a>Zabezpieczanie kodu otoki
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Kod otoki, szczególnie w przypadku, gdy otoka ma wyższy poziom zaufania niż kod, który go używa, może otwierać unikatowy zestaw słabych zabezpieczeń. Wszystkie elementy wykonywane w imieniu obiektu wywołującego, w którym ograniczone uprawnienia obiektu wywołującego nie są uwzględnione w odpowiednim sprawdzaniu zabezpieczeń, to potencjalna słaba próba wykorzystania.  
  
 Nigdy nie należy włączać elementu przez otokę, której obiekt wywołujący nie może sam wykonać. Jest to specjalne zagrożenie podczas wykonywania czynności obejmujących ograniczone sprawdzanie zabezpieczeń, w przeciwieństwie do żądania pełnego przechodzenia stosu. Gdy są wykorzystywane kontrole na jednym poziomie, zaproponowanie kodu otoki między rzeczywistym obiektem wywołującym i elementem interfejsu API w danej sytuacji może być w stanie łatwo spowodować pomyślne sprawdzenie zabezpieczeń, gdy nie będzie to miało wpływu na zabezpieczenia.  
  
## <a name="delegates"></a>Delegaty  
 Delegowanie zabezpieczeń różni się między wersjami .NET Framework.  W tej sekcji opisano różne zachowania delegata i powiązane zagadnienia dotyczące zabezpieczeń.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>W wersji 1,0 i 1,1 .NET Framework  
 W wersji 1,0 i 1,1 .NET Framework wykonać następujące akcje zabezpieczeń wobec twórcy delegatów i obiektu wywołującego delegata.  
  
- Gdy obiekt delegowany jest tworzony, żądania zabezpieczeń dotyczące metody obiektu docelowego delegata są wykonywane względem zestawu uprawnień twórcy delegowania.  Niespełnienie wyników akcji zabezpieczeń w <xref:System.Security.SecurityException>.  
  
- Gdy obiekt delegowany jest wywoływany, wszystkie istniejące wymagania dotyczące zabezpieczeń w obiekcie wywołującym delegata są wykonywane.  
  
 Za każdym razem, gdy kod pobiera <xref:System.Delegate> z mniej zaufanego kodu, który może go wywoływać, należy się upewnić, że nie jest włączona niegodny zaufania kod w celu eskalacji jego uprawnień. Jeśli obiekt delegowany zostanie użyty później, kod, który utworzył delegata, nie znajduje się na stosie wywołań i jego uprawnienia nie będą badane, jeśli kod w lub w obszarze delegat próbuje wykonać operację chronioną. Jeśli kod i kod wywołujący mają wyższe uprawnienia niż twórca, twórca może organizować ścieżkę wywołania bez części stosu wywołań.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>W wersji 2,0 i nowszych .NET Framework  
 W przeciwieństwie do poprzednich wersji, wersja 2,0 i nowsze wersje .NET Framework wykonuje akcję zabezpieczeń względem twórcy delegata, gdy delegat zostanie utworzony i wywołany.  
  
- Gdy obiekt delegowany jest tworzony, żądania zabezpieczeń dotyczące metody obiektu docelowego delegata są wykonywane względem zestawu uprawnień twórcy delegowania.  Niespełnienie wyników akcji zabezpieczeń w <xref:System.Security.SecurityException>.  
  
- Zestaw dotacji twórcy delegata jest również przechwytywany podczas tworzenia delegata i przechowywany z delegatem.  
  
- Gdy obiekt delegowany jest wywoływany, wychwycony zestaw dotacji twórcy delegowanego jest najpierw oceniany względem wszelkich żądań w bieżącym kontekście, jeśli twórca delegata i obiekt wywołujący należą do różnych zestawów.  Następnie zostaną wykonane wszelkie istniejące wymagania dotyczące zabezpieczeń dotyczące obiektu wywołującego delegowania.  
  
## <a name="link-demands-and-wrappers"></a>Wymagania dotyczące linków i otoki  
 Specjalna sprawa ochrony z wymaganiami dotyczącymi linków została wzmocniona w infrastrukturze zabezpieczeń, ale nadal jest źródłem możliwej słabej przyczyny w kodzie.  
  
 Jeśli w pełni zaufany kod wywołuje właściwość, zdarzenie lub metodę chronioną przez [LinkDemand](link-demands.md), wywołanie powiedzie się, jeśli zostanie spełnione sprawdzenie uprawnień **LinkDemand** dla elementu wywołującego. Ponadto jeśli w pełni zaufany kod ujawnia klasę, która przyjmuje nazwę właściwości i wywołuje metodę dostępu **Get** przy użyciu odbicia, to wywołanie metody dostępu **Get** powiedzie się, mimo że kod użytkownika nie ma prawa dostępu do tej właściwości. Wynika to z faktu, że **LinkDemand** sprawdza tylko bezpośredni obiekt wywołujący, który jest w pełni zaufanym kodem. W zasadzie w pełni zaufany kod dokonuje uprzywilejowanego wywołania w imieniu kodu użytkownika bez upewnienia się, że kod użytkownika ma prawo do tego wywołania.  
  
 Aby zapobiec występowaniu takich luk w zabezpieczeniach, środowisko uruchomieniowe języka wspólnego rozszerza kontrolę na pełne zapotrzebowanie na stosy dla każdego pośredniego wywołania metody, konstruktora, właściwości lub zdarzenia chronionego przez **LinkDemand**. Ta ochrona wiąże się z pewnymi kosztami wydajności i zmienia semantykę kontroli zabezpieczeń; pełne żądanie przechodzenia stosu może zakończyć się niepowodzeniem w przypadku szybszego sprawdzenia na jednym poziomie.  
  
## <a name="assembly-loading-wrappers"></a>Otoki ładowania zestawu  
 Kilka metod służących do ładowania kodu zarządzanego, w tym <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, ładowania zestawów z dowodem wywołującym. W przypadku oblewania którejkolwiek z tych metod system zabezpieczeń może użyć przydzielenia uprawnień kodu zamiast uprawnień obiektu wywołującego do otoki, aby załadować zestawy. Nie należy zezwalać na ładowanie kodu, który ma wyższy poziom uprawnień niż w przypadku obiektu wywołującego do otoki.  
  
 Każdy kod z pełnym zaufaniem lub znacznie wyższym zaufaniem niż potencjalny obiekt wywołujący (w tym obiekt wywołujący na poziomie uprawnień internetowych) może osłabić zabezpieczenia w ten sposób. Jeśli kod ma metodę publiczną, która pobiera tablicę bajtową i przekazuje ją do **zestawu. Load**, tworząc zestaw w imieniu obiektu wywołującego, może przerwać zabezpieczenia.  
  
 Ten problem dotyczy następujących elementów interfejsu API:  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Kontrola na żądanie a kontrola typu LinkDemand  
 Zabezpieczenia deklaracyjne oferują dwa rodzaje kontroli zabezpieczeń, które są podobne, ale wykonują bardzo różne sprawdzenia. Należy zrozumieć obie formy, ponieważ niewłaściwy wybór może spowodować słabe zabezpieczenia lub utratę wydajności.  
  
 Zabezpieczenia deklaracyjne oferują następujące sprawdzenia zabezpieczeń:  
  
- <xref:System.Security.Permissions.SecurityAction.Demand> określa przeszukiwanie stosu zabezpieczeń dostępu kodu. Wszystkie obiekty wywołujące na stosie muszą mieć określone uprawnienie lub tożsamość do przekazania. **Żądanie** występuje dla każdego wywołania, ponieważ stos może zawierać różne obiekty wywołujące. Jeśli wywołasz metodę wielokrotnie, to sprawdzanie zabezpieczeń odbywa się za każdym razem. **Zapotrzebowanie** jest dobrą ochronę przed atakami luringymi; zostanie wykryty nieautoryzowany kod, który próbuje się pobrać.  
  
- [LinkDemand](link-demands.md) odbywa się w czasie kompilacji just-in-Time (JIT) i sprawdza tylko bezpośredni obiekt wywołujący. To sprawdzenie zabezpieczeń nie sprawdza wywołującego obiektu wywołującego. Po pomyślnym sprawdzeniu nie ma żadnych dodatkowych obciążeń związanych z zabezpieczeniami niezależnie od tego, ile razy proces wywołujący może wywoływać. Nie ma jednak żadnej ochrony przed atakami luring. Dzięki **LinkDemand**każdy kod, który przekazuje test i może odwoływać się do kodu, może potencjalnie przerwać zabezpieczenia, umożliwiając złośliwemu kodowi wywoływanie przy użyciu autoryzowanego kodu. W związku z tym nie należy używać **LinkDemand** , chyba że wszystkie możliwe słabe luki nie będą widoczne.  
  
    > [!NOTE]
    > W .NET Framework 4 wymagania dotyczące linków zostały zastąpione przez atrybut <xref:System.Security.SecurityCriticalAttribute> w zestawach <xref:System.Security.SecurityRuleSet.Level2>. <xref:System.Security.SecurityCriticalAttribute> jest równoważne żądanie linku do pełnego zaufania; jednak ma także wpływ na reguły dziedziczenia. Aby uzyskać więcej informacji na temat tej zmiany, zobacz [kod przezroczysty zabezpieczeń, poziom 2](security-transparent-code-level-2.md).  
  
 Dodatkowe środki ostrożności wymagane, gdy użycie **LinkDemand** muszą być zaprogramowane osobno; System zabezpieczeń może pomóc wymuszać. Dowolny błąd powoduje otwarcie luki w zabezpieczeniach. Cały autoryzowany kod, który korzysta z kodu, musi być odpowiedzialny za wdrożenie dodatkowych zabezpieczeń, wykonując następujące czynności:  
  
- Ograniczanie dostępu do kodu wywołującego do klasy lub zestawu.  
  
- Umieszczenie tego samego sprawdzenia zabezpieczeń na wywoływanym kodzie, który pojawia się na wywoływanym kodzie i obligating jego wywołujący. Na przykład, jeśli piszesz kod, który wywołuje metodę, która jest chroniona za pomocą **LinkDemand** dla <xref:System.Security.Permissions.SecurityPermission> z określoną flagą <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>, metoda powinna również wykonać **LinkDemand** (lub **żądanie**, które jest silniejsze) dla tego uprawnienia. Wyjątek polega na tym, że kod korzysta z metody chronionej przez **LinkDemand**w ograniczony sposób, który jest bezpieczny, z uwzględnieniem innych mechanizmów ochrony zabezpieczeń (takich jak wymagania) w kodzie. W tym wyjątkowym przypadku wywołujący odpowiada za osłabienie ochrony zabezpieczeń w kodzie źródłowym.  
  
- Upewnienie się, że wywołujący kod nie może dochodzić do kodu w celu wywołania chronionego kodu w ich imieniu. Innymi słowy, obiekty wywołujące nie mogą wymusić, aby uprawniony kod mógł przekazać określone parametry do chronionego kodu lub uzyskać z powrotem wyniki.  
  
### <a name="interfaces-and-link-demands"></a>Interfejsy i wymagania dotyczące linków  
 Jeśli wirtualna metoda, właściwość lub zdarzenie z **LinkDemand** przesłania metodę klasy bazowej, metoda klasy bazowej musi również mieć ten sam **LinkDemand** dla zastąpionej metody, aby obowiązywać. Istnieje możliwość, że złośliwy kod będzie rzutować z powrotem na typ podstawowy i wywołać metodę klasy bazowej. Należy również zauważyć, że wymagania dotyczące linków mogą być dodawane niejawnie do zestawów, które nie mają atrybutu na poziomie zestawu <xref:System.Security.AllowPartiallyTrustedCallersAttribute>.  
  
 Dobrym sposobem jest ochrona implementacji metod za pomocą żądań linków, gdy metody interfejsu również mają wymagania dotyczące linków. Należy pamiętać o następujących kwestiach dotyczących używania żądań linków z interfejsami:  
  
- Jeśli umieścisz **LinkDemand** na metodzie publicznej klasy implementującej metodę interfejsu, **LinkDemand** nie zostanie wymuszony, jeśli następnie rzutowane do interfejsu i Wywołaj metodę. W tym przypadku, ponieważ połączono z interfejsem, tylko **LinkDemand** w interfejsie jest uznawany za.  
  
 Przejrzyj następujące elementy dotyczące problemów z zabezpieczeniami:  
  
- Jawne wymagania dotyczące linków w metodach interfejsu. Upewnij się, że te wymagania dotyczące linków oferują oczekiwaną ochronę. Należy określić, czy złośliwy kod może użyć rzutowania, aby uzyskać więcej, jak opisano powyżej.  
  
- Zastosowano metody wirtualne z wymaganiami dotyczącymi linków.  
  
- Typy i interfejsy, które implementują. Należy spójnie stosować wymagania dotyczące linków.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
