---
title: Kod o przezroczystym poziomie bezpieczeństwa, poziom 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 36c3f139564b39555370cd5d41133f39c6b271bb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487835"
---
# <a name="security-transparent-code-level-2"></a>Kod o przezroczystym poziomie bezpieczeństwa, poziom 2

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Poziom 2 przejrzystości został wprowadzony w programie .NET Framework 4. Trzy założenia tego modelu to kod przezroczysty, kod zabezpieczenia bezpieczny krytyczny i kod zabezpieczenia krytyczny.

- Przezroczysty kod, łącznie z kodem, który działa jako pełne zaufanie, wywołując inne kodu przezroczyste lub tylko kod zabezpieczenia bezpieczny krytyczny. Można wykonać tylko akcje dozwolone przez uprawnienie częściowej relacji zaufania domeny (jeśli istnieje). Przezroczysty kod nie są możliwe następujące czynności:

  - Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> lub podniesienie uprawnień.

  - Zawiera kod niebezpieczny lub niemożliwy do zweryfikowania.

  - Bezpośrednio Wywołaj kod krytyczny.

  - Wywoływanie kodu macierzystego lub kodu za pomocą <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.

  - Wywołaj element członkowski, który jest chroniony przez <xref:System.Security.Permissions.SecurityAction.LinkDemand>.

  - Dziedziczy z typów krytycznych.

  Ponadto metody przezroczyste nie mogą zastąpić krytycznych metod wirtualnych lub implementować krytycznych metod interfejsu.

- Kod bezpieczny krytyczny jest w pełni zaufany, ale jest wywoływany przez kod przejrzysty. Udostępnia ona ograniczona obszar powierzchni pełnego zaufania kodu; Weryfikacja poprawności i zabezpieczeń dojść w kod bezpieczny krytyczny.

- Kod zabezpieczenia krytyczny może wywołać dowolny kod i jest w pełni zaufany, ale nie może być wywoływany przez kod przezroczysty.

Ten temat zawiera następujące sekcje:

- [Przykłady użycia i zachowania](#examples)

- [Zastępowanie wzorów](#override)

- [Reguły dziedziczenia](#inheritance)

- [Dodatkowe informacje i zasady](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a>Przykłady użycia i zachowania

Aby określić zasady .NET Framework 4 (poziom 2 przezroczystości), należy użyć następujących adnotacji dla zestawu:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

Aby zablokować do reguł .NET Framework 2.0 (poziom 1 przejrzystości), należy użyć następujących adnotacji:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Jeśli nie możesz dodawać adnotacje do zestawu, reguły .NET Framework 4 są używane domyślnie. Jednak zalecanym najlepszym rozwiązaniem jest użycie <xref:System.Security.SecurityRulesAttribute> atrybutu zamiast w zależności od tego, wartość domyślna.

### <a name="assembly-wide-annotation"></a>Adnotacja całego zestawu

Następujące reguły dotyczą użytkowania atrybuty na poziomie zestawu:

- Żadne atrybuty: Jeśli nie określisz żadnych atrybutów, środowisko uruchomieniowe interpretuje cały kod jako krytyczne dla zabezpieczeń, z wyjątkiem sytuacji, w którym są krytyczne dla bezpieczeństwa narusza regułę dziedziczenia (na przykład podczas implementowania przezroczyste lub zastępowania wirtualnych lub metody interfejsu). W takich przypadkach metody są bezpieczny krytyczny. Określanie bez atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego ustalić zasady przejrzystości.

- `SecurityTransparent`: Cały kod jest przezroczysty; cały zespół nie będzie ono działać uprzywilejowanych lub unsafe.

- `SecurityCritical`: Cały kod, który został wprowadzony przez typy w tym zestawie jest krytyczna; inny kod jest przezroczysty. Ten scenariusz jest podobne do określania nie wszelkie atrybuty; jednak automatycznie środowiska uruchomieniowego języka wspólnego nie określa zasady przejrzystości. Na przykład jeśli zastąpienie metody wirtualne ani abstrakcyjne lub implementuje metodę interfejsu, domyślnie tej metody jest przezroczysty. Należy jawnie dodać adnotacje metodę jako `SecurityCritical` lub `SecuritySafeCritical`; w przeciwnym razie <xref:System.TypeLoadException> zostanie wyrzucony w czasie ładowania. Ta zasada ma zastosowanie, gdy klasa bazowa i Klasa pochodna znajdują się w tym samym zestawie.

- `AllowPartiallyTrustedCallers` (tylko poziom 2): Wartość domyślna to przezroczyste wszystkie kodu. Jednak poszczególne typy i składowe mogą mieć inne atrybuty.

W poniższej tabeli porównano zachowania poziomu zestawu na poziomie 2 z poziomu 1.

|Atrybutu zestawu|Poziom 2|Poziom 1|
|------------------------|-------------|-------------|
|Brak atrybutu w częściowo zaufanym zestawie|Typy i elementy członkowskie są domyślnie przejrzysty, ale może być krytyczne dla bezpieczeństwa lub zabezpieczenia bezpieczny krytyczny.|Wszystkie typy i elementy członkowskie są niewidoczne.|
|Brak atrybutu|Określanie bez atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego ustalić zasady przejrzystości. Wszystkie typy i elementy członkowskie są krytyczne dla bezpieczeństwa, z wyjątkiem sytuacji, w którym są krytyczne dla bezpieczeństwa narusza regułę dziedziczenia.|W pełni zaufanym zestawie (w globalnej pamięci podręcznej lub zidentyfikowane jako pełne zaufanie w `AppDomain`) wszystkie typy są niewidoczne, a wszystkie elementy członkowskie są zabezpieczenia bezpieczny krytyczny.|
|`SecurityTransparent`|Wszystkie typy i elementy członkowskie są niewidoczne.|Wszystkie typy i elementy członkowskie są niewidoczne.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Nie dotyczy.|Wszystkie typy i elementy członkowskie są krytyczne dla bezpieczeństwa.|
|`SecurityCritical`|Cały kod, który został wprowadzony przez typy w tym zestawie jest krytyczna; inny kod jest przezroczysty. Jeśli zastępują metody wirtualne ani abstrakcyjne lub implementować metody interfejsu muszą jawnie dodawania adnotacji do metody jako `SecurityCritical` lub `SecuritySafeCritical`.|Wartość domyślna to przezroczyste wszystkie kodu. Jednak poszczególne typy i składowe mogą mieć inne atrybuty.|

### <a name="type-and-member-annotation"></a>Typ i adnotacja członkowska

Atrybuty zabezpieczeń, które są stosowane do typu, która jest również zastosowanie do elementów członkowskich, które są wprowadzone przez tego typu. Jednak nie mają zastosowania do programu virtual lub abstract zastępuje podstawowej implementacji klasy lub interfejsu. Następujące reguły dotyczą użytkowania atrybuty na poziomie typów i elementów członkowskich:

- `SecurityCritical`: Typ lub element członkowski ma krytyczne znaczenie i może być wywoływany tylko przez kod pełnego zaufania. Metody, które zostały wprowadzone w typie, zabezpieczenia krytyczny są niezwykle ważne.

    > [!IMPORTANT]
    > Wirtualny i abstrakcyjny metody, które są wprowadzone w klasach bazowych lub interfejsów i zastąpione lub zaimplementowaniu w klasie zabezpieczenia krytyczny są niewidoczne domyślnie. Musi być identyfikowany jako `SecuritySafeCritical` lub `SecurityCritical`.

- `SecuritySafeCritical`: Typ lub składowa jest bezpieczny krytyczny. Jednak typ lub element członkowski może zostać wywołana z przezroczystym kodzie (częściowo zaufanym) i może się tak jak każdy inny kod krytyczny. Kod musi inspekcji zabezpieczeń.

[Powrót do początku](#top)

<a name="override"></a>

## <a name="override-patterns"></a>Zastępowanie wzorów

W poniższej tabeli przedstawiono zastąpienia metody, które mogą uzyskać przezroczystość poziomu 2.

|Podstawowy wirtualnej składowej/składowej interfejsu|Zastąpienie/interfejsu|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

[Powrót do początku](#top)

<a name="inheritance"></a>

## <a name="inheritance-rules"></a>Zasady dziedziczenia

W tej sekcji następującej kolejności jest przypisany do `Transparent`, `Critical`, i `SafeCritical` kodu na podstawie dostępu i możliwości:

`Transparent` < `SafeCritical` < `Critical`

- Reguły dla typów: Przechodzenie od lewej do prawej, dostępu staje się bardziej restrykcyjne. Typy pochodne musi być co najmniej tak restrykcyjne jako typu podstawowego.

- Reguły dla metod: Metody pochodnej nie można zmienić dostępności z metody podstawowej. Domyślne zachowanie wszystkich pochodnych metody, które nie posiadają adnotację, są `Transparent`. Pochodne typy krytyczne spowodować wyjątek zostanie wygenerowany, jeśli zastąpiona metoda nie jest jawnie oznaczona jako `SecurityCritical`.

W poniższej tabeli przedstawiono dozwolone typu wzorców dziedziczenia.

|Klasa bazowa|Klasa pochodna może być|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

W poniższej tabeli przedstawiono typ niedozwolonych wzorców dziedziczenia.

|Klasa bazowa|Klasa pochodna nie może być|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

W poniższej tabeli przedstawiono dozwolone metody wzorców dziedziczenia.

|Base — metoda|Pochodna metoda może być|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

W poniższej tabeli przedstawiono metody niedozwolonych wzorców dziedziczenia.

|Base — metoda|Metoda pochodnej nie może być|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Te reguły dziedziczenia stosuje się do poziomu 2 typów i członków. Typów w zestawach poziomu 1 może dziedziczyć z poziomu 2 krytyczne dla bezpieczeństwa typy i elementy członkowskie. W związku z tym poziom 2 typy i elementy Członkowskie musi mieć osobne inheritancedemand dotyczące obiektów dziedziczących poziomu 1.

[Powrót do początku](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a>Dodatkowe informacje i zasady

### <a name="linkdemand-support"></a>Obsługa LinkDemand

Zastępuje poziomie 2 modelu przezroczystości <xref:System.Security.Permissions.SecurityAction.LinkDemand> z <xref:System.Security.SecurityCriticalAttribute> atrybutu. W kodzie starszej wersji (poziom 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> jest automatycznie traktowany jako <xref:System.Security.Permissions.SecurityAction.Demand>.

### <a name="reflection"></a>Odbicie

Wywoływanie metody krytyczne lub pola Krytyczne do czytania wyzwala żądanie, aby uzyskać pełne zaufanie (tak, jakby były wywoływanie metody prywatnej lub pola). Pełni zaufany kod, można wywołać metody krytycznej, natomiast nie częściowo zaufanemu kodowi.

Następujące właściwości zostały dodane do <xref:System.Reflection> przestrzeń nazw w celu ustalenia, czy typ, metoda lub pole jest `SecurityCritical`, `SecuritySafeCritical`, lub `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, i <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Użyj tych właściwości, aby określić przezroczystość przy użyciu odbicia zamiast sprawdzania pod kątem obecności atrybutu. Zasady przezroczystości są złożone i sprawdzanie, czy atrybut może nie być wystarczające.

> [!NOTE]
> A `SafeCritical` metoda zwraca `true` dla obu <xref:System.Type.IsSecurityCritical%2A> i <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, ponieważ `SafeCritical` bezwzględnie rzeczywiście (ma takie same możliwości jak kodu krytycznego, ale może ona zostać wywołana z przezroczystego kodu).

Metody dynamiczne dziedziczą przezroczystość moduły, w których są podłączone. nie dziedziczą przezroczystości typu (jeśli są one dołączone do typu).

### <a name="skip-verification-in-full-trust"></a>Pomiń weryfikację w trybie całkowitego zaufania

Możesz pominąć weryfikację dla całkowicie zaufanych zestawów przezroczyste, ustawiając <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> właściwości `true` w <xref:System.Security.SecurityRulesAttribute> atrybutu:

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Właściwość `false` domyślnie, więc właściwość musi być równa `true` Aby pominąć weryfikację. To powinno odbywać się wyłącznie do celów optymalizacji. Należy upewnić się, że przezroczysty kod w zestawie jest możliwe do zweryfikowania przy użyciu `transparent` opcji [narzędzie PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).

## <a name="see-also"></a>Zobacz także

- [Kod o przezroczystym poziomie bezpieczeństwa, poziom 1](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [Zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md)
