---
title: Kod o przezroczystym poziomie bezpieczeństwa
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60f2856bea79f36beb3c467158114fa78d99e09a
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456500"
---
# <a name="security-transparent-code"></a>Kod o przezroczystym poziomie bezpieczeństwa

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Zabezpieczenia obejmują trzy części interakcje: tryb piaskownicy, uprawnienia i egzekwowanie. Tryb piaskownicy odnosi się do praktyki tworzenia izolowanych domen, gdzie jakiś kod jest traktowany jako w pełni zaufany, a inny kod jest ograniczony do uprawnień w zestawie dla obszaru piaskownicy. Kod aplikacji, który jest uruchamiany w ramach zestaw uprawnień piaskownicy uważany jest za przezroczysty; oznacza to że nie może wykonywać żadnych operacji, które mogą wpłynąć na bezpieczeństwo. Zestaw przydzielony do piaskownicy został ustalony na podstawie dowodów (<xref:System.Security.Policy.Evidence> klasy). Dowód Określa, jakie konkretne uprawnienia są wymagane przez piaskownice i jakiego rodzaju piaskownice mogą być tworzone. Wymuszanie odnosi się zezwalania kodowi przezroczystości na wykonanie tylko w ramach jego zestawu uprawnień.

> [!IMPORTANT]
> Zasady zabezpieczeń były kluczowym elementem w poprzednich wersjach programu .NET Framework. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zasady zabezpieczeń są przestarzałe. Zniesienie zasady zabezpieczeń jest niezależne od przezroczystości zabezpieczeń. Aby uzyskać informacje o skutkach tej zmiany, zobacz [zgodnością zasady zabezpieczeń dostępu kodu i migracji](../../../docs/framework/misc/code-access-security-policy-compatibility-and-migration.md).

W tym temacie opisano bardziej szczegółowo model przezroczystości. Ten temat zawiera następujące sekcje:

- [Cel modelu przezroczystości](#purpose)

- [Określanie poziomu przezroczystości](#level)

- [Egzekwowanie przejrzystości](#enforcement)

<a name="purpose"></a>

## <a name="purpose-of-the-transparency-model"></a>Cel modelu przezroczystości

Przezroczystość jest mechanizmu wymuszania oddziela kod, który działa jako część aplikacji, od kodu, który działa jako część infrastruktury. Przezroczystość rysuje barierę między kodem, który umożliwia wprowadzanie zmian uprzywilejowanych (kod krytyczny), takich jak wywoływanie kodu macierzystego i kod, który nie może (kod przezroczysty). Kod o przezroczystym można wykonywać polecenia w granicach zestawu uprawnień, który działa w, ale nie można wykonać, pochodzi od lub zawierać kodu krytycznego.

Podstawowym celem egzekwowania przejrzystości jest zapewnienie prostego i skutecznego mechanizmu służącego do wyodrębniania różnych grup kodu w oparciu o uprawnienia. W kontekście modelu sandboxing te grup uprawnień są albo w pełni zaufane (czyli nie są ograniczany) lub częściowo zaufanych (czyli ograniczone do zestawu uprawnień przyznanych do piaskownicy).

> [!IMPORTANT]
> Model przezroczystości wykracza poza zabezpieczenia dostępu kodu. Przezroczystość jest wymuszana przez kompilator just-in-time i obowiązuje niezależnie od uprawnienia dla zestawu, w tym pełne zaufanie.

Przejrzystości został wprowadzony w programie .NET Framework w wersji 2.0 uprościć model zabezpieczeń oraz ułatwić pisanie i wdrażanie bezpiecznych bibliotek i aplikacji. Kod o przezroczystym służy także w programie Microsoft Silverlight, aby uprościć opracowywanie częściowo zaufanych aplikacji.

> [!NOTE]
> Podczas opracowywania aplikacji częściowo zaufanej ma pod uwagę wymagania dotyczące uprawnień dla hostów docelowych. Można opracować aplikację korzystającą z zasobów, które nie są dozwolone przez niektóre hosty. Ta aplikacja zostanie skompilowana bez błędów, ale zakończy się niepowodzeniem po załadowaniu do hostowanego środowiska. Jeśli opracowano aplikację za pomocą programu Visual Studio, można włączyć debugowanie w trybie częściowego zaufania lub w ograniczonym zestawem uprawnień ze środowiska projektowego. Aby uzyskać więcej informacji, zobacz [jak: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). Funkcja Obliczanie uprawnień zapewniana przez aplikacje ClickOnce jest również dostępna dla dowolnej częściowo zaufanej aplikacji.

[Powrót do początku](#top)

<a name="level"></a>

## <a name="specifying-the-transparency-level"></a>Określanie poziomu przezroczystości

Poziom zestawu <xref:System.Security.SecurityRulesAttribute> atrybut jawnie wybiera <xref:System.Security.SecurityRuleSet> reguł, które będą się odbywać w zestawie. Reguły są zorganizowane w systemie poziomów liczbowych, gdzie wyższe poziomy oznaczają mocniejsze egzekwowanie reguł zabezpieczeń.

Dostępne są następujące poziomy:

- Poziom 2 (<xref:System.Security.SecurityRuleSet.Level2>) — zasady przejrzystości programu .NET Framework 4.

- Poziom 1 (<xref:System.Security.SecurityRuleSet.Level1>) — zasady przejrzystości programu .NET Framework 2.0.

Główną różnicą między dwoma poziomami przezroczystości jest, że poziom 1 nie wymusza zasad przejrzystości dla wywołań z poza zestawu i jest przeznaczona tylko dla zgodności.

> [!IMPORTANT]
> Należy określić poziom 1 przejrzystości, zgodności. oznacza to, określ poziom 1 tylko dla kodu, który został opracowany z .NET Framework 3.5 lub starszym, który używa <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybut lub nie używa modelu przezroczystości. Na przykład użyć poziomu przezroczystości 1 dla zestawów .NET Framework 2.0, które umożliwiają wywołania z częściowo zaufanych obiektów wywołujących (APTCA). Kod, który został opracowany dla programu .NET Framework 4 należy zawsze używać przezroczystości poziomu 2.

### <a name="level-2-transparency"></a>Poziom 2 przezroczystości

Poziom 2 przejrzystości został wprowadzony w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Trzy założenia tego modelu to kod przezroczysty, kod zabezpieczenia bezpieczny krytyczny i kod zabezpieczenia krytyczny.

- Przezroczysty kod, niezależnie od uprawnień, których mu udzielono (w tym pełne zaufanie), można wywołać tylko inne kodu przezroczyste lub kod zabezpieczenia bezpieczny krytyczny. Jeśli kod jest częściowo zaufany, to może wykonywać tylko akcje, które są dozwolone przez zestaw uprawnień do domeny. Przezroczysty kod nie są możliwe następujące czynności:

  - Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> operacji lub podniesienie uprawnień.

  - Zawiera kod niebezpieczny lub niemożliwy do zweryfikowania.

  - Bezpośrednio Wywołaj kod krytyczny.

  - Wywołanie kodu macierzystego lub kodu, który ma <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.

  - Wywołaj element członkowski, który jest chroniony przez <xref:System.Security.Permissions.SecurityAction.LinkDemand>.

  - Dziedziczy z typów krytycznych.

    Ponadto metody przezroczyste nie mogą zastąpić krytycznych metod wirtualnych lub implementować krytycznych metod interfejsu.

- Kod zabezpieczenia bezpieczny krytyczny jest w pełni zaufany, ale jest wywoływany przez kod przejrzysty. Udostępnia ona ograniczona obszar powierzchni kodu pełnego zaufania. Weryfikacja poprawności i zabezpieczeń dojść w kod bezpieczny krytyczny.

- Kod zabezpieczenia krytyczny może wywołać dowolny kod i jest w pełni zaufany, ale nie może być wywoływany przez kod przezroczysty.

### <a name="level-1-transparency"></a>Poziom 1 przezroczystości

Model przejrzystości poziomu 1 został wprowadzony w .NET Framework w wersji 2.0, aby umożliwić deweloperom zmniejszenie ilości kodu, będącego przedmiotem inspekcji zabezpieczeń. Mimo że poziom 1 przejrzystości był publicznie dostępny w wersji 2.0, wykorzystywany był głównie tylko w firmie Microsoft na potrzeby inspekcji zabezpieczeń. Za pomocą adnotacji Deweloperzy są w stanie oświadczać, które typy i elementy Członkowskie mogą wykonywać podniesienia zabezpieczeń i inne zaufane akcje (krytyczne dla zabezpieczeń), a które nie mogą (przezroczyste dla zabezpieczeń). Kod, który jest identyfikowany jako przezroczysty nie wymaga wysokiego stopnia inspekcji zabezpieczeń. Poziom 1 przejrzystości stwierdza, że egzekwowanie przejrzystości jest ograniczone do granic zestawu. Innymi słowy wszelkie publiczne typy lub elementy członkowskie, które są identyfikowane jako krytyczne dla zabezpieczeń są krytyczne dla zabezpieczeń tylko w obrębie zestawu. Jeśli chcesz wymusić zabezpieczenia dla tych typów i elementów członkowskich, gdy zostaną wywołane spoza zestawu, należy użyć zapotrzebowania na łącza do pełnego zaufania. Jeśli tego nie zrobisz, publicznie widoczne typy zabezpieczeń krytycznych i elementy członkowskie są traktowane jak zabezpieczenia bezpieczny krytyczny i mogą być wywoływane przez częściowo zaufany kod znajdującego się poza zestawem.

Model przejrzystości poziomu 1 ma następujące ograniczenia:

- Krytyczne dla bezpieczeństwa typy i elementy członkowskie, które są publiczne są dostępne z kodu zabezpieczenia przejrzysty.

- Adnotacje przezroczystości są wymuszane tylko w zestawie.

- Członkowie i typy zabezpieczeń krytycznych muszą używać żądań konsolidacji do wymuszania zabezpieczeń dla wywołań spoza zestawu.

- Reguły dziedziczenia nie są wymuszane.

- Istnieje potencjalna możliwość przejrzysty kod będzie robił szkodliwe rzeczy po uruchomieniu w trybie pełnego zaufania.

[Powrót do początku](#top)

<a name="enforcement"></a>

## <a name="transparency-enforcement"></a>Egzekwowanie przejrzystości

Zasady przezroczystości nie są wymuszane aż do wyliczenia przezroczystości. W tym czasie <xref:System.InvalidOperationException> jest generowany, jeśli zostanie naruszona zasada przejrzystości. Czas, który przezroczystości zależy od wielu czynników i nie można przewidzieć. Jest ona obliczana jak najpóźniej. W programie .NET Framework 4 obliczenia przejrzystości na poziomie zestawu odbywa się szybciej niż w programie .NET Framework 2.0. Jedyną gwarancją jest to, że obliczenia przejrzystości nastąpi przez razem, gdy jest to konieczne. Jest to podobne do jak kompilator just-in-time (JIT) może zmienić punkt gdy metoda jest kompilowana, a wykryto jakieś błędy w tej metodzie. Obliczanie przezroczystości jest niewidoczne, jeśli kod nie ma błędów przezroczystości.

## <a name="see-also"></a>Zobacz także

- [Kod o przezroczystym poziomie bezpieczeństwa, poziom 1](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
