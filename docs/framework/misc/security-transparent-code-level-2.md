---
title: Kod o przezroczystym poziomie bezpieczeństwa, poziom 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 12e991e4977b0866343158c05681ddf4bd0c869b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645731"
---
# <a name="security-transparent-code-level-2"></a>Kod o przezroczystym poziomie bezpieczeństwa, poziom 2

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Przejrzystość poziomu 2 została wprowadzona w ramach .NET Framework 4. Trzy założenia tego modelu to przezroczysty kod, kod o znaczeniu krytycznym dla zabezpieczeń i kod krytyczny dla zabezpieczeń.

- Przezroczysty kod, w tym kod, który jest uruchomiony jako pełne zaufanie, można wywołać inny kod przezroczysty lub kod krytyczny dla bezpieczeństwa tylko. Może wykonywać tylko akcje dozwolone przez zestaw uprawnień częściowego zaufania domeny (jeśli istnieje). Nie można wykonać następujące czynności:

  - Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> lub podniesienie uprawnień.

  - Zawierają niebezpieczny lub niemożliwy do wyczałkować kod.

  - Bezpośrednio wywołać kod krytyczny.

  - Wywołanie kodu macierzystego <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> lub kodu z atrybutem.

  - Wywołanie członka, który jest <xref:System.Security.Permissions.SecurityAction.LinkDemand>chroniony przez .

  - Dziedzicz po typach krytycznych.

  Ponadto metody przezroczyste nie można zastąpić krytycznych metod wirtualnych lub zaimplementować krytycznych metod interfejsu.

- Bezpieczny kod krytyczny jest w pełni zaufany, ale można go wywołać za pomocą przezroczystego kodu. Udostępnia ograniczoną powierzchnię kodu pełnego zaufania; weryfikacji poprawności i bezpieczeństwa w kodzie o znaczeniu krytycznym.

- Kod krytyczny dla zabezpieczeń może wywołać dowolny kod i jest w pełni zaufany, ale nie można go wywołać za pomocą przezroczystego kodu.

## <a name="usage-examples-and-behaviors"></a>Przykłady użycia i zachowania

Aby określić reguły programu .NET Framework 4 (przezroczystość poziomu 2), należy użyć następującej adnotacji dla zestawu:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

Aby zablokować reguły programu .NET Framework 2.0 (przezroczystość poziomu 1), należy użyć następującej adnotacji:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Jeśli nie dodasz do adnotacji zestawu, reguły .NET Framework 4 są używane domyślnie. Jednak zalecaną najlepszą praktyką <xref:System.Security.SecurityRulesAttribute> jest użycie atrybutu zamiast w zależności od wartości domyślnej.

### <a name="assembly-wide-annotation"></a>Adnotacja dla całego zestawu

Następujące reguły mają zastosowanie do używania atrybutów na poziomie zestawu:

- Brak atrybutów: Jeśli nie określisz żadnych atrybutów, środowisko wykonawcze interpretuje cały kod jako krytyczny dla zabezpieczeń, z wyjątkiem sytuacji, gdy krytyczne zabezpieczenia naruszają regułę dziedziczenia (na przykład podczas zastępowania lub implementowania przezroczystej metody wirtualnej lub interfejsu). W takich przypadkach metody są bezpieczne krytyczne. Określenie żadnego atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego określa reguły przejrzystości.

- `SecurityTransparent`: Cały kod jest przezroczysty; całe zgromadzenie nie zrobi nic uprzywilejowanego lub niebezpiecznego.

- `SecurityCritical`: Cały kod, który jest wprowadzany przez typy w tym zestawie jest krytyczny; wszystkie inne kody są przezroczyste. Ten scenariusz jest podobny do nie określania żadnych atrybutów; jednak środowisko uruchomieniowe języka wspólnego nie określa automatycznie reguł przezroczystości. Na przykład jeśli zastąpić metodę wirtualną lub abstrakcyjną lub zaimplementować metodę interfejsu, domyślnie ta metoda jest przezroczysta. Należy jawnie dodawać adnotacje do metody jako `SecurityCritical` lub `SecuritySafeCritical`; w przeciwnym <xref:System.TypeLoadException> razie zostanie rzucony w czasie ładowania. Ta reguła ma również zastosowanie, gdy zarówno klasa podstawowa, jak i klasa pochodna znajdują się w tym samym zestawie.

- `AllowPartiallyTrustedCallers`(tylko poziom 2): Wszystkie domyślne ustawienia kodu mają być przezroczyste. Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.

W poniższej tabeli porównano zachowanie poziomu złożenia dla poziomu 2 z poziomem 1.

|Atrybut zestawu|Poziom 2|Poziom 1|
|------------------------|-------------|-------------|
|Brak atrybutu w częściowo zaufanym zestawie|Typy i elementy członkowskie są domyślnie przezroczyste, ale mogą być krytyczne dla zabezpieczeń lub krytyczne dla zabezpieczeń.|Wszystkie typy i elementy członkowskie są przezroczyste.|
|Brak atrybutu|Określenie żadnego atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego określa reguły przejrzystości. Wszystkie typy i elementy członkowskie są krytyczne dla zabezpieczeń, z wyjątkiem sytuacji, gdy krytyczne zabezpieczenia naruszają regułę dziedziczenia.|W pełni zaufanym zestawie (w globalnej pamięci podręcznej `AppDomain`zestawów lub zidentyfikowane jako pełne zaufanie do) wszystkie typy są przezroczyste i wszystkie elementy członkowskie są bezpieczne-krytyczne.|
|`SecurityTransparent`|Wszystkie typy i elementy członkowskie są przezroczyste.|Wszystkie typy i elementy członkowskie są przezroczyste.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Nie dotyczy.|Wszystkie typy i elementy członkowskie są krytyczne dla zabezpieczeń.|
|`SecurityCritical`|Cały kod, który jest wprowadzany przez typy w tym zestawie jest krytyczny; wszystkie inne kody są przezroczyste. W przypadku zastąpienia metody wirtualnej lub abstrakcyjnej lub zaimplementowania metody `SecurityCritical` interfejsu `SecuritySafeCritical`należy jawnie opisać metodę jako lub .|Domyślnie wszystkie ustawienia kodu są przezroczyste. Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.|

### <a name="type-and-member-annotation"></a>Typ i adnotacja członkowska

Atrybuty zabezpieczeń, które są stosowane do typu również stosuje się do elementów członkowskich, które są wprowadzane przez typ. Jednak nie mają one zastosowania do wirtualnych lub abstrakcyjnych zastąpienia implementacji klasy podstawowej lub interfejsu. Następujące reguły mają zastosowanie do używania atrybutów na poziomie typu i elementu członkowskiego:

- `SecurityCritical`: Typ lub element członkowski jest krytyczny i może być wywoływany tylko przez kod pełnego zaufania. Metody, które są wprowadzane w typie krytycznym zabezpieczeń są krytyczne.

    > [!IMPORTANT]
    > Metody wirtualne i abstrakcyjne, które są wprowadzane w klasach podstawowych lub interfejsach i zastępowane lub implementowane w klasie krytycznej zabezpieczeń są domyślnie przezroczyste. Muszą one być identyfikowane jako jeden `SecuritySafeCritical` lub `SecurityCritical`.

- `SecuritySafeCritical`: Typ lub element członkowski jest krytyczny dla bezpieczeństwa. Jednak typ lub element członkowski może być wywoływany z przezroczystego (częściowo zaufanego) kodu i jest tak samo zdolny, jak każdy inny kod krytyczny. Kod musi być poddany inspekcji pod kątem zabezpieczeń.

## <a name="override-patterns"></a>Zastępowanie wzorów

W poniższej tabeli przedstawiono zastąpienia metody dozwolone dla przezroczystości poziomu 2.

|Podstawowy element członkowski wirtualny/interfejs|Zastępowanie/interfejs|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a>Zasady dziedziczenia

W tej sekcji do programu `Transparent`przypisano `Critical`następującą kolejność i `SafeCritical` kod oparty na dostępie i możliwościach:

`Transparent` < `SafeCritical` < `Critical`

- Reguły typów: przechodząc od lewej do prawej, dostęp staje się bardziej restrykcyjny. Typy pochodne muszą być co najmniej tak restrykcyjne jak typ podstawowy.

- Reguły dla metod: Metody pochodne nie można zmienić dostępność z metody podstawowej. W przypadku zachowania domyślnego wszystkie metody pochodne, które nie są oś tym adnotacjami, są `Transparent`. Pochodne typów krytycznych powodują wyjątek, jeśli zastąpiona metoda nie jest jawnie opisywana jako `SecurityCritical`.

W poniższej tabeli przedstawiono wzorce dziedziczenia dozwolonego typu.

|Klasa podstawowa|Klasa pochodna może być|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

W poniższej tabeli przedstawiono wzorce dziedziczenia niedozwolonych typów.

|Klasa podstawowa|Klasa pochodna nie może być|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

W poniższej tabeli przedstawiono wzorce dziedziczenia dozwolonej metody.

|Metoda podstawowa|Metoda pochodna może być|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

W poniższej tabeli przedstawiono wzorce dziedziczenia niedozwolonych metod.

|Metoda podstawowa|Metoda pochodna nie może być|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Te reguły dziedziczenia mają zastosowanie do typów poziomu 2 i elementów członkowskich. Typy w zestawach poziomu 1 mogą dziedziczyć z typów i elementów członkowskich poziomu 2 o krytycznym znaczeniu dla zabezpieczeń. W związku z tym poziom 2 typów i członków musi mieć oddzielne żądania dziedziczenia dla dziedzicców poziomu 1.

## <a name="additional-information-and-rules"></a>Dodatkowe informacje i zasady

### <a name="linkdemand-support"></a>Obsługa LinkDemand

Model przezroczystości poziomu 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> zastępuje <xref:System.Security.SecurityCriticalAttribute> ten atrybut. W starszym kodzie (poziom <xref:System.Security.Permissions.SecurityAction.LinkDemand> 1) a jest <xref:System.Security.Permissions.SecurityAction.Demand>automatycznie traktowany jako .

### <a name="reflection"></a>Odbicie

Wywoływanie metody krytycznej lub odczytywanie pola krytycznego wyzwala zapotrzebowanie na pełne zaufanie (tak, jakby wywoływano metodę prywatną lub pole). W związku z tym kod pełnego zaufania można wywołać metodę krytyczną, podczas gdy kod częściowego zaufania nie może.

Następujące właściwości zostały dodane do <xref:System.Reflection> obszaru nazw, aby określić, czy `SecurityCritical` `SecuritySafeCritical`typ, `SecurityTransparent` <xref:System.Type.IsSecurityCritical%2A>metoda <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>lub <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>pole jest , , lub : , i . Użyj tych właściwości, aby określić przezroczystość za pomocą odbicia zamiast sprawdzania obecności atrybutu. Reguły przejrzystości są złożone, a sprawdzanie atrybutu może nie być wystarczające.

> [!NOTE]
> Metoda `SafeCritical` zwraca `true` dla <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>obu `SafeCritical` i , ponieważ jest rzeczywiście krytyczne (ma takie same możliwości jak kod krytyczny, ale może być wywoływana z przezroczystego kodu).

Metody dynamiczne dziedziczą przezroczystość modułów, do których są dołączone; nie dziedziczą przezroczystości typu (jeśli są dołączone do typu).

### <a name="skip-verification-in-full-trust"></a>Pomiń weryfikację w trybie całkowitego zaufania

Weryfikację w pełni zaufanych zestawów <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> przezroczystych `true` można <xref:System.Security.SecurityRulesAttribute> pominąć, ustawiając właściwość w atrybucie:

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

Właściwość <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> `false` jest domyślnie, więc właściwość `true` musi być ustawiona na pominąć weryfikacji. Należy to zrobić tylko w celach optymalizacyjnych. Należy upewnić się, że przezroczysty kod w `transparent` zestawie można zweryfikować za pomocą opcji w [narzędziu PEVerify](../tools/peverify-exe-peverify-tool.md).

## <a name="see-also"></a>Zobacz też

- [Kod przezroczysty zabezpieczeń, poziom 1](security-transparent-code-level-1.md)
- [Zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
