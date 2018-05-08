---
title: Kod o przezroczystym poziomie bezpieczeństwa, poziom 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 252611f3aab138ab7344f1afe6eefb0fe2f5ea24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-transparent-code-level-1"></a>Kod o przezroczystym poziomie bezpieczeństwa, poziom 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Przezroczystość ułatwia deweloperom pisanie bezpieczniejsze bibliotek .NET Framework, które ujawniać funkcjonalność częściowo zaufany kod. Przezroczystość poziomu 1 została wprowadzona w programie .NET Framework w wersji 2.0 i głównie użyto tylko w ramach firmy Microsoft. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć [przezroczystość poziomu 2](../../../docs/framework/misc/security-transparent-code-level-2.md). Jednak przezroczystość poziomu 1 została zatrzymana, dzięki czemu można zidentyfikować starszego kodu, który musi zostać uruchomiony z wcześniejszych reguły zabezpieczeń.  
  
> [!IMPORTANT]
>  Należy określić poziom 1 przezroczystość zgodności. oznacza to, określić poziom 1 tylko dla kodu, który został opracowany przy użyciu programu .NET Framework 3.5 lub starszej korzystającego z <xref:System.Security.AllowPartiallyTrustedCallersAttribute> albo nie używa modelu przezroczystości. Na przykład użyć przezroczystość poziomu 1 dla zestawów platformy .NET Framework 2.0, które zezwala na wywołania z częściowo zaufanych wywołań (APTCA). Kod, który został utworzony dla [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], należy zawsze używać przezroczystość poziomu 2.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Model przezroczystość poziomu 1](#the_level_1_transparency_model)  
  
-   [Atrybuty przezroczystości](#transparency_attributes)  
  
-   [Przykłady przezroczystość zabezpieczeń](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>Model przezroczystość poziomu 1  
 Korzystając z przezroczystość poziomu 1, używany jest model zabezpieczeń, która oddziela kod do metody przezroczystym poziomie bezpieczeństwa, bezpieczny krytyczny dla zabezpieczeń i krytyczny dla zabezpieczeń.  
  
 Możesz oznaczyć całego urządzenia, niektóre klasy w zestawie lub niektóre metody w klasie jako przezroczysty zabezpieczeń. Kod o przezroczystym poziomie bezpieczeństwa nie podniesienia uprawnień. Ograniczenie to ma trzy konsekwencje:  
  
-   Kod o przezroczystym poziomie bezpieczeństwa nie można wykonać <xref:System.Security.Permissions.SecurityAction.Assert> akcje.  
  
-   Wszelkie żądania link, który będzie spełniony przez kod o przezroczystym poziomie bezpieczeństwa staje się pełne żądanie.  
  
-   Niebezpieczny kod (niemożliwy), który musi być wykonywany w kod o przezroczystym poziomie bezpieczeństwa powoduje, że pełne żądanie dla <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> uprawnienia zabezpieczeń.  
  
 Te zasady są wymuszane podczas wykonywania przez środowisko uruchomieniowe języka wspólnego (CLR). Kod o przezroczystym poziomie bezpieczeństwa przekazuje wszystkie wymagania zabezpieczeń kod, który wywołuje wstecz do jego obiekty wywołujące. Wymagania, które przepływać przez kod o przezroczystym poziomie bezpieczeństwa nie podniesienia uprawnień. Aplikacji niskiego zaufania wywołuje kod o przezroczystym poziomie bezpieczeństwa, powoduje, że popyt na wysokim poziomie uprawnień żądanie zostanie przepływać do kodu małej zaufania i zakończyć się niepowodzeniem. Kod o przezroczystym poziomie bezpieczeństwa nie można zatrzymać żądanie, ponieważ nie może wykonywać akcje potwierdzenia. Ten sam kod przezroczystym poziomie bezpieczeństwa wywoływana z kodu pełnego zaufania powoduje powiodło się żądanie.  
  
 Krytyczny dla zabezpieczeń jest przeciwieństwem przezroczystym poziomie bezpieczeństwa. Kod krytyczny dla zabezpieczeń wykonuje z pełnym zaufaniem i mogą wykonywać wszystkie operacje uprzywilejowane. Safe-kod krytyczny dla zabezpieczeń to przeszła inspekcji zabezpieczeń szeroką gamę, aby upewnić się, że nie zezwalała na częściowo zaufane obiekty wywołujące do użycia zasobów, które nie mają uprawnień dostępu do uprzywilejowanych kod.  
  
 Należy zastosować jawnie przezroczystość. Większość swój kod, który obsługuje do manipulowania danymi i logiki zwykle może być oznaczony jako przezroczystym poziomie bezpieczeństwa, podczas gdy mniejsza ilość kodu, który wykonuje wybierającym uprawnień jest oznaczony jako krytyczny dla zabezpieczeń lub bezpieczny krytyczny dla zabezpieczeń.  
  
> [!IMPORTANT]
>  Przezroczystość poziomu 1 jest ograniczona do zakresu zestawu; nie jest wymuszana między zestawami. Przezroczystość poziomu 1 głównie została użyta w ramach firmy Microsoft na potrzeby inspekcji zabezpieczeń. Krytyczny dla zabezpieczeń typy i składniki w zestawie poziom 1 są dostępne przez kod o przezroczystym poziomie bezpieczeństwa w innych zestawów. Należy przeprowadzić linkdemand dla pełnego zaufania w typy krytyczny dla zabezpieczeń na poziomie 1 i elementów członkowskich. Bezpieczny krytyczny dla zabezpieczeń typy i składniki musi również potwierdzić, że obiekty wywołujące uprawnień do chronionych zasobów, które są udostępniane przez typ lub element członkowski.  
  
 Dla zgodności z poprzednimi wersjami z wcześniejszymi wersjami programu .NET Framework wszystkie elementy członkowskie, które nie mają adnotacje z atrybutami przezroczystość są uważane bezpieczny krytyczny dla zabezpieczeń. Wszystkie typy, które nie mają adnotacje są uważane za przezroczysty. Brak reguł analizy statycznej do sprawdzania poprawności przezroczystość. W związku z tym konieczne może być debugowania przezroczystość błędy w czasie wykonywania.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Atrybuty przezroczystości  
 W poniższej tabeli opisano trzy atrybuty, które umożliwia dodawanie adnotacji przezroczystości kodu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Dozwolone tylko na poziomie zestawu. Określa wszystkie typy i składniki w zestawie jako przezroczysty zabezpieczeń. Zestaw nie może zawierać dowolny kod krytyczny dla zabezpieczeń.|  
|<xref:System.Security.SecurityCriticalAttribute>|Gdy jest używany na poziomie zestawu bez <xref:System.Security.SecurityCriticalAttribute.Scope%2A> właściwość identyfikuje domyślnie cały kod w zestawie jako przezroczystym poziomie bezpieczeństwa, ale wskazuje, że zestaw może zawierać kod krytyczny dla zabezpieczeń.<br /><br /> W przypadku na poziomie klasy identyfikuje klasa lub metoda jako krytyczny dla zabezpieczeń, ale nie elementy członkowskie klasy. Aby wszystkie elementy członkowskie krytyczny dla zabezpieczeń, ustaw <xref:System.Security.SecurityCriticalAttribute.Scope%2A> właściwości <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> Gdy jest używany na poziomie członka, ten atrybut dotyczy tylko ten element członkowski.<br /><br /> Klasa lub element członkowski zidentyfikowane jako krytyczny dla zabezpieczeń mogą wykonywać wybierającym uprawnień. **Ważne:** w przezroczystość poziomu 1 krytyczny dla zabezpieczeń typy i składniki są traktowane jako bezpieczny krytyczny dla zabezpieczeń podczas zostaną wywołane poza zestaw. Należy chronić krytyczny dla zabezpieczeń typy i składniki zażąda łącze pełnego zaufania, aby uniknąć nieautoryzowanego podniesienie uprawnień.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identyfikuje kod krytyczny dla zabezpieczeń, który można uzyskać, sprawdzając kod o przezroczystym poziomie bezpieczeństwa w zestawie. W przeciwnym razie kod o przezroczystym poziomie bezpieczeństwa nie można uzyskać dostępu do prywatne lub wewnętrzne elementy członkowskie krytyczny dla zabezpieczeń w tym samym zestawie. W ten sposób będzie wpływać kod krytyczny dla zabezpieczeń i umożliwiają nieoczekiwany wybierającym uprawnień. Safe-kod krytyczny dla zabezpieczeń powinny zostać poddane inspekcji zabezpieczeń rygorystyczne. **Uwaga:** bezpieczny krytyczny dla zabezpieczeń typy i składniki należy zweryfikować uprawnienia obiekty wywołujące do ustalania, czy element wywołujący ma uprawnienia dostępu do chronionych zasobów.|  
  
 <xref:System.Security.SecuritySafeCriticalAttribute> Atrybut umożliwia kod o przezroczystym poziomie bezpieczeństwa na dostęp do krytyczny dla zabezpieczeń elementów członkowskich w tym samym zestawie. Kod przezroczystym poziomie bezpieczeństwa i krytyczny dla zabezpieczeń, w tym zestawem wziąć pod uwagę podzielone na dwa zestawy. Kod o przezroczystym poziomie bezpieczeństwa, nie będzie można zobaczyć prywatne lub wewnętrzne elementy członkowskie kod krytyczny dla zabezpieczeń. Ponadto kod krytyczny dla zabezpieczeń jest zazwyczaj inspekcji dostępu do jego interfejsu publicznego. Nie można oczekiwać prywatny lub wewnętrzny stan był dostępny spoza zestawu; Czy chcesz zachować stanu samodzielnie. <xref:System.Security.SecuritySafeCriticalAttribute> Atrybutu zapewnia izolację stanu między kodu przezroczystym poziomie bezpieczeństwa i krytyczny dla zabezpieczeń, zapewniając możliwość zastępowania izolację, gdy konieczne jest. Kod o przezroczystym poziomie bezpieczeństwa nie można uzyskać dostępu prywatny lub wewnętrzny kod krytyczny dla zabezpieczeń, chyba że te elementy członkowskie zostały oznaczone <xref:System.Security.SecuritySafeCriticalAttribute>. Przed zastosowaniem <xref:System.Security.SecuritySafeCriticalAttribute>, inspekcji ten element członkowski, jak gdyby zostały publicznie udostępnione.  
  
### <a name="assembly-wide-annotation"></a>Adnotacja całego zestawu  
 W poniższej tabeli opisano skutków przy użyciu atrybutów zabezpieczeń na poziomie zestawu.  
  
|Atrybut zestawu|Stan zestawu|  
|------------------------|--------------------|  
|Brak atrybutu na częściowo zaufanym zestawie|Wszystkie elementy członkowskie i typy są niewidoczne.|  
|Brak atrybutu w pełni zaufanych zestawów (w globalnej pamięci podręcznej zestawów lub zidentyfikowane jako pełne zaufanie w `AppDomain`)|Wszystkie typy są niewidoczne i wszystkie elementy członkowskie są bezpieczny krytyczny dla zabezpieczeń.|  
|`SecurityTransparent`|Wszystkie elementy członkowskie i typy są niewidoczne.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Wszystkie typy i elementy członkowskie są krytyczny dla zabezpieczeń.|  
|`SecurityCritical`|Wszystkie kodu, wartością domyślną będzie przezroczysty. Jednak poszczególne typy i składniki może mieć innych atrybutów.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Przykłady przezroczystość zabezpieczeń  
 Aby użyć reguł przezroczystości .NET Framework 2.0 (poziom 1 przezroczystości), użyj następujących adnotacji zestawu:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Jeśli ma być przezroczysty, aby wskazać, że zestaw nie zawiera żadnego kodu krytycznego i nie podniesienia uprawnień w żaden sposób całego zestawu, musisz jawnie dodać przezroczystość do zestawu z następujących atrybutów:  
  
```  
[assembly: SecurityTransparent]  
```  
  
 Jeśli chcesz mieszać krytyczne i przejrzysty kod w tym samym zestawie, Rozpocznij od oznaczenie zestawu z <xref:System.Security.SecurityCriticalAttribute> atrybutu, aby wskazać, że zestaw może zawierać kod krytyczny w następujący sposób:  
  
```  
[assembly: SecurityCritical]  
```  
  
 Jeśli chcesz wykonać akcje krytyczny dla zabezpieczeń, należy jawnie oznaczyć kod, który przeprowadzi akcji krytycznej z inną <xref:System.Security.SecurityCriticalAttribute> atrybutu, jak pokazano w poniższym przykładzie:  
  
```  
[assembly: SecurityCritical]  
Public class A  
{  
    [SecurityCritical]  
    private void Critical()  
    {  
        // critical  
    }  
  
    public int SomeProperty  
    {  
        get {/* transparent */ }  
        set {/* transparent */ }  
    }  
}  
public class B  
{      
    internal string SomeOtherProperty  
    {  
        get { /* transparent */ }  
        set { /* transparent */ }  
    }  
}  
```  
  
 Poprzedni kod jest niewidoczny, z wyjątkiem `Critical` metodę, która jawnie jest oznaczony jako krytyczny dla zabezpieczeń. Przezroczystość jest ustawieniem domyślnym, nawet w przypadku poziomu zestawu <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md)  
 [Zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md)
