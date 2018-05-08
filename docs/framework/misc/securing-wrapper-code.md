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
ms.openlocfilehash: ac278a4a3b06e0611e1cf57d079516a1dccf606b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="securing-wrapper-code"></a>Zabezpieczanie kodu otoki
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Kod otoki, szczególnie gdy otoka ma zaufania wyższe niż kod, który korzysta z niego, można otworzyć unikatowy zestaw słabych zabezpieczeń. Wszystko gotowe imieniu obiekt wywołujący, gdzie ograniczone uprawnienia obiektu wywołującego nie znajdują się w wyboru odpowiednich ustawień zabezpieczeń, to potencjalne osłabienia wykorzystanie.  
  
 Nigdy nie włączyć coś otoki, który obiekt wywołujący nie może sam. Jest to specjalne zagrożenie, gdy ten element, który obejmuje kontrolę ograniczonych zabezpieczeń, zamiast żądanie przeszukiwania pełnego stosu. W przypadku poziom kontroli interposing kod otoki między rzeczywistych wywołującego i element interfejsu API w pytanie łatwo może spowodować sprawdzania zabezpieczeń, aby możliwe, gdy jest on powinien nie, a tym samym osłabienia zabezpieczeń.  
  
## <a name="delegates"></a>Delegaty  
 Delegat zabezpieczeń różni się od wersji programu .NET Framework.  W tej sekcji opisano zachowania innego obiektu delegowanego i skojarzone zagadnienia dotyczące zabezpieczeń.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>W wersji 1.0, 1.1 programu .NET Framework  
 Akcje zabezpieczeń wersja 1.0 i 1.1 platformy .NET, wykonaj poniższe czynności przed twórcy delegata i obiekt wywołujący delegata.  
  
-   Po utworzeniu delegata zabezpieczeń linkdemand dla metody docelowego delegata są wykonywane względem zestawu twórcy obiektu delegowanego.  Nieprzestrzeganie akcji zabezpieczeń powoduje <xref:System.Security.SecurityException>.  
  
-   Po wywołaniu delegata są wykonywane wszystkie istniejące żądania kontroli zabezpieczeń na wywołującego delegata.  
  
 Zawsze, gdy trwa kodu <xref:System.Delegate> z kodu niższym poziomie zaufania, które może wywołać ją, upewnij się, że nie włączasz kod zaufany mniej eskalować uprawnienia. Przypadku trwać delegata i używać go później, kod utworzenia delegata nie jest w stosie wywołań, a jego uprawnienia nie zostanie sprawdzona, jeśli kod w lub na podstawie delegata prób chronionych operacji. Jeśli kod i kod wywołujący uprawnień wyższe niż twórca, twórca można organizować ścieżki wywołania nie są częścią stosu wywołań.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>W wersji 2.0 i nowszych wersji programu .NET Framework  
 W przeciwieństwie do poprzednich wersji w wersji 2.0 i nowszych wersji programu .NET Framework wykonuje akcję zabezpieczeń przed twórca delegata podczas tworzenia i wywołuje delegata.  
  
-   Po utworzeniu delegata zabezpieczeń linkdemand dla metody docelowego delegata są wykonywane względem zestawu twórcy obiektu delegowanego.  Nieprzestrzeganie akcji zabezpieczeń powoduje <xref:System.Security.SecurityException>.  
  
-   Zestaw uprawnień twórcy obiektu delegowanego jest również przechwycone podczas tworzenia obiektu delegowanego i przechowywane z obiektem delegowanym.  
  
-   Po wywołaniu delegat przechwyconych zestawu twórcy delegata najpierw zostaną ocenione względem wszystkie żądania w bieżącym kontekście, jeśli delegat twórcę i wywołującego należą do różnych zestawów.  Następnie wszystkie istniejące żądania kontroli zabezpieczeń na wywołującego delegata są wykonywane.  
  
## <a name="link-demands-and-wrappers"></a>Żądania łączy i otoki  
 W infrastrukturze zabezpieczeń została wzmocniona przypadku specjalnej ochrony z żądaniem linkdemand, ale nadal jest źródłem możliwe osłabienia w kodzie.  
  
 Jeśli pełni zaufany kod wywołuje właściwości, zdarzenia lub metoda chronione przez [LinkDemand](../../../docs/framework/misc/link-demands.md), wywołanie zakończy się pomyślnie, jeśli **LinkDemand** spełnieniu sprawdzenie uprawnień do obiektu wywołującego. Ponadto, jeśli pełni zaufanego kodu udostępnia klasę pobierającej nazwę właściwości i wywołania jego **uzyskać** dostępu za pomocą odbicia, które wywołanie **uzyskać** dostępu zakończy się powodzeniem, nawet jeśli kod użytkownika wykonuje nie ma prawa dostępu do tej właściwości. Jest to spowodowane **LinkDemand** sprawdza tylko bezpośredniego obiektu wywołującego, który jest całkowicie zaufanego kodu. W zasadzie całkowicie zaufanego kodu jest wywołania uprzywilejowanych imieniu kod użytkownika bez upewnieniu się, że kod użytkownik ma prawo do wprowadzania tego wywołania.  
  
 Aby zapobiec takiej luk w zabezpieczeniach, środowisko uruchomieniowe języka wspólnego rozszerza wyboru do pełnej przejście stosu zażąda na wszelkie pośrednie wywołanie do metody, konstruktora, właściwość lub zdarzenie chronione przez **LinkDemand**. Ta ochrona ponosi pewne koszty wydajności i zmienia semantykę kontroli zabezpieczeń. żądanie pełnego przeszukiwana stosu mogą wystąpić błędy, gdzie będzie przekazanego wyboru szybsze, jeden poziom.  
  
## <a name="assembly-loading-wrappers"></a>Otoki ładowania zestawu  
 Kilka metod używana do załadowania kodu zarządzanego włącznie z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, ładowanie zestawów dowody obiektu wywołującego. Jeśli opakowaniem jednej z tych metod system zabezpieczeń można użyć udzielanie uprawnień swój kod, zamiast uprawnienia obiektu wywołującego do Twojej otoki załadować zestawów. Nie należy zezwalać na niższym poziomie zaufania kod, aby załadować kodu, który jest wyższy uprawnień niż obiekt wywołujący, aby Twoje otoki.  
  
 Wszelki kod, który ma pełne zaufanie lub zaufania znacznie wyższa niż obiekt wywołujący potencjalnych (w tym Internet uprawnienia obiektu wywołującego) może obniżyć poziom zabezpieczeń w ten sposób. Jeśli kod ma publicznej metody, która przyjmuje tablicę bajtów i przekazuje je do **metody Assembly.Load**, co umożliwia tworzenie zestawu w imieniu wywołującego, go może spowodować uszkodzenie zabezpieczeń.  
  
 Ten problem dotyczy następujących elementów interfejsu API:  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Żądanie programu vs. Żądanie LinkDemand  
 Zabezpieczenia deklaracyjne oferuje dwa rodzaje kontroli zabezpieczeń, które są podobne, ale sprawdzana jest bardzo różnią się. Zarówno formularzy należy poznać, ponieważ błędnego wyboru może spowodować utratę słabe zabezpieczeń lub wydajności.  
  
 Zabezpieczenia deklaracyjne oferuje następujące kontrole zabezpieczeń:  
  
-   <xref:System.Security.Permissions.SecurityAction.Demand> Określa przeszukiwania stosu zabezpieczeń dostępu kodu. Wszystkich obiektów wywołujących na stosie musi mieć określone uprawnienie lub tożsamości do przekazania. **Żądanie** wykonywane przy każdym wywołaniu, ponieważ stos mogą zawierać różne elementy wywołujące. Jeśli wielokrotnie wywołania metody to sprawdzanie zabezpieczeń jest wykonywane zawsze. **Żądanie** dobrej ochrony przed atakami; zapewnienia zostanie wykryty nieautoryzowanego kodu próby pobrania za jego pośrednictwem.  
  
-   [Żądanie LinkDemand](../../../docs/framework/misc/link-demands.md) odbywa się na czas kompilacji just in time (JIT) i sprawdza tylko bezpośredniego obiektu wywołującego. Ta kontrola zabezpieczeń nie sprawdza obiekt wywołujący obiektu wywołującego. Po pomyślnej ten test, nie istnieje żadne dodatkowe zabezpieczenia narzut niezależnie od tego, ile razy może wywołać obiekt wywołujący. Ponieważ nie ma również nie ochrona przed atakami zapewnienia. Z **LinkDemand**, kodu, który przekazuje testu i może się odwoływać kod potencjalnie może uszkodzić zabezpieczeń przez złośliwy kod wywołać przy użyciu autoryzowanego kodu. W związku z tym nie należy używać **LinkDemand** chyba, że wszystkie możliwe słabe punkty można uniknąć dokładnie.  
  
    > [!NOTE]
    >  W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], linkdemand zostały zastąpione przez <xref:System.Security.SecurityCriticalAttribute> atrybutu w <xref:System.Security.SecurityRuleSet.Level2> zestawów. <xref:System.Security.SecurityCriticalAttribute> Jest odpowiednikiem żądanie łącza dla pełnego zaufania, jednak również wpływa na zasady dziedziczenia. Aby uzyskać więcej informacji na temat tej zmiany, zobacz [kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 Dodatkowe środki ostrożności, wymagane, gdy usługa **LinkDemand** musi być programowane pojedynczo; może systemu zabezpieczeń, pomoc wymuszania. Wszelkie błędu otwiera osłabienia zabezpieczeń. Wszystkie autoryzowane kodu, że używa Twój kod musi być odpowiedzialny za zaimplementowanie dodatkowych zabezpieczeń w następujący sposób:  
  
-   Ograniczanie dostępu wywołującego kodu do klasy lub zestawu.  
  
-   Wprowadzenie do zabezpieczeń tego samego kontroli kodu wywołującego, który pojawia się na wywoływanego kodu i obligating jego wywołań, aby to zrobić. Na przykład, jeśli pisania kodu, który wywołuje metodę, która jest chroniony za pomocą **LinkDemand** dla <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> Flaga określona, również powinny być metodę **LinkDemand** (lub **Żądanie**, który jest mocniejszy) dla tego uprawnienia. Wyjątek stanowi, jeśli używa Twój kod **LinkDemand**-Metoda chroniona w sposób ograniczony, który ma jest bezpieczne, podane innych mechanizmów ochrony zabezpieczeń (na przykład wymagania) w kodzie. W tym przypadku wyjątkowych wywołującego ma odpowiedzialność za osłabienia ochrony zabezpieczeń kodu źródłowego.  
  
-   Zapewnienie, że wywoływania z kodu nie można wymuszać kodu wywoływanie chronionych kodu w ich imieniu. Innymi słowy wywołań nie może wymusić autoryzowanego kodu do przekazania parametrów określonych w kodzie chronionych lub uzyskiwać wyniki z powrotem od niego.  
  
### <a name="interfaces-and-link-demands"></a>Interfejsy i żądania łączy  
 Jeśli wirtualny metoda, właściwość lub zdarzenie z **LinkDemand** zastępuje metodę klasy podstawowej metody klasy podstawowej również muszą mieć ten sam **LinkDemand** przesłoniętej metody w celu wprowadzenia. Istnieje możliwość złośliwego kodu można rzutować typu podstawowego i wywołanie metody klasy podstawowej. Również należy pamiętać, że link wymagań można dodać niejawnie do zestawów, które nie mają <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybut na poziomie zestawu.  
  
 Dobrym rozwiązaniem do ochrony implementacje metod z żądaniem linkdemand, gdy metody interfejsu muszą również linkdemand jest. Należy pamiętać, że o korzystaniu z interfejsami linkdemand:  
  
-   Jeśli umieścisz **LinkDemand** w publicznej metody klasy, która implementuje metody interfejsu **LinkDemand** nie będą wymuszane, jeśli następnie rzutowane na interfejs i wywołania metody. W takim przypadku ponieważ powiązane interfejsu tylko **LinkDemand** w interfejsie jest go uznać.  
  
 Sprawdź następujące elementy związane z zabezpieczeniami:  
  
-   Jawne linkdemand dla metod interfejsu. Upewnij się, te linkdemand zapewniają ochronę oczekiwanego. Ustal, czy złośliwy kod może używać rzutowanie uzyskanie wokół linkdemand opisanych powyżej.  
  
-   Metody wirtualne z żądaniem linkdemand zastosowane.  
  
-   Typy i interfejsów, które miały zaimplementowane. Te należy używać linkdemand spójnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
