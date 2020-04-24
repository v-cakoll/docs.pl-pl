---
title: Kod przezroczysty zabezpieczeń, poziom 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
ms.openlocfilehash: 6f6c6ecd9ecab8c531be971a0e7896994127beb8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645748"
---
# <a name="security-transparent-code-level-1"></a>Kod przezroczysty zabezpieczeń, poziom 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Przezroczystość pomaga deweloperom pisać bezpieczniejsze biblioteki programu .NET Framework, które udostępniają funkcje częściowo zaufanemu kodowi. Przezroczystość poziomu 1 została wprowadzona w wersji .NET Framework 2.0 i była używana głównie w firmie Microsoft. Począwszy od programu .NET Framework 4, można użyć [przezroczystości poziomu 2](security-transparent-code-level-2.md). Jednak poziom 1 przezroczystość została zachowana, dzięki czemu można zidentyfikować starszy kod, który musi być uruchomiony z wcześniejszych reguł zabezpieczeń.  
  
> [!IMPORTANT]
> Należy określić przezroczystość poziomu 1 tylko dla zgodności; oznacza to, że należy określić poziom 1 tylko dla kodu, który został opracowany <xref:System.Security.AllowPartiallyTrustedCallersAttribute> za pomocą programu .NET Framework 3.5 lub wcześniejszego, który używa modelu przezroczystości lub nie używa. Na przykład należy użyć przezroczystości poziomu 1 dla zestawów .NET Framework 2.0, które zezwalają na wywołania z częściowo zaufanych wywołań (APTCA). Dla kodu, który jest opracowany dla programu .NET Framework 4, należy zawsze używać poziomu 2 przezroczystości.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Model przezroczystości poziomu 1](#the_level_1_transparency_model)  
  
- [Atrybuty przezroczystości](#transparency_attributes)  
  
- [Przykłady przejrzystości zabezpieczeń](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>
## <a name="the-level-1-transparency-model"></a>Model przezroczystości poziomu 1  
 Korzystając z przezroczystości poziomu 1, używasz modelu zabezpieczeń, który oddziela kod na metody przezroczyste dla zabezpieczeń, bezpieczne i krytyczne dla zabezpieczeń.  
  
 Można oznaczyć cały zestaw, niektóre klasy w zestawie lub niektóre metody w klasie jako przezroczyste zabezpieczeń. Kod przezroczysty dla zabezpieczeń nie może podnieść uprawnień. Ograniczenie to ma trzy konsekwencje:  
  
- Kod przezroczysty dla <xref:System.Security.Permissions.SecurityAction.Assert> zabezpieczeń nie może wykonywać akcji.  
  
- Każde żądanie łącza, które byłoby spełnione przez kod przezroczysty zabezpieczeń staje się pełne żądanie.  
  
- Każdy niebezpieczny (niemożliwy dowerfififii) kod, który musi <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> zostać wykonany w kodzie przezroczystym zabezpieczeń powoduje pełne zapotrzebowanie na uprawnienia zabezpieczeń.  
  
 Reguły te są wymuszane podczas wykonywania przez środowisko uruchomieniowe języka wspólnego (CLR). Kod przezroczysty zabezpieczeń przekazuje wszystkie wymagania dotyczące zabezpieczeń kodu, który wywołuje z powrotem do swoich wywołań. Żądania, które przepływają przez kod przezroczysty zabezpieczeń nie można podnieść uprawnienia. Jeśli aplikacja o niskim zaufaniu wywołuje kod przezroczysty zabezpieczeń i powoduje zapotrzebowanie na wysokie uprawnienia, żądanie będzie przepływać z powrotem do kodu niskiego zaufania i zakończyć się niepowodzeniem. Kod przezroczysty zabezpieczeń nie może zatrzymać popytu, ponieważ nie może wykonywać akcji potwierdzenia. Ten sam kod przezroczysty zabezpieczeń wywoływany z kodu pełnego zaufania powoduje pomyślne żądanie.  
  
 Krytyczne dla zabezpieczeń jest przeciwieństwem przezroczystych zabezpieczeń. Kod o krytycznym znaczeniu dla zabezpieczeń jest wykonywany z pełnym zaufaniem i może wykonywać wszystkie operacje uprzywilejowane. Kod krytyczny dla bezpieczeństwa to kod uprzywilejowany, który został poddany obszernemu audytowi zabezpieczeń w celu potwierdzenia, że nie zezwala częściowo zaufanym wywołującym na korzystanie z zasobów, do których nie mają uprawnień dostępu.  
  
 Przejrzystość należy zastosować jawnie. Większość kodu, który obsługuje manipulowanie danymi i logiki zazwyczaj mogą być oznaczone jako przezroczyste zabezpieczeń, natomiast mniejsza ilość kodu, który wykonuje podniesienie uprawnień jest oznaczony jako krytyczne dla zabezpieczeń lub zabezpieczeń-safe-critical.  
  
> [!IMPORTANT]
> Przezroczystość poziomu 1 jest ograniczona do zakresu złożenia; nie jest wymuszany między zestawami. Przejrzystość poziomu 1 była używana głównie w firmie Microsoft do celów inspekcji zabezpieczeń. Typy krytyczne dla zabezpieczeń i elementy członkowskie w ramach zestawu poziomu 1 są dostępne za pomocą kodu przezroczystego zabezpieczeń w innych zestawach. Ważne jest, aby wykonać żądania łącza dla pełnego zaufania do wszystkich typów i członków krytycznych dla zabezpieczeń poziomu 1. Typy i elementy członkowskie o znaczeniu krytycznym dla zabezpieczeń muszą również potwierdzić, że osoby wywołujące mają uprawnienia do chronionych zasobów, do których uzyskuje dostęp typ lub element członkowski.  
  
 W przypadku zgodności z poprzednimi wersjami programu .NET Framework wszystkie elementy członkowskie, które nie są opatrzone atrybutami przezroczystości, są uważane za krytyczne dla zabezpieczeń. Wszystkie typy, które nie są oznaczone adnotacjami są uważane za przezroczyste. Nie ma żadnych reguł analizy statycznej, aby sprawdzić przejrzystość. W związku z tym może być konieczne debugowanie błędów przezroczystości w czasie wykonywania.  
  
<a name="transparency_attributes"></a>
## <a name="transparency-attributes"></a>Atrybuty przezroczystości  
 W poniższej tabeli opisano trzy atrybuty używane do dotów kodu dla przezroczystości.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Dozwolone tylko na poziomie złożenia. Identyfikuje wszystkie typy i elementy członkowskie w zestawie jako przezroczyste zabezpieczeń. Zestaw nie może zawierać żadnego kodu krytycznego dla zabezpieczeń.|  
|<xref:System.Security.SecurityCriticalAttribute>|Gdy jest używany na <xref:System.Security.SecurityCriticalAttribute.Scope%2A> poziomie zestawu bez właściwości, identyfikuje cały kod w zestawie jako domyślnie przezroczysty zabezpieczeń, ale wskazuje, że zestaw może zawierać kod krytyczny dla zabezpieczeń.<br /><br /> Gdy jest używany na poziomie klasy, identyfikuje klasę lub metodę jako krytyczne dla zabezpieczeń, ale nie członków klasy. Aby wszystkie elementy członkowskie były krytyczne <xref:System.Security.SecurityCriticalAttribute.Scope%2A> dla <xref:System.Security.SecurityCriticalScope.Everything>bezpieczeństwa, ustaw właściwość na .<br /><br /> Gdy jest używany na poziomie elementu członkowskiego, atrybut ma zastosowanie tylko do tego elementu członkowskiego.<br /><br /> Klasa lub element członkowski zidentyfikowany jako krytyczny dla zabezpieczeń może wykonywać podniesienie uprawnień. **Ważne:**  W poziomie 1 przejrzystości, krytyczne dla zabezpieczeń typy i elementy członkowskie są traktowane jako bezpieczne krytyczne, gdy są wywoływane spoza zestawu. Należy chronić typy krytyczne dla zabezpieczeń i członków z żądaniem łącza dla pełnego zaufania, aby uniknąć nieautoryzowanego podniesienia uprawnień.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identyfikuje kod krytyczny dla zabezpieczeń, do który można uzyskać dostęp za pomocą kodu przezroczystego zabezpieczeń w zestawie. W przeciwnym razie kod przezroczysty zabezpieczeń nie może uzyskać dostępu do prywatnych lub wewnętrznych elementów członkowskich o krytycznym znaczeniu dla bezpieczeństwa w tym samym zestawie. W ten sposób wpłynie na kod krytyczny dla zabezpieczeń i możliwe nieoczekiwane podniesienie uprawnień. Kod o znaczeniu krytycznym dla bezpieczeństwa powinien zostać poddany rygorystycznemu audytowi zabezpieczeń. **Uwaga:**  Typy krytyczne dla zabezpieczeń i elementy członkowskie muszą sprawdzić poprawność uprawnień obiektów wywołujących, aby ustalić, czy obiektu wywołującego jest uprawniony do uzyskiwania dostępu do chronionych zasobów.|  
  
 Atrybut <xref:System.Security.SecuritySafeCriticalAttribute> umożliwia kod przezroczysty zabezpieczeń, aby uzyskać dostęp do elementów członkowskich o znaczeniu krytycznym dla zabezpieczeń w tym samym zestawie. Należy wziąć pod uwagę kod zabezpieczeń i krytyczne dla zabezpieczeń w zestawie, jak podzielone na dwa zestawy. Kod przezroczysty zabezpieczeń nie będzie w stanie zobaczyć prywatnych lub wewnętrznych członków kodu krytycznego dla zabezpieczeń. Ponadto kod krytyczny dla zabezpieczeń jest zazwyczaj poddana inspekcji w celu uzyskania dostępu do interfejsu publicznego. Nie można oczekiwać, że stan prywatny lub wewnętrzny będzie dostępny poza zestawem; chcesz, aby państwo było odizolowane. Atrybut <xref:System.Security.SecuritySafeCriticalAttribute> utrzymuje izolację stanu między kodem przezroczystym i krytycznym dla zabezpieczeń, zapewniając jednocześnie możliwość zastąpienia izolacji, gdy jest to konieczne. Kod przezroczysty dla zabezpieczeń nie może uzyskać dostępu do prywatnego <xref:System.Security.SecuritySafeCriticalAttribute>lub wewnętrznego kodu o krytycznym znaczeniu dla bezpieczeństwa, chyba że ci członkowie zostali oznaczeni . Przed zastosowaniem <xref:System.Security.SecuritySafeCriticalAttribute>, audyt tego członka, jakby były publicznie narażone.  
  
### <a name="assembly-wide-annotation"></a>Adnotacja dla całego zestawu  
 W poniższej tabeli opisano skutki używania atrybutów zabezpieczeń na poziomie zestawu.  
  
|Atrybut zestawu|Stan zgromadzenia|  
|------------------------|--------------------|  
|Brak atrybutu w częściowo zaufanym zestawie|Wszystkie typy i elementy członkowskie są przezroczyste.|  
|Brak atrybutu w pełni zaufanym zestawie (w globalnej pamięci `AppDomain`podręcznej zestawów lub zidentyfikowanego jako pełne zaufanie do)|Wszystkie typy są przezroczyste, a wszystkie elementy członkowskie są bezpieczne dla bezpieczeństwa.All types are transparent and all members are security-safe-critical.|  
|`SecurityTransparent`|Wszystkie typy i elementy członkowskie są przezroczyste.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Wszystkie typy i elementy członkowskie są krytyczne dla zabezpieczeń.|  
|`SecurityCritical`|Domyślnie wszystkie ustawienia kodu są przezroczyste. Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.|  
  
<a name="security_transparency_examples"></a>
## <a name="security-transparency-examples"></a>Przykłady przejrzystości zabezpieczeń  
 Aby użyć reguł przezroczystości programu .NET Framework 2.0 (przezroczystość poziomu 1), należy użyć następującej adnotacji zestawu:  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Jeśli chcesz, aby cały zestaw przezroczysty, aby wskazać, że zestaw nie zawiera żadnego kodu krytycznego i nie podnosi uprawnień w żaden sposób, można jawnie dodać przezroczystość do zestawu z następującym atrybutem:  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 Jeśli chcesz mieszać kod krytyczny i przezroczysty w tym <xref:System.Security.SecurityCriticalAttribute> samym zestawie, zacznij od oznaczenia zestawu atrybutem, aby wskazać, że zestaw może zawierać kod krytyczny, w następujący sposób:  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 Jeśli chcesz wykonać akcje o krytycznym znaczeniu dla zabezpieczeń, należy jawnie <xref:System.Security.SecurityCriticalAttribute> oznaczyć kod, który wykona akcję krytyczną z innym atrybutem, jak pokazano w poniższym przykładzie kodu:  
  
```csharp  
[assembly: SecurityCritical]  
public class A  
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
  
 Poprzedni kod jest przezroczysty, `Critical` z wyjątkiem metody, która jest jawnie oznaczona jako krytyczna dla zabezpieczeń. Przezroczystość jest ustawieniem domyślnym, <xref:System.Security.SecurityCriticalAttribute> nawet w odniesieniu do atrybutu na poziomie zestawu.  
  
## <a name="see-also"></a>Zobacz też

- [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](security-transparent-code-level-2.md)
- [Zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
