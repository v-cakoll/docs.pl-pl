---
title: Zabezpieczanie kodu otoki
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c74a130c078077d9f692fbf6107e9d5aefc16b9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505942"
---
# <a name="securing-wrapper-code"></a>Zabezpieczanie kodu otoki
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Kod otoki, szczególnie w przypadku gdy otoki ma zaufania wyższe niż kod, który korzysta z niego, można otworzyć unikatowy zestaw luk zabezpieczeń. Wszystko gotowe w imieniu obiekt wywołujący, gdzie wywołującego ograniczone uprawnienia nie są uwzględnione w wyboru odpowiednich zabezpieczeń, jest słabość potencjalne wykorzystanie.  
  
 Nigdy nie umożliwiają coś otok, który obiekt wywołujący nie może sam. Jest to szczególne zagrożenie, gdy wykonuje określone operacje, które obejmuje sprawdzanie zabezpieczeń ograniczona, a nie żądanie przeszukiwania pełnego stosu. W przypadku poziom kontroli interposing kod otoki między rzeczywistego obiektu wywołującego, a element interfejsu API w pytaniu mogą łatwo spowodować sprawdzania zabezpieczeń, aby pomyślnie wykonane po jego powinna nie, a tym samym osłabienia zabezpieczeń.  
  
## <a name="delegates"></a>Delegaty  
 Delegat zabezpieczeń różni się między wersjami programu .NET Framework.  W tej sekcji opisano zachowania różnych delegata i skojarzone zagadnienia dotyczące zabezpieczeń.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>W wersji 1.0 i 1.1 programu .NET Framework  
 Akcje zabezpieczeń wersja 1.0 i 1.1 programu .NET Framework, wykonaj następujące czynności przed twórcy delegata, jak i obiekt wywołujący delegata.  
  
-   Podczas tworzenia delegata zabezpieczeń zapotrzebowania na łącza na metody delegata w docelowej są wykonywane względem zestaw uprawnień twórcy delegata.  Niespełnienie akcji zabezpieczeń powoduje <xref:System.Security.SecurityException>.  
  
-   Gdy obiekt delegowany jest wywoływany, są wykonywane żadnych istniejących wymogów bezpieczeństwa na obiekcie wywołującym delegata.  
  
 Zawsze, gdy kod przyjmuje <xref:System.Delegate> kodu niższym poziomie zaufania, który może wywołać go, upewnij się, nie włączasz kod niższym poziomie zaufania, aby eskalować uprawnienia. Jeśli wykonać delegata i użyć go później, kod, który utworzony delegat nie znajduje się na stosie wywołań i jego uprawnienia nie zostaną przetestowane, jeśli kod w lub na podstawie obiektu delegowanego prób chronionej operacji. Jeśli Twój kod i kod wywołujący ma uprawnienia wyższe niż twórca, twórca można organizować ścieżki wywołania nie są częścią stosu wywołań.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>W wersji 2.0 i nowszych wersjach programu .NET Framework  
 W przeciwieństwie do poprzednich wersji wersji 2.0 i nowszych wersjach .NET Framework wykonuje akcję zabezpieczeń względem Autor delegowanego Jeśli delegat jest tworzony i o nazwie.  
  
-   Podczas tworzenia delegata zabezpieczeń zapotrzebowania na łącza na metody delegata w docelowej są wykonywane względem zestaw uprawnień twórcy delegata.  Niespełnienie akcji zabezpieczeń powoduje <xref:System.Security.SecurityException>.  
  
-   Zestaw uprawnień twórcy delegata jest również przechwycony podczas tworzenia delegata i przechowywane z obiektem delegowanym.  
  
-   Gdy obiekt delegowany jest wywoływany, twórca delegata przechwyconych przydzielonym zestawie najpierw zostaną ocenione względem dowolnego żądania w bieżącym kontekście, jeśli twórca delegata i element wywołujący należą do różnych zestawów.  Następnie są wykonywane żadnych istniejących wymogów bezpieczeństwa na obiekcie wywołującym delegata.  
  
## <a name="link-demands-and-wrappers"></a>Żądania połączeń i otoki  
 Przypadek specjalny ochrony za pomocą zapotrzebowania na łącza została wzmocniona w ramach infrastruktury zabezpieczeń, ale nadal jest źródłem możliwe słabość w kodzie.  
  
 Jeśli w pełni zaufany kod wywołuje właściwości, zdarzenia lub metoda chronione przez [LinkDemand](../../../docs/framework/misc/link-demands.md), wywołanie zakończy się pomyślnie, jeśli **LinkDemand** sprawdzenie uprawnień do obiektu wywołującego jest spełniony. Ponadto, jeśli całkowicie zaufanego kodu udostępnia klasę, przyjmuje nazwę właściwości i wywołuje jego **uzyskać** przy użyciu odbicia, że wywołanie metody dostępu **uzyskać** dostępu zakończy się pomyślnie, nawet jeśli kod użytkownika realizuje nie ma uprawnień do dostępu do tej właściwości. Jest to spowodowane **LinkDemand** sprawdza tylko bezpośredniego wywołującego, która jest całkowicie zaufanego kodu. W zasadzie w pełni zaufany kod wywołuje element uprzywilejowanych imieniu kod użytkownika bez upewniając się, że kod użytkownika ma uprawnienia do wykonania tego wywołania.  
  
 Aby uniknąć takich luk w zabezpieczeniach, środowisko uruchomieniowe języka wspólnego rozszerzenie wyboru do pełnej zalet stosu zapotrzebowanie na każde wywołanie pośrednie metoda, Konstruktor, właściwość lub zdarzenie chronione przez **LinkDemand**. Ta ochrona jest naliczana pewne koszty wydajności i zmienia semantykę kontroli zabezpieczeń. żądanie przejście przez stos może przestać działać, gdzie będzie przeszły sprawdzania szybciej i jeden poziom.  
  
## <a name="assembly-loading-wrappers"></a>Otoki ładowania zestawu  
 Kilka metod, używana do ładowania kodu zarządzanego, w tym <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, ładować zestawów z dowodem obiektu wywołującego. Jeśli opakowaniem dowolnej z tych metod system zabezpieczeń za pomocą udzielenia uprawnień kodu, zamiast uprawnień obiekt wywołujący, aby Twoje otoki załadować zestawy. Nie należy zezwalać na niższym poziomie zaufania kod, aby załadować kod, który otrzymuje wyższych uprawnień niż te, które obiekt wywołujący, aby Twoje otoki.  
  
 Wszelki kod, który ma pełnego zaufania lub zaufania znacznie wyższa niż obiekt wywołujący potencjalnych (w tym Internetu uprawnienia poziomu obiektu wywołującego) może obniżyć poziom zabezpieczeń w ten sposób. Jeśli kod zawiera metodę publiczną, która przyjmuje tablicę bajtów i przekazuje go do **Assembly.Load**, a tym samym tworzenia zestawu w imieniu obiektu wywołującego, jego mogłyby spowodować przerwanie działania zabezpieczeń.  
  
 Ten problem dotyczy następujących elementów interfejsu API:  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Żądanie programu vs. LinkDemand  
 Zabezpieczenia deklaratywne oferuje dwa rodzaje zabezpieczeń sprawdza, czy są podobne, ale kontrole bardzo różnią się. Należy zrozumieć obie formy, ponieważ błędnego wyboru może spowodować utratę słabe zabezpieczeń i wydajności.  
  
 Zabezpieczenia deklaratywne oferuje następujące kontrole zabezpieczeń:  
  
-   <xref:System.Security.Permissions.SecurityAction.Demand> Określa przeszukiwania stosu zabezpieczeń dostępu kodu. Wszystkie obiekty wywołujące w stosie musi mieć określone uprawnienie lub tożsamości w celu przekazania. **Żądanie** występuje w przypadku każdego wywołania, ponieważ stos może zawierać różne obiekty wywołujące. Tego sprawdzenia zabezpieczeń występuje zawsze, jeśli wielokrotne wywołania metody. **Żądanie** jest dobrą ochronę przed atakami; zapewnienia nieautoryzowanego kodu próby uzyskania przez nią zostanie wykryty.  
  
-   [Żądanie LinkDemand](../../../docs/framework/misc/link-demands.md) się dzieje w momencie kompilacji just-in-time (JIT) i sprawdza, czy tylko bezpośredniego wywołującego. Tego sprawdzenia zabezpieczeń nie sprawdza obiekt wywołujący obiektu wywołującego. Po pomyślnej to sprawdzenie nie istnieje żadne dodatkowe zabezpieczenia, obciążenie niezależnie od tego, ile razy może wywołać obiekt wywołujący. Istnieje jednak także nie ochrony przed atakami zapewnienia. Za pomocą **LinkDemand**, umożliwiając złośliwego kodu do wywołania, przy użyciu kodu autoryzowanych wszelki kod, który przejdzie test i może przywoływać kod może potencjalnie uszkodzić zabezpieczeń. W związku z tym, nie używaj **LinkDemand** chyba, że wszystkie możliwe luki zabezpieczeń można uniknąć dokładnie.  
  
    > [!NOTE]
    >  W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zapotrzebowanie na łącza zostały zastąpione przez <xref:System.Security.SecurityCriticalAttribute> atrybutu w <xref:System.Security.SecurityRuleSet.Level2> zestawów. <xref:System.Security.SecurityCriticalAttribute> Jest odpowiednikiem zapotrzebowania na łącza, aby uzyskać pełne zaufanie; jednak również wpływa na zasady dziedziczenia. Aby uzyskać więcej informacji na temat tej zmiany, zobacz [kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 Dodatkowe środki ostrożności, wymagany, gdy za pomocą **LinkDemand** musi być zaprogramowany pojedynczo; może system zabezpieczeń, pomoc dotycząca wymuszania. Wszelkie błędu zostanie otwarty do osłabienia zabezpieczeń. Wszystkie autoryzowane kodu, że używa Twój kod musi być odpowiedzialne za wykonanie dodatkowe zabezpieczenia, wykonując następujące czynności:  
  
-   Ograniczanie dostępu do kodu wywołującego do klasy lub zestawu.  
  
-   Wprowadzenie do zabezpieczeń tego samego kontroli kodu wywołującego, wyświetlane na wywoływanego kodu i obligating wywołujące, aby to zrobić. Na przykład jeśli piszesz kod, który wywołuje metodę, która jest chroniona za pomocą **LinkDemand** dla <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> określone flagi, metoda również powinny być **LinkDemand** (lub **Żądanie**, który jest silniejszy) tego uprawnienia. Wyjątkiem jest, jeśli kod używa **LinkDemand**— Metoda chroniona w sposób ograniczony, możesz zdecydować, jak są bezpieczne, biorąc pod uwagę innych mechanizmów ochrony zabezpieczeń (na przykład żądania) w kodzie. W tym wyjątkowym przypadku obiekt wywołujący odpowiada w osłabienia ochrony zabezpieczeń na odpowiedni kod.  
  
-   Zapewnienie wywołujących swój kod nie może wymuszać kod do wywoływania chronionego kodu w ich imieniu. Innymi słowy obiekty wywołujące nie może wymusić autoryzowanego kodu przekazać określone parametry do chronionego kodu lub wrócić wyniki z niego.  
  
### <a name="interfaces-and-link-demands"></a>Interfejsy i zapotrzebowania na łącza  
 Jeśli metoda wirtualna, właściwość lub zdarzenie z **LinkDemand** zastępuje metodę klasy bazowej, metody klasy bazowej również muszą mieć taką samą **LinkDemand** dla przeciążonej, aby były skuteczne. Istnieje możliwość dla złośliwego kodu, można rzutować typu podstawowego i wywołać metodę klasy bazowej. Ponadto należy pamiętać, że link żądania można dodać niejawnie do zestawów, które nie mają <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybut na poziomie zestawu.  
  
 Jest dobrą praktyką chronić implementacje metod za pomocą zapotrzebowania na łącza, gdy metody interfejsu muszą również zapotrzebowania na łącza. Należy pamiętać o używaniu zapotrzebowania na łącza z interfejsów:  
  
-   Jeśli umieścisz **LinkDemand** w publicznej metodzie klasy, która implementuje metodę interfejsu **LinkDemand** nie zostaną wymuszone, jeśli następnie rzutowane na interfejs i wywołać metodę. W tym przypadku faktu, że połączone interfejsu tylko **LinkDemand** w interfejsie są uwzględniane.  
  
 Sprawdź następujące elementy związane z zabezpieczeniami:  
  
-   Zapotrzebowanie na łącza jawnych metod interfejsu. Upewnij się, zapotrzebowanie na łącza zapewniają oczekiwanego ochronę. Ustal, czy złośliwy kod może użyć rzutowania, aby obejść zapotrzebowania na łącza zgodnie z wcześniejszym opisem.  
  
-   Metody wirtualne linkdemand stosowane.  
  
-   Typy i interfejsy, które implementują. Te powinny używać żądań konsolidacji spójne.  
  
## <a name="see-also"></a>Zobacz także
- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
