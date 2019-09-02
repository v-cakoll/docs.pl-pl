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
ms.openlocfilehash: 61a436efe3e3af7ce4aa50afe242838b1cd8941e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206066"
---
# <a name="security-transparent-code-level-2"></a>Kod o przezroczystym poziomie bezpieczeństwa, poziom 2

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Poziom 2 przejrzystości został wprowadzony w .NET Framework 4. Trzy założenia tego modelu to kod przezroczysty, kod zabezpieczeń bezpieczny-krytyczny i kod krytyczny dla bezpieczeństwa.

- Kod przezroczysty, w tym kod, który jest uruchomiony jako pełne zaufanie, może wywoływać inny kod przezroczysty lub tylko kod krytyczny bezpieczeństwa. Może wykonywać tylko akcje dozwolone przez zestaw uprawnień częściowej relacji zaufania domeny (jeśli taki istnieje). Kod przezroczysty nie może wykonać następujących czynności:

  - <xref:System.Security.CodeAccessPermission.Assert%2A> Wykonanie lub podniesienie uprawnień.

  - Zawiera kod niebezpieczny lub niemożliwy do zweryfikowania.

  - Bezpośrednie Wywoływanie kodu krytycznego.

  - Wywoływanie kodu natywnego lub kodu <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> przy użyciu atrybutu.

  - Wywoływanie elementu członkowskiego, który jest <xref:System.Security.Permissions.SecurityAction.LinkDemand>chroniony przez.

  - Dziedzicz z typów krytycznych.

  Ponadto metody przezroczyste nie mogą przesłaniać krytycznych metod wirtualnych ani implementować metod interfejsu krytycznego.

- Kod bezpieczny-krytyczny jest w pełni zaufany, ale jest wywoływany przez kod przezroczysty. Ujawnia on ograniczony obszar, w którym znajduje się kod pełnego zaufania; Sprawdzanie poprawności i zabezpieczeń odbywa się w kodzie krytycznym.

- Kod krytyczny dla zabezpieczeń może wywołać dowolny kod i jest w pełni zaufany, ale nie może być wywoływany przez kod przezroczysty.

Ten temat zawiera następujące sekcje:

- [Przykłady użycia i zachowania](#examples)

- [Zastąp wzorce](#override)

- [Reguły dziedziczenia](#inheritance)

- [Dodatkowe informacje i zasady](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a>Przykłady użycia i zachowania

Aby określić reguły .NET Framework 4 (poziom 2 przezroczystości), użyj następującej adnotacji dla zestawu:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

Aby zablokować reguły .NET Framework 2,0 (poziom 1 przejrzystości), użyj następującej adnotacji:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Jeśli nie podasz adnotacji z zestawem, domyślnie używane są reguły .NET Framework 4. Jednak zalecanym najlepszym rozwiązaniem jest użycie <xref:System.Security.SecurityRulesAttribute> atrybutu zamiast wartości domyślnej.

### <a name="assembly-wide-annotation"></a>Adnotacja w całej zestawie

Następujące reguły mają zastosowanie do korzystania z atrybutów na poziomie zestawu:

- Brak atrybutów: Jeśli nie określisz żadnych atrybutów, środowisko uruchomieniowe interpretuje cały kod jako krytyczny dla zabezpieczeń, z wyjątkiem sytuacji, w których krytyczne zabezpieczenia naruszają regułę dziedziczenia (na przykład podczas zastępowania lub implementowania przezroczystej metody wirtualnej lub interfejsu). W takich przypadkach metody są bezpieczne-krytyczne. Określenie braku atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego nie określi reguł przezroczystości.

- `SecurityTransparent`: Cały kod jest przezroczysty; cały zestaw nie będzie miał żadnego uprzywilejowanego ani niebezpiecznego.

- `SecurityCritical`: Cały kod, który jest wprowadzany przez typy w tym zestawie, ma krytyczne znaczenie. cały inny kod jest przezroczysty. Ten scenariusz jest podobny do nieokreślania atrybutów; jednak środowisko uruchomieniowe języka wspólnego nie ustala automatycznie reguł przezroczystości. Na przykład jeśli zastąpisz metodę wirtualną lub abstrakcyjną lub implementuje metodę interfejsu, domyślnie ta metoda jest przezroczysta. Należy jawnie dodać adnotację do metody jako `SecurityCritical` lub `SecuritySafeCritical`; w przeciwnym razie <xref:System.TypeLoadException> zostanie wygenerowane w czasie ładowania. Ta reguła ma zastosowanie również wtedy, gdy zarówno Klasa bazowa, jak i Klasa pochodna znajdują się w tym samym zestawie.

- `AllowPartiallyTrustedCallers`(tylko poziom 2): Wszystkie wartości domyślne kodu są przezroczyste. Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.

Poniższa tabela zawiera porównanie zachowania poziomu zestawu dla poziomu 2 z poziomem 1.

|Atrybut zestawu|Poziom 2|Poziom 1|
|------------------------|-------------|-------------|
|Brak atrybutu dla częściowo zaufanego zestawu|Typy i elementy członkowskie są domyślnie przezroczyste, ale mogą mieć zabezpieczenia krytyczne lub zabezpieczenia-krytyczne.|Wszystkie typy i elementy członkowskie są przezroczyste.|
|Brak atrybutu|Określenie braku atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego nie określi reguł przezroczystości. Wszystkie typy i elementy członkowskie mają krytyczne znaczenie dla zabezpieczeń, z wyjątkiem sytuacji, w których krytyczne zabezpieczenia naruszają regułę dziedziczenia.|W pełni zaufany zestaw (w globalnej pamięci podręcznej zestawów lub zidentyfikowane jako pełne zaufanie w `AppDomain`) wszystkie typy są przezroczyste i wszystkie elementy członkowskie są bezpieczne-krytyczne.|
|`SecurityTransparent`|Wszystkie typy i elementy członkowskie są przezroczyste.|Wszystkie typy i elementy członkowskie są przezroczyste.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Nie dotyczy.|Wszystkie typy i elementy członkowskie są krytyczne dla zabezpieczeń.|
|`SecurityCritical`|Cały kod, który jest wprowadzany przez typy w tym zestawie, ma krytyczne znaczenie. cały inny kod jest przezroczysty. Jeśli zastąpisz wirtualną lub abstrakcyjną metodę lub implementuje metodę interfejsu, należy jawnie dodać adnotację do metody jako `SecurityCritical` lub `SecuritySafeCritical`.|Wszystkie wartości domyślne kodu są przezroczyste. Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.|

### <a name="type-and-member-annotation"></a>Typ i adnotacja członkowska

Atrybuty zabezpieczeń stosowane do typu mają również zastosowanie do elementów członkowskich, które są wprowadzane przez typ. Jednak nie mają zastosowania do wirtualnych lub abstrakcyjnych zastąpień klasy bazowej lub implementacji interfejsów. Następujące reguły mają zastosowanie do używania atrybutów na poziomie typu i elementu członkowskiego:

- `SecurityCritical`: Typ lub element członkowski jest krytyczny i może być wywoływany tylko przez kod pełnego zaufania. Metody wprowadzane w zabezpieczeniach typu krytycznego są krytyczne.

    > [!IMPORTANT]
    > Metody wirtualne i abstrakcyjne wprowadzone w klasach bazowych lub interfejsach, a także zastąpione lub zaimplementowane w klasie o krytycznym znaczeniu są domyślnie przezroczyste. Muszą one być zidentyfikowane jako `SecuritySafeCritical` lub. `SecurityCritical`

- `SecuritySafeCritical`: Typ lub element członkowski jest bezpieczny-krytyczny. Jednak typ lub element członkowski może być wywoływany z przezroczystego (częściowo zaufanego) kodu i jest tak jak każdy inny kod krytyczny. Kod musi być poddany inspekcji pod kątem bezpieczeństwa.

[Powrót do początku](#top)

<a name="override"></a>

## <a name="override-patterns"></a>Zastępowanie wzorów

W poniższej tabeli przedstawiono metody przesłaniania dozwolone dla przezroczystości poziomu 2.

|Podstawowy element członkowski wirtualnego/interfejsu|Zastąpienie/interfejs|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

[Powrót do początku](#top)

<a name="inheritance"></a>

## <a name="inheritance-rules"></a>Zasady dziedziczenia

W tej sekcji następująca kolejność jest przypisana do `Transparent`, `Critical`i `SafeCritical` kodu na podstawie dostępu i możliwości:

`Transparent` < `SafeCritical` < `Critical`

- Reguły dla typów: Przechodzenie od lewej do prawej powoduje bardziej restrykcyjne dostęp. Typy pochodne muszą być co najmniej tak restrykcyjne jak typ podstawowy.

- Reguły dla metod: Metody pochodne nie mogą zmieniać dostępności z metody podstawowej. W przypadku zachowania domyślnego wszystkie metody pochodne, które nie są adnotacjami `Transparent`, są. Pochodne typów krytycznych powodują, że wyjątek jest zgłaszany, jeśli zastąpiona metoda nie jest jawnie oznaczona adnotacją `SecurityCritical`.

W poniższej tabeli przedstawiono wzorce dziedziczenia typów dozwolonych.

|Klasa bazowa|Klasa pochodna może być|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

W poniższej tabeli przedstawiono wzorce dziedziczenia typu niedozwolone.

|Klasa bazowa|Klasa pochodna nie może być|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

W poniższej tabeli przedstawiono dozwolone wzorce dziedziczenia metody.

|Metoda bazowa|Pochodna Metoda może być|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

W poniższej tabeli przedstawiono niedozwolone wzorce dziedziczenia metody.

|Metoda bazowa|Metoda pochodna nie może być|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Te reguły dziedziczenia mają zastosowanie do typów i elementów członkowskich poziomu 2. Typy zestawów na poziomie 1 mogą dziedziczyć z typów i elementów krytycznych zabezpieczeń poziomu 2. W związku z tym typy i elementy członkowskie poziomu 2 muszą mieć oddzielne żądania dziedziczenia dla dziedziczeń poziomu 1.

[Powrót do początku](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a>Dodatkowe informacje i zasady

### <a name="linkdemand-support"></a>Obsługa LinkDemand

Model przezroczystości poziomu 2 zastępuje <xref:System.Security.Permissions.SecurityAction.LinkDemand> <xref:System.Security.SecurityCriticalAttribute> atrybut i. W starszej wersji (poziom 1) kod <xref:System.Security.Permissions.SecurityAction.LinkDemand> jest automatycznie traktowany <xref:System.Security.Permissions.SecurityAction.Demand>jako.

### <a name="reflection"></a>Odbicie

Wywołanie krytycznej metody lub odczytanie pola krytycznego wyzwala żądanie pełnego zaufania (podobnie jak w przypadku wywołania metody prywatnej lub pola). W związku z tym kod pełnego zaufania może wywołać metodę krytyczną, natomiast kod częściowego zaufania nie może.

<xref:System.Reflection> Do przestrzeni nazw dodano następujące właściwości, aby określić, czy typ, metoda lub pole to <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> `SecurityCritical`, `SecuritySafeCritical`, lub `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>,, i <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Te właściwości umożliwiają określanie przejrzystości przy użyciu odbicia zamiast sprawdzania obecności atrybutu. Reguły przezroczystości są złożone i sprawdzanie, czy atrybut może być niewystarczający.

> [!NOTE]
> `SafeCritical` Metoda zwraca `true` dla obu <xref:System.Type.IsSecurityCritical%2A> i ,<xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> ponieważ`SafeCritical` jest rzeczywiście krytyczne (ma takie same możliwości jak kod krytyczny, ale może być wywoływana z kodu przezroczystego).

Metody dynamiczne dziedziczą przezroczystości modułów, do których są dołączone; nie dziedziczą przezroczystości typu (jeśli są dołączone do typu).

### <a name="skip-verification-in-full-trust"></a>Pomiń weryfikację w trybie całkowitego zaufania

Możesz pominąć weryfikację dla w pełni zaufanych zestawów przezroczystych przez <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> ustawienie właściwości `true` na wartość <xref:System.Security.SecurityRulesAttribute> w atrybucie:

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

Właściwość jest `false` domyślnie, więc właściwość musi być ustawiona na `true` , aby pominąć weryfikację. <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Należy to zrobić tylko w celach optymalizacji. Upewnij się, że przezroczysty kod w zestawie jest możliwy do zweryfikowania przy `transparent` użyciu opcji w [narzędziu PEVerify](../tools/peverify-exe-peverify-tool.md).

## <a name="see-also"></a>Zobacz także

- [Kod przezroczysty pod względem zabezpieczeń, poziom 1](security-transparent-code-level-1.md)
- [Zmiany zabezpieczeń](../security/security-changes.md)
