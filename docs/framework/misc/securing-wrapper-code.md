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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399911"
---
# <a name="securing-wrapper-code"></a>Zabezpieczanie kodu otoki
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Kod otoki, zwłaszcza gdy otoka ma większe zaufanie niż kod, który go używa, można otworzyć unikatowy zestaw zabezpieczeń słabości. Wszystko, co zostało zrobione w imieniu osoby dzwoniącej, w której ograniczone uprawnienia osoby dzwoniącej nie są uwzględnione w odpowiedniej kontroli zabezpieczeń, jest potencjalną słabością, którą należy wykorzystać.  
  
 Nigdy nie włączaj czegoś za pośrednictwem otoki, że wywołujący nie może zrobić sam. Jest to szczególne niebezpieczeństwo podczas robienia czegoś, co wiąże się z ograniczoną kontrolą bezpieczeństwa, w przeciwieństwie do pełnego popytu na spacer stosu. Gdy kontrole na jednym poziomie są zaangażowane, interposing kod otoki między rzeczywistym wywołującego i elementu interfejsu API, o których mowa może łatwo spowodować sprawdzanie zabezpieczeń, aby zakończyć się pomyślnie, gdy nie powinno, osłabiając w ten sposób zabezpieczeń.  
  
## <a name="delegates"></a>Delegaty  
 Zabezpieczenia delegata różnią się między wersjami programu .NET Framework.  W tej sekcji opisano różne zachowania delegata i skojarzone zagadnienia dotyczące zabezpieczeń.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>W wersji 1.0 i 1.1 programu .NET Framework  
 Wersja 1.0 i 1.1 programu .NET Framework wykonują następujące akcje zabezpieczeń przeciwko twórcy delegata i wywołującemu delegata.  
  
- Po utworzeniu pełnomocnika żądania łącza zabezpieczeń dla metody docelowej delegata są wykonywane względem zestawu dotacji twórcy delegata.  Niespełnienie akcji zabezpieczeń powoduje <xref:System.Security.SecurityException>.  
  
- Po wywołaniu pełnomocnika wykonywane są wszystkie istniejące żądania zabezpieczeń na wywołującym delegata.  
  
 Za każdym razem, <xref:System.Delegate> gdy kod pobiera z mniej zaufanego kodu, który może go wywołać, upewnij się, że nie włączasz mniej zaufanego kodu, aby eskalować jego uprawnienia. Jeśli wziąć pełnomocnika i użyć go później, kod, który utworzył pełnomocnika nie jest na stosie wywołań i jego uprawnienia nie będą testowane, jeśli kod w lub w ramach delegata próbuje operacji chronionej. Jeśli kod i kod wywołującego mają wyższe uprawnienia niż twórca, twórca może zorganizować ścieżkę wywołania bez bycia częścią stosu wywołań.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>W wersji 2.0 i nowszych wersji programu .NET Framework  
 W przeciwieństwie do poprzednich wersji, wersja 2.0 i nowsze wersje programu .NET Framework wykonuje akcję zabezpieczeń przeciwko twórcy delegata podczas tworzenia i wywoływania pełnomocnika.  
  
- Po utworzeniu pełnomocnika żądania łącza zabezpieczeń dla metody docelowej delegata są wykonywane względem zestawu dotacji twórcy delegata.  Niespełnienie akcji zabezpieczeń powoduje <xref:System.Security.SecurityException>.  
  
- Zestaw dotacji twórcy delegata jest również przechwytywany podczas tworzenia delegata i przechowywany z pełnomocnikiem.  
  
- Gdy pełnomocnik jest wywoływany, zestaw przechwyconych dotacji twórcy delegata jest najpierw oceniany na podstawie wszelkich żądań w bieżącym kontekście, jeśli twórca delegata i wywołujący należą do różnych zestawów.  Następnie wykonywane są wszystkie istniejące wymagania zabezpieczeń dla wywołującego delegata.  
  
## <a name="link-demands-and-wrappers"></a>Żądania łączy i otoki  
 Specjalny przypadek ochrony z żądaniami łącza został wzmocniony w infrastrukturze zabezpieczeń, ale nadal jest źródłem możliwej słabości kodu.  
  
 Jeśli w pełni zaufany kod wywołuje właściwość, zdarzenie lub metodę chronioną przez [LinkDemand,](link-demands.md)wywołanie powiedzie się, jeśli sprawdzanie uprawnień **LinkDemand** dla obiektu wywołującego jest spełnione. Ponadto jeśli w pełni zaufany kod udostępnia klasę, która przyjmuje nazwę właściwości i wywołuje jego **get** akcesor przy użyciu odbicia, to wywołanie **get** akcesor zakończy się pomyślnie, mimo że kod użytkownika nie ma prawa dostępu do tej właściwości. Jest to spowodowane **LinkDemand** sprawdza tylko bezpośrednie wywołujących, który jest w pełni zaufany kod. W istocie w pełni zaufany kod jest wykonywanie uprzywilejowanego wywołania w imieniu kodu użytkownika bez upewnienia się, że kod użytkownika ma prawo do tego wywołania.  
  
 Aby zapobiec takim lukom w zabezpieczeniach, środowisko uruchomieniowe języka wspólnego rozszerza sprawdzanie na pełne żądanie przechodzenia stosu na wszelkie pośrednie wywołanie metody, konstruktora, właściwości lub zdarzenia chronionego przez **LinkDemand**. Ta ochrona wiąże się z pewnymi kosztami wydajności i zmienia semantycę kontroli zabezpieczeń; pełne żądanie stosu spacer może zakończyć się niepowodzeniem, gdzie szybciej, jednopoziomowe sprawdzanie by minęło.  
  
## <a name="assembly-loading-wrappers"></a>Opakowania załadunkowe do montażu  
 Kilka metod używanych do <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>ładowania kodu zarządzanego, w tym , załadować zestawy z dowodami wywołującego. Jeśli zawijasz dowolną z tych metod, system zabezpieczeń może użyć uprawnienia kodu, zamiast uprawnień wywołującego do otoki, aby załadować zestawy. Nie należy zezwalać na mniej zaufany kod, aby załadować kod, który jest przyznawany wyższe uprawnienia niż te wywołującego do otoki.  
  
 Każdy kod, który ma pełne zaufanie lub znacznie wyższe zaufanie niż potencjalny rozmówca (w tym wywołującego na poziomie uprawnień internetowych) może osłabić bezpieczeństwo w ten sposób. Jeśli kod ma metodę publiczną, która przyjmuje tablicę bajtów i przekazuje ją do **Assembly.Load**, tworząc w ten sposób zestaw w imieniu wywołującego, może to złamać zabezpieczenia.  
  
 Ten problem dotyczy następujących elementów interfejsu API:  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Kontrola na żądanie a kontrola typu LinkDemand  
 Deklaratywne zabezpieczenia oferuje dwa rodzaje kontroli zabezpieczeń, które są podobne, ale wykonać bardzo różne kontrole. Należy zrozumieć obie formy, ponieważ niewłaściwy wybór może spowodować słabe zabezpieczenia lub utratę wydajności.  
  
 Deklaratywne zabezpieczenia oferują następujące kontrole zabezpieczeń:  
  
- <xref:System.Security.Permissions.SecurityAction.Demand>określa spacer stosu zabezpieczeń dostępu do kodu. Wszystkie osoby wywołujące na stosie musi mieć określone uprawnienia lub tożsamości do przekazania. **Żądanie** występuje przy każdym wywołaniu, ponieważ stos może zawierać różne wywołania. Jeśli wywołasz metodę wielokrotnie, to sprawdzanie zabezpieczeń odbywa się za każdym razem. **Popyt** jest dobrą ochroną przed atakami zwabiania; nieautoryzowany kod próbuje przez to zostanie wykryty.  
  
- [LinkDemand](link-demands.md) dzieje się w czasie kompilacji just-in-time (JIT) i sprawdza tylko bezpośredniego wywołującego. Ta kontrola zabezpieczeń nie sprawdza rozmówcy wywołującego. Po przejściu tego sprawdzenia nie ma żadnych dodatkowych narzutów zabezpieczeń bez względu na to, ile razy wywołujący może wywołać. Jednak nie ma również ochrony przed atakami zwabianiem. Z **LinkDemand**, każdy kod, który przechodzi test i może odwołać się do kodu może potencjalnie złamać zabezpieczenia, umożliwiając złośliwy kod do wywołania przy użyciu autoryzowanego kodu. Dlatego nie należy używać **LinkDemand** chyba że wszystkie możliwe słabości można dokładnie uniknąć.  
  
    > [!NOTE]
    > W .NET Framework 4 żądania łączy zostały <xref:System.Security.SecurityCriticalAttribute> zastąpione <xref:System.Security.SecurityRuleSet.Level2> atrybutem w zestawach. Jest <xref:System.Security.SecurityCriticalAttribute> odpowiednikiem żądania łącza dla pełnego zaufania; ma jednak również wpływ na reguły dziedziczenia. Aby uzyskać więcej informacji na temat tej zmiany, zobacz [Security-Transparent Code, Poziom 2](security-transparent-code-level-2.md).  
  
 Dodatkowe środki ostrożności wymagane podczas korzystania z **LinkDemand** muszą być zaprogramowane indywidualnie; system bezpieczeństwa może pomóc w egzekwowaniu przepisów. Każdy błąd otwiera słabość zabezpieczeń. Wszystkie autoryzowane kody, który używa kodu musi być odpowiedzialny za wdrożenie dodatkowych zabezpieczeń, wykonując następujące czynności:  
  
- Ograniczanie dostępu kodu wywołującego do klasy lub zestawu.  
  
- Umieszczenie tych samych kontroli zabezpieczeń na kod wywołujący, które pojawiają się na kod wywoływany i zobowiązuje jego wywołujących do tego. Na przykład jeśli piszesz kod, który wywołuje metodę, która jest <xref:System.Security.Permissions.SecurityPermission> chroniona <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> za pomocą **LinkDemand** dla z flagą określoną, metoda powinna również dokonać **LinkDemand** (lub **Demand**, który jest silniejszy) dla tego uprawnienia. Wyjątek jest, jeśli kod używa **LinkDemand**-protected metody w ograniczony sposób, który zdecydujesz, jest bezpieczny, biorąc pod uwagę inne mechanizmy ochrony zabezpieczeń (takie jak wymagania) w kodzie. W tym wyjątkowym przypadku wywołujący bierze odpowiedzialność za osłabienie ochrony zabezpieczeń na kod podstawowej.  
  
- Upewniając się, że wywołania kodu nie może oszukać kodu do wywoływania chronionego kodu w ich imieniu. Innymi słowy wywołujących nie można wymusić autoryzowany kod przekazać określone parametry do chronionego kodu lub uzyskać wyniki z powrotem z niego.  
  
### <a name="interfaces-and-link-demands"></a>Interfejsy i żądania łączy  
 Jeśli metoda wirtualna, właściwość lub zdarzenie z **LinkDemand** zastępuje metodę klasy podstawowej, metoda klasy podstawowej musi mieć również taką samą **metodę LinkDemand** dla metody zastąpione, aby była skuteczna. Jest możliwe dla złośliwego kodu do rzutowania z powrotem do typu podstawowego i wywołać metodę klasy podstawowej. Należy również zauważyć, że żądania łącza można dodać niejawnie do zestawów, które nie mają atrybutu na <xref:System.Security.AllowPartiallyTrustedCallersAttribute> poziomie zestawu.  
  
 Jest dobrą praktyką, aby chronić implementacje metod z wymaganiami łącza, gdy metody interfejsu mają również wymagania łącza. Należy zwrócić uwagę na następujące informacje dotyczące używania żądań łączy z interfejsami:  
  
- Jeśli umieścisz **LinkDemand** na metodę publiczną klasy, która implementuje metodę interfejsu, **LinkDemand** nie będą wymuszane, jeśli następnie rzutowane do interfejsu i wywołać metodę. W takim przypadku, ponieważ połączone z **interfejsem, tylko LinkDemand** na interfejsie jest honorowany.  
  
 Przejrzyj następujące elementy w celu uzyskania problemów z zabezpieczeniami:  
  
- Jawne żądania łącza na metody interfejsu. Upewnij się, że te żądania łącza oferują oczekiwaną ochronę. Określ, czy złośliwy kod może używać rzutowania, aby obejść żądania łącza, jak opisano wcześniej.  
  
- Metody wirtualne z zastosowanymi żądaniami łącza.  
  
- Typy i interfejsy, które implementują. Powinny one używać żądań linków konsekwentnie.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
