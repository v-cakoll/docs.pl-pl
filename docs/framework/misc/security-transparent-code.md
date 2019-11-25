---
title: Kod o przezroczystym poziomie bezpieczeństwa
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f90b64b5e9ab5a167333a594ace7f247b1b2b7e7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975529"
---
# <a name="security-transparent-code"></a>Kod o przezroczystym poziomie bezpieczeństwa

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Zabezpieczenia obejmują trzy aktywne elementy: piaskownicy, uprawnienia i wymuszanie. Tryb piaskownicy odnosi się do sposobu tworzenia izolowanych domen, w których jakiś kod jest traktowany jako w pełni zaufany, a inny kod jest ograniczony do uprawnień w odniesieniu do elementu. Kod aplikacji, który działa w ramach zestawu uprawnień piaskownicy, jest traktowany jako przezroczysty. oznacza to, że nie może wykonywać żadnych operacji, które mogą mieć wpływ na zabezpieczenia. Zestaw dotacji dla piaskownicy jest określany na podstawie dowodów (Klasa<xref:System.Security.Policy.Evidence>). Dowody określają, jakie konkretne uprawnienia są wymagane przez Piaskownice i jakie rodzaje piaskownicy mogą być tworzone. Wymuszanie dotyczy zezwalania na wykonywanie przezroczystego kodu tylko w ramach jego zestawu uprawnień.

> [!IMPORTANT]
> Zasada zabezpieczeń była kluczem elementu w poprzednich wersjach .NET Framework. Począwszy od .NET Framework 4, zasady zabezpieczeń są przestarzałe. Eliminowanie zasad zabezpieczeń jest niezależne od przejrzystości zabezpieczeń. Aby uzyskać informacje o efektach tej zmiany, zobacz temat [zgodność i migracja zasad zabezpieczeń dostępu kodu](code-access-security-policy-compatibility-and-migration.md).

## <a name="purpose-of-the-transparency-model"></a>Cel modelu przezroczystości

Przezroczystość jest mechanizmem wymuszania, który oddziela kod, który jest uruchamiany jako część aplikacji z kodu, który jest uruchamiany jako część infrastruktury. Przezroczystość rysuje barierę między kodem, który może wykonywać uprzywilejowane elementy (kod krytyczny), np. wywołując kod natywny, i kod, który nie może (kod przezroczysty). Kod przezroczysty może wykonywać polecenia w granicach zestawu uprawnień, który działa, ale nie może wykonywać, dziedziczyć ani zawierać kodu krytycznego.

Głównym celem wymuszenia przejrzystości jest zapewnienie prostego, skutecznego mechanizmu izolowania różnych grup kodu w oparciu o uprawnienia. W kontekście modelu piaskownicy te grupy uprawnień są w pełni zaufane (czyli nieograniczone) lub częściowo zaufane (czyli ograniczone do zestawu uprawnień przydzielonego do piaskownicy).

> [!IMPORTANT]
> Model przejrzystości transcends zabezpieczenia dostępu kodu. Przezroczystość jest wymuszana przez kompilator just-in-Time i obowiązuje niezależnie od przydzielenia zestawu dla zestawu, w tym pełnego zaufania.

Przejrzystość została wprowadzona w .NET Framework w wersji 2,0, aby uprościć model zabezpieczeń i ułatwić zapisywanie i wdrażanie bezpiecznych bibliotek i aplikacji. Kod przezroczysty jest również używany w programie Microsoft Silverlight, aby uprościć tworzenie częściowo zaufanych aplikacji.

> [!NOTE]
> Podczas tworzenia częściowo zaufanej aplikacji należy znać wymagania dotyczące uprawnień dla hostów docelowych. Można opracować aplikację korzystającą z zasobów, które nie są dozwolone przez niektóre hosty. Ta aplikacja zostanie skompilowana bez błędu, ale zakończy się niepowodzeniem po załadowaniu do hostowanego środowiska. Jeśli aplikacja została opracowana przy użyciu programu Visual Studio, można włączyć debugowanie w częściowej relacji zaufania lub z ograniczonym zestawem uprawnień ze środowiska deweloperskiego. Aby uzyskać więcej informacji, zobacz [How to: Debug The ClickOnce Application z ograniczonymi uprawnieniami](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). Funkcja obliczania uprawnień udostępniona dla aplikacji ClickOnce jest również dostępna dla dowolnej częściowo zaufanej aplikacji.

## <a name="specifying-the-transparency-level"></a>Określanie poziomu przezroczystości

Atrybut <xref:System.Security.SecurityRulesAttribute> na poziomie zestawu jawnie wybiera reguły <xref:System.Security.SecurityRuleSet>, których będzie przestrzegać zestaw. Reguły są zorganizowane w systemie, w którym wyższe poziomy oznaczają ściślejsze Wymuszanie reguł zabezpieczeń.

Poziomy są następujące:

- Poziom 2 (<xref:System.Security.SecurityRuleSet.Level2>) — reguły przezroczystości .NET Framework 4.

- Poziom 1 (<xref:System.Security.SecurityRuleSet.Level1>) — reguły przezroczystości .NET Framework 2,0.

Podstawowa różnica między dwoma poziomami przezroczystości polega na tym, że poziom 1 nie wymusza reguł przezroczystości dla wywołań spoza zestawu i jest przeznaczony tylko do zgodności.

> [!IMPORTANT]
> Należy określić przezroczystość poziomu 1 w celu zapewnienia zgodności. oznacza to, że należy określić poziom 1 tylko dla kodu, który został opracowany z .NET Framework 3,5 lub wcześniejszym, który używa atrybutu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> lub nie używa modelu przezroczystości. Na przykład użyj przejrzystości poziomu 1 dla zestawów .NET Framework 2,0, które zezwalają na wywołania od częściowo zaufanych wywołujących (APTCA). W przypadku kodu opracowanego dla .NET Framework 4 zawsze używaj przejrzystości poziomu 2.

### <a name="level-2-transparency"></a>Przezroczystość poziomu 2

Poziom 2 przejrzystości został wprowadzony w .NET Framework 4. Trzy założenia tego modelu to kod przezroczysty, kod zabezpieczeń bezpieczny-krytyczny i kod krytyczny dla bezpieczeństwa.

- Kod przezroczysty, niezależnie od uprawnień, które są przyznawane (w tym pełnego zaufania), może wywoływać tylko inny kod przezroczysty lub kod krytyczny dla bezpieczeństwa. Jeśli kod jest częściowo zaufany, może wykonać tylko akcje, które są dozwolone przez zestaw uprawnień domeny. Kod przezroczysty nie może wykonać następujących czynności:

  - Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> operacji lub podniesienia uprawnień.

  - Zawiera kod niebezpieczny lub niemożliwy do zweryfikowania.

  - Bezpośrednie Wywoływanie kodu krytycznego.

  - Wywoływanie kodu natywnego lub kodu, który ma atrybut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.

  - Wywołaj element członkowski, który jest chroniony przez <xref:System.Security.Permissions.SecurityAction.LinkDemand>.

  - Dziedzicz z typów krytycznych.

    Ponadto metody przezroczyste nie mogą przesłaniać krytycznych metod wirtualnych ani implementować metod interfejsu krytycznego.

- Kod zabezpieczeń-bezpieczny-krytyczny jest w pełni zaufany, ale jest wywoływany przez kod przezroczysty. Ujawnia on ograniczony obszar o pełnym zaufaniu. Sprawdzanie poprawności i zabezpieczeń odbywa się w kodzie krytycznym.

- Kod krytyczny dla zabezpieczeń może wywołać dowolny kod i jest w pełni zaufany, ale nie może być wywoływany przez kod przezroczysty.

### <a name="level-1-transparency"></a>Poziom 1 przezroczystości

Model przejrzystości poziomu 1 został wprowadzony w .NET Framework w wersji 2,0, aby umożliwić deweloperom zmniejszenie ilości kodu, który podlega inspekcji zabezpieczeń. Chociaż poziom 1 przejrzystości był publicznie dostępny w wersji 2,0, był głównie używany tylko w firmie Microsoft do celów inspekcji zabezpieczeń. Za poorednictwem adnotacji deweloperzy mogą zadeklarować, które typy i elementy członkowskie mogą wykonywać podniesienia zabezpieczeń i inne zaufane akcje (krytyczne dla zabezpieczeń), które nie mogą (być przezroczyste dla zabezpieczeń). Kod, który jest identyfikowany jako przezroczysty, nie wymaga wysokiego stopnia inspekcji zabezpieczeń. Przezroczystość poziomu 1 oznacza, że wymuszanie przezroczystości jest ograniczone do wewnątrz zestawu. Innymi słowy, wszelkie publiczne typy lub elementy członkowskie, które są identyfikowane jako krytyczne dla zabezpieczeń, są krytyczne dla zabezpieczeń tylko w obrębie zestawu. Jeśli chcesz wymusić zabezpieczenia dla tych typów i członków, gdy są wywoływane spoza zestawu, musisz użyć żądań linków dla pełnego zaufania. Jeśli nie, publicznie widoczne typy i elementy członkowskie o kluczowym znaczeniu zabezpieczeń są traktowane jako bezpieczny dla bezpieczeństwa i mogą być wywoływane przez częściowo zaufany kod poza zestawem.

Model przejrzystości poziomu 1 ma następujące ograniczenia:

- Krytyczne typy zabezpieczeń i członków, które są publiczne są dostępne z kodu przezroczystego pod względem bezpieczeństwa.

- Adnotacje przezroczystości są wymuszane tylko w obrębie zestawu.

- Typy i elementy o kluczowym znaczeniu zabezpieczeń muszą używać żądań linków, aby wymusić zabezpieczenia dla wywołań spoza zestawu.

- Reguły dziedziczenia nie są wymuszane.

- Istnieje potencjalny kod, który umożliwia wykonywanie szkodliwych operacji w przypadku uruchamiania w trybie pełnego zaufania.

## <a name="transparency-enforcement"></a>Egzekwowanie przejrzystości

Reguły przezroczystości nie są wymuszane, dopóki nie zostanie obliczona przezroczystość. W tym czasie <xref:System.InvalidOperationException> jest zgłaszany w przypadku naruszenia reguły przezroczystości. Czas obliczania przejrzystości zależy od wielu czynników i nie może być przewidywany. Jest on obliczany możliwie najpóźniej. W .NET Framework 4, obliczanie przejrzystości na poziomie zestawu odbywa się szybciej, niż w .NET Framework 2,0. Jedyną gwarancją jest to, że Obliczanie przejrzystości będzie odbywać się przez czas, gdy jest to konieczne. Jest to podobne do sposobu, w jaki kompilator just-in-Time (JIT) może zmienić punkt po skompilowaniu metody i wykryciu wszelkich błędów w tej metodzie. Obliczanie przezroczystości jest niewidoczne, jeśli kod nie ma błędów przezroczystości.

## <a name="see-also"></a>Zobacz także

- [Kod przezroczysty pod względem zabezpieczeń, poziom 1](security-transparent-code-level-1.md)
- [Kod przezroczysty pod względem zabezpieczeń, poziom 2](security-transparent-code-level-2.md)
