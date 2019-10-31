---
title: 'Wskazówki: emitowanie kodu w scenariuszach częściowo zaufanych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection emit, anonymously hosted dynamic methods
- partial trust, reflection
- partial trust, emitting dynamic methods
- reflection emit, partial trust scenarios
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: c45be261-2a9d-4c4e-9bd6-27f0931b7d25
ms.openlocfilehash: fd420c9754494b95c55df403edec87743572db03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129990"
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>Wskazówki: emitowanie kodu w scenariuszach częściowo zaufanych

Emisja odbicia używa tego samego interfejsu API w pełnej lub częściowej relacji zaufania, ale niektóre funkcje wymagają specjalnych uprawnień w częściowo zaufanym kodzie. Ponadto emitowanie odbicia ma funkcję, anonimowo hostowane metody dynamiczne, która jest przeznaczona do użycia z częściowym zaufaniem i przez zestawy przezroczyste dla zabezpieczeń.

> [!NOTE]
> Przed .NET Framework 3,5, emitujący wymagany kod <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType>. To uprawnienie jest uwzględniane domyślnie w `FullTrust` i `Intranet` o nazwanych zestawach uprawnień, ale nie w `Internet` zestawie uprawnień. Z tego względu biblioteka może być używana z częściowej relacji zaufania tylko wtedy, gdy ma atrybut <xref:System.Security.SecurityCriticalAttribute>, a także wykonała metodę <xref:System.Security.PermissionSet.Assert%2A> dla <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Takie biblioteki wymagają starannej oceny zabezpieczeń, ponieważ błędy kodowania mogą spowodować powstanie luk w zabezpieczeniach. .NET Framework 3,5 umożliwia emitowanie kodu w scenariuszach częściowej relacji zaufania bez wydawania żadnych wymagań dotyczących zabezpieczeń, ponieważ generowanie kodu nie jest z założenia uprzywilejowanej operacji. Oznacza to, że wygenerowany kod nie ma więcej uprawnień niż zestaw, który emituje go. Pozwala to na używanie bibliotek, które emitują kod jako nieprzezroczysty, i eliminuje konieczność potwierdzenia <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, dzięki czemu pisanie bezpiecznej biblioteki nie wymaga takiego dokładnego przeglądu zabezpieczeń.

W instruktażu przedstawiono następujące zagadnienia:

- [Konfigurowanie prostej piaskownicy do testowania częściowo zaufanego kodu](#Setting_up).

  > [!IMPORTANT]
  > Jest to prosty sposób na eksperymentowanie z kodem w częściowej relacji zaufania. Aby uruchomić kod, który rzeczywiście pochodzi z niezaufanych lokalizacji, zobacz [jak: uruchamiać częściowo zaufany kod w piaskownicy](../misc/how-to-run-partially-trusted-code-in-a-sandbox.md).

- [Uruchamianie kodu w domenach częściowo zaufanych aplikacji](#Running_code).

- [Używanie anonimowo obsługiwanych metod dynamicznych do emisji i wykonywania kodu w częściowej relacji zaufania](#Using_methods).

Aby uzyskać więcej informacji na temat emitowania kodu w scenariuszach częściowej relacji zaufania, zobacz [problemy z zabezpieczeniami w emisji odbicia](security-issues-in-reflection-emit.md).

Aby zapoznać się z pełną listą kodu podanego w tych procedurach, zobacz [sekcję przykład](#Example) na końcu tego przewodnika.

<a name="Setting_up"></a>

## <a name="setting-up-partially-trusted-locations"></a>Konfigurowanie częściowo zaufanych lokalizacji

Poniższe dwie procedury pokazują, jak skonfigurować lokalizacje, z których można testować kod z częściowym zaufaniem.

- W pierwszej procedurze pokazano, jak utworzyć domenę aplikacji w trybie piaskownicy, w której kod otrzymuje uprawnienia internetowe.

- Druga procedura pokazuje, jak dodać <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> do domeny częściowo zaufanej aplikacji, aby umożliwić dostęp do prywatnych danych w zestawach równorzędnych lub mniej zaufania.

### <a name="creating-sandboxed-application-domains"></a>Tworzenie domen aplikacji w trybie piaskownicy

Aby utworzyć domenę aplikacji, w której zestawy działają z częściowym zaufaniem, należy określić zestaw uprawnień, które mają zostać przyznane zestawom przy użyciu przeciążenia metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>, aby utworzyć domenę aplikacji. Najprostszym sposobem określenia zestawu przydzielenia jest pobranie nazwanego zestawu uprawnień z zasad zabezpieczeń.

Poniższa procedura służy do tworzenia domeny aplikacji w trybie piaskownicy, która uruchamia kod z częściowym zaufaniem, do testowania scenariuszy, w których emitowany kod może uzyskać dostęp tylko do publicznych składowych typów publicznych. Kolejna procedura pokazuje, jak dodać <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>, aby przetestować scenariusze, w których emitowany kod może uzyskać dostęp do niepublicznych typów i elementów członkowskich w zestawach, które mają przyznane równe lub mniejsze uprawnienia.

#### <a name="to-create-an-application-domain-with-partial-trust"></a>Aby utworzyć domenę aplikacji z częściowym zaufaniem

1. Utwórz zestaw uprawnień do przydzielenia do zestawów w domenie aplikacji w trybie piaskownicy. W takim przypadku używany jest zestaw uprawnień strefy Internet.

    [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
    [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]

2. Utwórz obiekt <xref:System.AppDomainSetup>, aby zainicjować domenę aplikacji przy użyciu ścieżki aplikacji.

    > [!IMPORTANT]
    > Dla uproszczenia ten przykład kodu używa bieżącego folderu. Aby uruchomić kod, który rzeczywiście pochodzi z Internetu, użyj oddzielnego folderu dla niezaufanego kodu, zgodnie z opisem w artykule [jak: uruchamianie częściowo zaufanego kodu w piaskownicy](../misc/how-to-run-partially-trusted-code-in-a-sandbox.md).

    [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
    [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]

3. Utwórz domenę aplikacji, określając informacje o konfiguracji domeny aplikacji i przypisz dla wszystkich zestawów, które są wykonywane w domenie aplikacji.

    [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
    [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]

    Ostatni parametr przeciążenia metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> umożliwia określenie zestawu zestawów, które mają mieć przyznane pełne zaufanie, a nie do zestawu uprawnień domeny aplikacji. Nie trzeba określać zestawów .NET Framework używanych przez aplikację, ponieważ te zestawy znajdują się w globalnej pamięci podręcznej zestawów. Zestawy w globalnej pamięci podręcznej zestawów są zawsze w pełni zaufane. Można użyć tego parametru, aby określić zestawy o silnych nazwach, które nie znajdują się w globalnej pamięci podręcznej zestawów.

### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Dodawanie RestrictedMemberAccess do domen w trybie piaskownicy

Aplikacje hosta mogą zezwalać anonimowo hostowanym metodom dynamicznym na dostęp do prywatnych danych w zestawach, które mają poziomy zaufania równe lub mniejsze niż poziom zaufania zestawu, który emituje kod. Aby umożliwić tę ograniczoną możliwość pomijania sprawdzania widoczności just-in-Time (JIT), aplikacja hosta dodaje obiekt <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> (autoryzacji) do zestawu dotacji.

Na przykład host może udzielić dostępu do Internetu przez aplikacje internetowe i AUTORYZACJa, aby aplikacja internetowa mogła emitować kod, który uzyskuje dostęp do danych prywatnych w własnych zestawach. Ponieważ dostęp jest ograniczony do zestawów o równej lub mniejszej relacji zaufania, aplikacja internetowa nie może uzyskać dostępu do członków w pełni zaufanych zestawów, takich jak zestawy .NET Framework.

> [!NOTE]
> Aby zapobiec podwyższeniu poziomu uprawnień, informacje stosu dotyczące zestawu emitującego są uwzględniane w przypadku skonstruowania anonimowo obsługiwanych metod dynamicznych. Gdy wywoływana jest metoda, informacje stosu są sprawdzane. W rezultacie anonimowo obsługiwana metoda dynamiczna wywoływana z w pełni zaufanego kodu jest nadal ograniczona do poziomu zaufania wyemitowanego zestawu.

#### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Aby utworzyć domenę aplikacji z częściowym zaufaniem i opcją autoryzacji

1. Utwórz nowy obiekt <xref:System.Security.Permissions.ReflectionPermission> przy użyciu flagi <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (autoryzacji) i użyj metody <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType>, aby dodać uprawnienie do zestawu dotacji.

    [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
    [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]

    Metoda <xref:System.Security.PermissionSet.AddPermission%2A> dodaje uprawnienie do zestawu dotacji, jeśli nie została jeszcze uwzględniona. Jeśli uprawnienie jest już zawarte w zestawie uprawnień, określone flagi są dodawane do istniejącego uprawnienia.

    > [!NOTE]
    > Funkcja autoryzacji jest funkcją anonimowo obsługiwanych metod dynamicznych. Gdy zwykłe metody dynamiczne pomijają sprawdzanie widoczności JIT, emitowany kod wymaga pełnego zaufania.

2. Utwórz domenę aplikacji, określając informacje o konfiguracji domeny aplikacji i Przydziel zestaw.

    [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
    [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]

<a name="Running_code"></a>

## <a name="running-code-in-sandboxed-application-domains"></a>Uruchamianie kodu w domenach aplikacji w trybie piaskownicy

Poniższa procedura wyjaśnia, jak zdefiniować klasę przy użyciu metod, które mogą być wykonywane w domenie aplikacji, jak utworzyć wystąpienie klasy w domenie i jak wykonać metody.

#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>Aby zdefiniować i wykonać metodę w domenie aplikacji

1. Zdefiniuj klasę, która pochodzi od <xref:System.MarshalByRefObject>. Pozwala to na tworzenie wystąpień klasy w innych domenach aplikacji i wykonywanie wywołań metod między granicami domeny aplikacji. Klasa w tym przykładzie nosi nazwę `Worker`.

    [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
    [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]

2. Zdefiniuj metodę publiczną, która zawiera kod, który chcesz wykonać. W tym przykładzie kod emituje prostą metodę dynamiczną, tworzy delegata do wykonania metody i wywołuje delegata.

    [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
    [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]

3. W programie głównym Pobierz nazwę wyświetlaną zestawu. Ta nazwa jest używana podczas tworzenia wystąpień klasy `Worker` w domenie aplikacji w trybie piaskownicy.

    [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
    [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]

4. W programie głównym Utwórz domenę aplikacji w trybie piaskownicy, zgodnie z opisem w [pierwszej procedurze](#Setting_up) w tym instruktażu. Nie trzeba dodawać żadnych uprawnień do zestawu uprawnień `Internet`, ponieważ metoda `SimpleEmitDemo` używa tylko metod publicznych.

5. W programie głównym Utwórz wystąpienie klasy `Worker` w domenie aplikacji w trybie piaskownicy.

    [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
    [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]

    Metoda <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> tworzy obiekt w domenie aplikacji docelowej i zwraca serwer proxy, który może służyć do wywoływania właściwości i metod obiektu.

    > [!NOTE]
    > Jeśli używasz tego kodu w programie Visual Studio, musisz zmienić nazwę klasy, aby uwzględnić przestrzeń nazw. Domyślnie przestrzeń nazw jest nazwą projektu. Na przykład, jeśli projekt jest "PartialTrust", nazwa klasy musi być "PartialTrust. Worker".

6. Dodaj kod, aby wywołać metodę `SimpleEmitDemo`. Wywołanie jest organizowane między granicami domeny aplikacji, a kod jest wykonywany w domenie aplikacji w trybie piaskownicy.

    [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
    [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]

<a name="Using_methods"></a>

## <a name="using-anonymously-hosted-dynamic-methods"></a>Używanie anonimowo obsługiwanych metod dynamicznych

Anonimowo hostowane metody dynamiczne są skojarzone z przezroczystym zestawem, który jest dostarczany przez system. W związku z tym, kod, który zawiera, jest przezroczysty. Zwykłe metody dynamiczne, z drugiej strony, muszą być skojarzone z istniejącym modułem (bezpośrednio określić lub wywnioskowane ze skojarzonego typu) i przyjmować swój poziom zabezpieczeń z tego modułu.

> [!NOTE]
> Jedynym sposobem skojarzenia metody dynamicznej z zestawem, który zapewnia hosting anonimowy, jest użycie konstruktorów, które są opisane w poniższej procedurze. Nie można jawnie określić modułu w zestawie hostingu anonimowe.

Zwykłe metody dynamiczne mają dostęp do wewnętrznych elementów członkowskich modułu, do których są skojarzone, lub do prywatnych składowych typu, z którym są skojarzone. Anonimowo hostowane metody dynamiczne są odizolowane od innych kodów, ale nie mają dostępu do prywatnych danych. Jednak mają ograniczoną możliwość pomijania kontroli widoczności JIT w celu uzyskania dostępu do prywatnych danych. Ta możliwość jest ograniczona do zestawów, które mają poziomy zaufania równe lub mniejsze niż poziom zaufania zestawu, który emituje kod.

Aby zapobiec podwyższeniu poziomu uprawnień, informacje stosu dotyczące zestawu emitującego są uwzględniane w przypadku skonstruowania anonimowo obsługiwanych metod dynamicznych. Gdy wywoływana jest metoda, informacje stosu są sprawdzane. Anonimowo obsługiwana metoda dynamiczna wywoływana z w pełni zaufanego kodu jest nadal ograniczona do poziomu zaufania zestawu, który emituje go.

#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Aby użyć anonimowo obsługiwanych metod dynamicznych

- Utwórz anonimowo obsługiwaną metodę dynamiczną, używając konstruktora, który nie określa skojarzonego modułu lub typu.

  [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
  [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]

  Jeśli anonimowo obsługiwana metoda dynamiczna używa tylko typów publicznych i metod, nie wymaga ograniczonego dostępu do składowych i nie musi pomijać kontroli widoczności JIT.

  Do emisji metody dynamicznej nie są wymagane żadne specjalne uprawnienia, ale emitowany kod wymaga uprawnień wymaganych przez używane typy i metody. Na przykład, jeśli emitowany kod wywołuje metodę, która uzyskuje dostęp do pliku, wymaga <xref:System.Security.Permissions.FileIOPermission>. Jeśli poziom zaufania nie obejmuje tego uprawnienia, podczas wykonywania emitowanego kodu zostanie wygenerowany wyjątek zabezpieczeń. Kod przedstawiony tutaj emituje metodę dynamiczną, która korzysta tylko z metody <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>. W związku z tym kod może być wykonywany z częściowo zaufanych lokalizacji.

- Alternatywnie można utworzyć anonimowo obsługiwaną metodę dynamiczną z ograniczoną możliwością pomijania sprawdzania widoczności JIT przy użyciu konstruktora <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> i określając `true` parametru `restrictedSkipVisibility`.

  [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
  [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]

  Ograniczenie polega na tym, że anonimowo obsługiwana metoda dynamiczna może uzyskać dostęp do prywatnych danych tylko w zestawach z poziomami zaufania równymi lub mniejszymi niż poziom zaufania wyemitowanego zestawu. Na przykład jeśli metoda dynamiczna jest wykonywana z zaufaniem internetowym, może uzyskać dostęp do prywatnych danych w innych zestawach, które są również wykonywane z zaufaniem internetowym, ale nie mogą uzyskać dostępu do prywatnych danych zestawów .NET Framework. Zestawy .NET Framework są zainstalowane w globalnej pamięci podręcznej zestawów i są zawsze w pełni zaufane.

  Anonimowo hostowane metody dynamiczne mogą korzystać z tej ograniczonej zdolności do pomijania sprawdzania widoczności JIT tylko wtedy, gdy aplikacja hosta udzieli <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>. Żądanie dotyczące tego uprawnienia jest wykonywane, gdy wywoływana jest metoda.

  > [!NOTE]
  > Informacje stosu wywołań dla zestawu emitującego są uwzględniane podczas konstruowania metody dynamicznej. W związku z tym żądanie jest wykonywane względem uprawnień do emitowania zestawu zamiast zestawu, który wywołuje metodę. Zapobiega to wykonywaniu emitowanego kodu z podniesionymi uprawnieniami.

  [Pełny przykładowy kod](#Example) na końcu tego instruktażu ilustruje użycie i ograniczenia dostępu do ograniczonego elementu członkowskiego. Jej Klasa `Worker` obejmuje metodę, która może tworzyć anonimowo hostowane metody dynamiczne z ograniczoną możliwością lub bez ograniczenia, aby pominąć sprawdzanie widoczności, a przykład pokazuje wynik wykonania tej metody w domenach aplikacji, które mają różne zaufania poziomy.

  > [!NOTE]
  > Ograniczona możliwość pominięcia kontroli widoczności jest funkcją anonimowo obsługiwanych metod dynamicznych. Gdy zwykłe metody dynamiczne pomijają sprawdzanie widoczności JIT, muszą mieć przyznane pełne zaufanie.

<a name="Example"></a>

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład kodu demonstruje użycie flagi <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>, aby umożliwić anonimowo hostowane metody dynamiczne, aby pominąć sprawdzanie widoczności JIT, ale tylko wtedy, gdy docelowy element członkowski jest na równym lub niższym poziomie zaufania niż zestaw, który emituje kod.

W przykładzie zdefiniowano klasę `Worker`, która może być organizowana między granicami domeny aplikacji. Klasa ma dwa przeciążenia metody `AccessPrivateMethod`, które emitują i wykonują metody dynamiczne. Pierwsze Przeciążenie emituje metodę dynamiczną, która wywołuje metodę prywatną `PrivateMethod` klasy `Worker` i może emitować metodę dynamiczną z lub bez kontroli widoczności JIT. Drugie Przeciążenie emituje metodę dynamiczną, która uzyskuje dostęp do właściwości `internal` (`Friend` właściwości w Visual Basic) klasy <xref:System.String>.

W przykładzie użyto metody pomocnika do utworzenia zestawu grantu ograniczonego do uprawnień `Internet`, a następnie tworzenia domeny aplikacji przy użyciu przeciążenia metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>, aby określić, że cały kod, który jest wykonywany w domenie używa tego zestawu dotacji. Przykład tworzy wystąpienie klasy `Worker` w domenie aplikacji i wykonuje metodę `AccessPrivateMethod` dwa razy.

- Przy pierwszym uruchomieniu metody `AccessPrivateMethod` są wymuszane sprawdzanie widoczności JIT. Metoda dynamiczna kończy się niepowodzeniem, gdy jest wywoływana, ponieważ sprawdzanie widoczności JIT uniemożliwia uzyskanie dostępu do prywatnej metody.

- Przy drugim czasie wykonywania metody `AccessPrivateMethod` sprawdzanie widoczności JIT jest pomijane. Metoda dynamiczna kończy się niepowodzeniem podczas kompilowania, ponieważ zestaw `Internet` Grant nie przyznaje wystarczających uprawnień, aby pominąć sprawdzanie widoczności.

Przykład dodaje <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> do zestawu dotacji. W przykładzie zostanie utworzona druga domena, określając, że wszystkie kody wykonywane w domenie uzyskują uprawnienia w nowym zestawie dotacji. Przykład tworzy wystąpienie klasy `Worker` w nowej domenie aplikacji i wykonuje oba przeciążenia metody `AccessPrivateMethod`.

- Pierwsze Przeciążenie metody `AccessPrivateMethod` jest wykonywane, a sprawdzanie widoczności JIT jest pomijane. Metoda dynamiczna kompiluje się i wykonuje pomyślnie, ponieważ zestaw, który emituje kod, jest taki sam jak zestaw, który zawiera metodę prywatną. W związku z tym poziomy zaufania są równe. Jeśli aplikacja, która zawiera klasę `Worker` ma kilka zestawów, ten sam proces zakończy się powodzeniem dla każdego z tych zestawów, ponieważ wszyscy będą mieli na tym samym poziomie zaufania.

- Drugie Przeciążenie metody `AccessPrivateMethod` jest wykonywane, a ponowne sprawdzanie widoczności JIT jest pomijane. Tym razem metoda dynamiczna kończy się niepowodzeniem podczas kompilowania, ponieważ próbuje uzyskać dostęp do właściwości `FirstChar` `internal` klasy <xref:System.String>. Zestaw zawierający klasę <xref:System.String> jest w pełni zaufany. W związku z tym jest na wyższym poziomie zaufania niż zestaw, który emituje kod.

To porównanie pokazuje, w jaki sposób <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> włącza częściowo zaufany kod, aby pominąć sprawdzanie widoczności dla innego kodu częściowo zaufanego bez naruszania zabezpieczeń kodu zaufanego.

### <a name="code"></a>Kod

[!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
[!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

- W przypadku kompilowania tego przykładu kodu w programie Visual Studio należy zmienić nazwę klasy, aby uwzględnić przestrzeń nazw podczas przekazywania jej do metody <xref:System.AppDomain.CreateInstanceAndUnwrap%2A>. Domyślnie przestrzeń nazw jest nazwą projektu. Na przykład, jeśli projekt jest "PartialTrust", nazwa klasy musi być "PartialTrust. Worker".

## <a name="see-also"></a>Zobacz także

- [Problemy związane z zabezpieczeniami w emisji odbicia](security-issues-in-reflection-emit.md)
- [Instrukcje: uruchamianie częściowo zaufanego kodu w piaskownicy](../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
