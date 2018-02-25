---
title: "Kod o przezroczystym poziomie bezpieczeństwa, poziom 2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 66d3611117c02b60bcf4b3713cd2b5bd79856add
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/24/2018
---
# <a name="security-transparent-code-level-2"></a>Kod o przezroczystym poziomie bezpieczeństwa, poziom 2
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Przezroczystość poziomu 2 została wprowadzona w systemie [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Trzy zasady tego modelu są kod o przezroczystym, bezpieczne-kod krytyczny dla zabezpieczeń i kod krytyczny dla zabezpieczeń.  
  
-   Kod o przezroczystym, wraz z kodem, który działa jako pełne zaufanie, można wywołać innych kod o przezroczystym lub tylko kodu bezpieczny krytyczny dla zabezpieczeń. Można wykonać tylko akcje dozwolone przez uprawnienia częściowej relacji zaufania domeny (jeśli istnieje). Kod o przezroczystym nie może wykonać następujące czynności:  
  
    -   Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> lub podniesienie uprawnień.  
  
    -   Zawiera kod niezabezpieczony lub niemożliwy.  
  
    -   Bezpośrednio wywoływać kod krytyczny.  
  
    -   Wywołania kodu natywnego lub kodu z <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.  
  
    -   Wywołanie elementu członkowskiego, który jest chroniony przez <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Dziedziczy z typu krytycznego.  
  
     Ponadto jawne metody nie można zastąpić krytycznych metod wirtualnych lub implementować metod interfejsu krytyczne.  
  
-   Bezpieczne krytyczne kod jest w pełni zaufany, ale jest wywołane przez kod przezroczysty. Udostępnia ona ograniczona powierzchni kodu pełnego zaufania. weryfikacji prawidłowości i zabezpieczeń się tak zdarzyć w kodzie bezpieczne krytyczne.  
  
-   Kod krytyczny dla zabezpieczeń można wywołać żadnego kodu i jest w pełni zaufany, ale nie można wywołać przez kod przezroczysty.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Przykłady użycia i zachowania](#examples)  
  
-   [Zastąpienie wzorce](#override)  
  
-   [Dziedziczenie zasad](#inheritance)  
  
-   [Dodatkowe informacje i reguł](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a>Przykłady użycia i zachowania  
 Aby określić [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] reguły (przezroczystość poziomu 2), użyj następujących adnotacji dla zestawu:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 Aby zablokować do reguł .NET Framework 2.0 (poziom 1 przezroczystości), należy użyć następujących adnotacji:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Jeśli zestaw nie dodawać adnotacje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zasady są stosowane domyślnie. Jednak zalecanym najlepszym rozwiązaniem jest użycie <xref:System.Security.SecurityRulesAttribute> atrybutu zamiast w zależności od domyślnego.  
  
### <a name="assembly-wide-annotation"></a>Adnotacja całego zestawu  
 Korzystanie z atrybutów na poziomie zestawu mają zastosowanie następujące reguły:  
  
-   Żadne atrybuty: Jeśli nie określono żadnych atrybutów, środowisko uruchomieniowe interpretuje całego kodu jako krytyczny dla zabezpieczeń, z wyjątkiem przypadków, gdy trwa krytyczny dla zabezpieczeń narusza regułę dziedziczenia (na przykład podczas implementowania przezroczysty lub zastępowania wirtualnych lub metody interfejsu ). W takich przypadkach metody są bezpieczne krytyczne. Określenie atrybutu nie powoduje, że środowisko uruchomieniowe języka wspólnego do określenia reguł przezroczystości dla Ciebie.  
  
-   `SecurityTransparent`: Wszystkie kodu jest niewidoczny; cały zestaw nie ma żadnego znaczenia uprzywilejowanych lub niebezpieczna.  
  
-   `SecurityCritical`: Kod wszystkie wprowadzone przez typy w tym zestawie jest krytyczne; inny kod jest niewidoczny. Ten scenariusz jest podobne do określania nie wszystkie atrybuty; środowisko uruchomieniowe języka wspólnego nie jednak automatycznie określić reguł przezroczystości. Na przykład jeśli zastąpić metodę wirtualne lub abstrakcyjne lub zaimplementować metodę interfejsu domyślnie, ta metoda jest niewidoczny. Należy jawnie dodawać adnotacje metodę jako `SecurityCritical` lub `SecuritySafeCritical`; w przeciwnym razie <xref:System.TypeLoadException> zostanie zgłoszony w czasie ładowania. Ta zasada ma zastosowanie również w przypadku zarówno klasy podstawowej i pochodnej klasy w tym samym zestawie.  
  
-   `AllowPartiallyTrustedCallers` (poziom 2): wszystkie kodu, wartością domyślną będzie przezroczysty. Jednak poszczególne typy i składniki może mieć innych atrybutów.  
  
 W poniższej tabeli porównano zachowanie poziomu zestawu dla poziomu 2 z poziomu 1.  
  
|Atrybut zestawu|Poziom 2|Poziom 1|  
|------------------------|-------------|-------------|  
|Brak atrybutu na częściowo zaufanym zestawie|Typy i składniki są domyślnie przezroczyste, ale może być krytyczny dla zabezpieczeń lub bezpieczny krytyczny dla zabezpieczeń.|Wszystkie elementy członkowskie i typy są niewidoczne.|  
|Brak atrybutu|Określenie atrybutu nie powoduje, że środowisko uruchomieniowe języka wspólnego do określenia reguł przezroczystości dla Ciebie. Wszystkie typy i elementy członkowskie są krytyczny dla zabezpieczeń, z wyjątkiem przypadków, gdy trwa krytyczny dla zabezpieczeń narusza regułę dziedziczenia.|W pełni zaufanych zestawów (w globalnej pamięci podręcznej zestawów lub zidentyfikowane jako pełne zaufanie w `AppDomain`) wszystkie typy są niewidoczne i wszystkie elementy członkowskie są bezpieczny krytyczny dla zabezpieczeń.|  
|`SecurityTransparent`|Wszystkie elementy członkowskie i typy są niewidoczne.|Wszystkie elementy członkowskie i typy są niewidoczne.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Nie dotyczy.|Wszystkie typy i elementy członkowskie są krytyczny dla zabezpieczeń.|  
|`SecurityCritical`|Cały kod wprowadzone przez typy w tym zestawie ma kluczowe znaczenie; inny kod jest niewidoczny. Jeśli zastąpić metodę wirtualne lub abstrakcyjne lub zaimplementować metodę interfejsu, musi jawnie dodawania adnotacji do metody jako `SecurityCritical` lub `SecuritySafeCritical`.|Wszystkie kodu, wartością domyślną będzie przezroczysty. Jednak poszczególne typy i składniki może mieć innych atrybutów.|  
  
### <a name="type-and-member-annotation"></a>Typ i adnotacja członkowska  
 Atrybuty zabezpieczeń, które są stosowane do typu również zastosowanie do elementów członkowskich, które są wprowadzane według typu. Jednak nie mają zastosowania do wirtualnego lub abstrakcyjny zastępuje podstawowej implementacji klasy lub interfejsu. Korzystanie z atrybutów na poziomie typu i element członkowski mają zastosowanie następujące reguły:  
  
-   `SecurityCritical`Typ lub element członkowski jest szczególnie ważne i może być wywoływana tylko przez kod pełnego zaufania. Metody, które zostały wprowadzone w typie krytyczny dla zabezpieczeń są krytyczne.  
  
    > [!IMPORTANT]
    >  Wirtualny i abstrakcyjny metody, które wprowadzono w klasy podstawowej lub do interfejsów i przesłonięcia lub zaimplementowania w klasie krytyczny dla zabezpieczeń są niewidoczne domyślnie. Zostaną one zidentyfikowane jako `SecuritySafeCritical` lub `SecurityCritical`.  
  
-   `SecuritySafeCritical`Typ lub element członkowski jest bezpieczne krytyczne. Jednak typu lub elementu członkowskiego może zostać wywołana z kod o przezroczystym (częściowo zaufanych) i może jako inne krytyczne kodu. Kod musi podlegać inspekcji zabezpieczeń.  
  
 [Powrót do początku](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a>Zastępowanie wzorów  
 W poniższej tabeli przedstawiono przesłonięcia metody dozwolone w przypadku przezroczystość poziomu 2.  
  
|Podstawowy wirtualny/elementu członkowskiego interfejsu|Zastąpienie/interfejsu|  
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
  
-   Reguły dla typów: przechodząc od lewej do prawej, dostępu staje się bardziej restrykcyjne. Typy pochodne musi być przynajmniej tak restrykcyjne jako typu podstawowego.  
  
-   Reguły dla metody: pochodnej metody nie można zmienić ułatwień dostępu z metody podstawowej. Domyślne zachowanie są wszystkie metody pochodne, które nie mają adnotacje `Transparent`. Pochodne typy krytyczne spowodować wyjątek zostanie wygenerowany, jeśli przeciążonej nie ma jawnie adnotacji jako `SecurityCritical`.  
  
 W poniższej tabeli przedstawiono dozwolone typu wzorce dziedziczenia.  
  
|Klasa podstawowa|Klasa pochodna może być|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 W poniższej tabeli przedstawiono typu niedozwolonych wzorców dziedziczenia.  
  
|Klasa podstawowa|Klasa pochodna nie może być|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 W poniższej tabeli przedstawiono dozwolone metody wzorce dziedziczenia.  
  
|Base — metoda|Metoda pochodna może być|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 W poniższej tabeli przedstawiono metodę niedozwolonych wzorców dziedziczenia.  
  
|Base — metoda|Metoda pochodna nie może być|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  Te reguły dziedziczenia stosuje się do poziomu 2 typów i członków. Typów w zestawach poziom 1 może dziedziczyć typy krytyczny dla zabezpieczeń poziomu 2 i elementów członkowskich. W związku z tym poziom 2 typy i składniki musi mieć osobne inheritancedemand dla dziedziczenia poziomu 1.  
  
 [Powrót do początku](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a>Dodatkowe informacje i zasady  
  
### <a name="linkdemand-support"></a>Obsługa LinkDemand  
 Zastępuje modelu przezroczystość poziomu 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> z <xref:System.Security.SecurityCriticalAttribute> atrybutu. W kodzie starszych (poziom 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> jest automatycznie traktowane jako <xref:System.Security.Permissions.SecurityAction.Demand>.  
  
### <a name="reflection"></a>Odbicie  
 Wywoływanie metody krytycznych lub odczytywania pola krytyczne wyzwala zażąda pełnego zaufania (tak, jakby były wywoływania prywatnej metody lub pola). Kod pełnego zaufania może wywołać metodę krytycznych, natomiast kod częściowego zaufania nie.  
  
 Dodano następujące właściwości <xref:System.Reflection> przestrzeni nazw, aby określić, czy typ, metoda lub pole jest `SecurityCritical`, `SecuritySafeCritical`, lub `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, i <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Użyj tych właściwości, aby określić przezroczystość przy użyciu odbicia zamiast sprawdzania pod kątem obecności atrybutu. Reguł przezroczystości są złożone i sprawdzanie dla atrybutu, nie może być wystarczające.  
  
> [!NOTE]
>  A `SafeCritical` metoda zwraca `true` dla obu <xref:System.Type.IsSecurityCritical%2A> i <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, ponieważ `SafeCritical` jest w rzeczywistości krytyczne (ma takie same możliwości jak wykonywanie kodu krytycznego, ale może ona zostać wywołana z kod o przezroczystym).  
  
 Metody dynamiczne dziedziczą przezroczystość moduły, w których są one dołączone do; nie dziedziczą przezroczystość typu (jeśli są one dołączone do typu).  
  
### <a name="skip-verification-in-full-trust"></a>Pomiń weryfikację w trybie całkowitego zaufania  
 Można pominąć weryfikacji całkowicie zaufanych zestawów przezroczysty przez ustawienie <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> właściwości `true` w <xref:System.Security.SecurityRulesAttribute> atrybutu:  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Właściwość jest `false` domyślnie, więc właściwości należy wybrać opcję `true` do pominięcia weryfikacji. Należy to zrobić tylko na potrzeby optymalizacji. Należy upewnić się, kod przezroczysty w zestawie jest możliwe do zweryfikowania przy użyciu `transparent` opcji [narzędzie PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 1](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [Zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md)
