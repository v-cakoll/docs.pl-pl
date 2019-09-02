---
title: Kod przezroczysty pod względem zabezpieczeń, poziom 1
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
ms.openlocfilehash: d1c108e75c0e2da3d513669f5b8b02bada43b983
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206078"
---
# <a name="security-transparent-code-level-1"></a>Kod przezroczysty pod względem zabezpieczeń, poziom 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Przejrzystość ułatwia deweloperom pisanie bardziej bezpiecznych bibliotek .NET Framework, które uwidaczniają funkcjonalność do częściowo zaufanego kodu. Przejrzystość poziomu 1 została wprowadzona w .NET Framework w wersji 2,0 i była używana głównie tylko w firmie Microsoft. Począwszy od .NET Framework 4, można użyć przezroczystości [poziomu 2](security-transparent-code-level-2.md). Przejrzystość poziomu 1 została jednak zachowana, aby można było zidentyfikować starszy kod, który musi zostać uruchomiony przy użyciu wcześniejszych reguł zabezpieczeń.  
  
> [!IMPORTANT]
> Należy określić przezroczystość poziomu 1 w celu zapewnienia zgodności. oznacza to, że należy określić poziom 1 tylko dla kodu, który został opracowany z .NET Framework 3,5 lub wcześniejszym <xref:System.Security.AllowPartiallyTrustedCallersAttribute> , który używa lub nie używa modelu przezroczystości. Na przykład użyj przejrzystości poziomu 1 dla zestawów .NET Framework 2,0, które zezwalają na wywołania od częściowo zaufanych wywołujących (APTCA). W przypadku kodu opracowanego dla .NET Framework 4 zawsze używaj przejrzystości poziomu 2.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Model przejrzystości poziomu 1](#the_level_1_transparency_model)  
  
- [Atrybuty przezroczystości](#transparency_attributes)  
  
- [Przykłady przezroczystości zabezpieczeń](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>Model przejrzystości poziomu 1  
 W przypadku korzystania z przejrzystości poziomu 1 jest używany model zabezpieczeń, który oddziela kod do metod zabezpieczeń-przezroczystych, zabezpieczeń-bezpiecznych i krytycznych dla zabezpieczeń.  
  
 Można oznaczyć cały zestaw, niektóre klasy w zestawie lub niektóre metody klasy jako przezroczyste dla zabezpieczeń. Kod przezroczysty pod względem zabezpieczeń nie może podwyższyć poziomu uprawnień. To ograniczenie ma trzy konsekwencje:  
  
- Kod przezroczysty pod względem zabezpieczeń <xref:System.Security.Permissions.SecurityAction.Assert> nie może wykonać akcji.  
  
- Wszystkie żądania dotyczące linków, które byłyby spełnione przez kod przezroczysty dla zabezpieczeń, staną się pełnymi żądaniami.  
  
- Dowolny niebezpieczny (niemożliwy do zweryfikowania) kod, który musi zostać wykonany w nieprzezroczystym kodzie zabezpieczeń <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> , powoduje pełny popyt na uprawnienia zabezpieczeń.  
  
 Te reguły są wymuszane podczas wykonywania przez środowisko uruchomieniowe języka wspólnego (CLR). Kod przezroczysty pod względem zabezpieczeń przekazuje wszystkie wymagania dotyczące zabezpieczeń kodu, który wywołuje z powrotem do jego wywoływania. Wymaga, aby przepływ przez kod przezroczysty pod względem zabezpieczeń nie mógł podwyższyć poziomu uprawnień. Jeśli aplikacja z niskim zaufaniem wywołuje kod przezroczysty z zabezpieczeniami i powoduje żądanie wysokiego poziomu uprawnień, żądanie zostanie przekazane z powrotem do kodu niskiego zaufania i nie powiedzie się. Kod przezroczysty pod względem zabezpieczeń nie może zatrzymać żądania, ponieważ nie może wykonać akcji potwierdzeń. Ten sam kod przezroczysty pod względem zabezpieczeń, który jest wywoływany z kodu pełnego zaufania, skutkuje pomyślnym zapotrzebowaniem.  
  
 Krytyczne dla zabezpieczeń są przeciwieństwem przezroczystości zabezpieczeń. Kod krytyczny dla zabezpieczeń jest wykonywany z pełnym zaufaniem i może wykonywać wszystkie uprzywilejowane operacje. Bezpieczny-krytyczny kod jest uprzywilejowanym kodem, który został przeprowadzona przez kompleksową inspekcję zabezpieczeń, aby upewnić się, że nie zezwala częściowo zaufanym wywołującym na używanie zasobów, do których nie ma uprawnień dostępu.  
  
 Musisz jawnie zastosować przezroczystość. Większość kodu, który obsługuje manipulowanie danymi i logikę, może być zwykle oznaczona jako przezroczysty dla zabezpieczeń, podczas gdy mniejsza ilość kodu, która wykonuje podniesienie uprawnień, jest oznaczona jako krytyczna dla zabezpieczeń lub bezpieczna — zabezpieczenia krytyczne.  
  
> [!IMPORTANT]
> Przezroczystość poziomu 1 jest ograniczona do zakresu zestawu; nie jest wymuszany między zestawami. Przejrzystość poziomu 1 została głównie użyta w firmie Microsoft do celów inspekcji zabezpieczeń. Typy krytyczne pod względem zabezpieczeń i elementy członkowskie w zestawie poziomu 1 są dostępne przez kod przezroczysty dla zabezpieczeń w innych zestawach. Ważne jest, aby wykonać wymagania dotyczące linków w celu pełnego zaufania we wszystkich typach i elementach krytycznych zabezpieczeń na poziomie 1. Typy i składowe z bezpiecznymi zabezpieczeniami muszą także potwierdzić, że wywołujący mają uprawnienia do chronionych zasobów, do których dostęp jest uzyskiwany przez typ lub element członkowski.  
  
 W celu zapewnienia zgodności z poprzednimi wersjami .NET Framework wszystkie elementy członkowskie, które nie są adnotacjami z atrybutami przezroczystości są uznawane za bezpieczne-krytyczne. Wszystkie typy, które nie są adnotacjami, są uważane za przezroczyste. Brak statycznych reguł analizy do zweryfikowania przejrzystości. W związku z tym może być konieczne Debugowanie błędów przezroczystości w czasie wykonywania.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Atrybuty przezroczystości  
 W poniższej tabeli opisano trzy atrybuty, które służą do dodawania adnotacji do kodu dla przezroczystości.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Dozwolone tylko na poziomie zestawu. Identyfikuje wszystkie typy i składowe w zestawie jako przezroczyste dla zabezpieczeń. Zestaw nie może zawierać żadnego kodu krytycznego dla zabezpieczeń.|  
|<xref:System.Security.SecurityCriticalAttribute>|Gdy jest używany na poziomie zestawu bez <xref:System.Security.SecurityCriticalAttribute.Scope%2A> właściwości, program identyfikuje cały kod w zestawie jako zabezpieczenia-przezroczysty domyślnie, ale wskazuje, że zestaw może zawierać kod krytyczny dla bezpieczeństwa.<br /><br /> Gdy jest używana na poziomie klasy, identyfikuje klasę lub metodę jako krytyczny dla zabezpieczeń, ale nie elementy członkowskie klasy. Aby wszystkie elementy członkowskie miały krytyczne znaczenie dla zabezpieczeń, należy <xref:System.Security.SecurityCriticalAttribute.Scope%2A> ustawić właściwość <xref:System.Security.SecurityCriticalScope.Everything>na.<br /><br /> Gdy jest używany na poziomie elementu członkowskiego, atrybut ma zastosowanie tylko do tego elementu członkowskiego.<br /><br /> Klasa lub element członkowski identyfikowany jako krytyczny dla zabezpieczeń może wykonywać podniesienia uprawnień. **Ważne:**  Na poziomie 1 przejrzystość typy i elementy członkowskie o kluczowym znaczeniu zabezpieczeń są traktowane jako bezpieczne-krytyczne dla bezpieczeństwa, gdy są wywoływane spoza zestawu. Aby uniknąć nieautoryzowanego podniesienia uprawnień, należy chronić typy i członków o kluczowym znaczeniu zabezpieczeń z użyciem żądania linku do pełnego zaufania.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identyfikuje kod krytyczny dla zabezpieczeń, do którego można uzyskać dostęp za pomocą kodu przezroczystego dla zabezpieczeń w zestawie. W przeciwnym razie kod przezroczysty pod względem zabezpieczeń nie może uzyskać dostępu do prywatnych lub wewnętrznych składowych o kluczowym znaczeniu zabezpieczeń w tym samym zestawie. Mogłoby to mieć wpływ na kod krytyczny zabezpieczeń i spowodować nieoczekiwane podwyższenie poziomu uprawnień. Kod zabezpieczeń-bezpieczny-krytyczny powinien zostać poddany rygorystycznej inspekcji zabezpieczeń. **Uwaga:**  Typy i składowe z bezpiecznymi zabezpieczeniami muszą sprawdzać uprawnienia obiektów wywołujących w celu ustalenia, czy obiekt żądający ma uprawnienia dostępu do chronionych zasobów.|  
  
 Ten <xref:System.Security.SecuritySafeCriticalAttribute> atrybut umożliwia nieprzezroczysty kod w celu uzyskania dostępu do elementów członkowskich o znaczeniu krytycznym w tym samym zestawie. Rozważ użycie kodu o kluczowym znaczeniu zabezpieczeń i zabezpieczeń w zestawie, który jest podzielony na dwa zestawy. Kod przezroczysty pod względem zabezpieczeń nie może zobaczyć prywatnych lub wewnętrznych elementów członkowskich kodu krytycznego dla zabezpieczeń. Ponadto kod krytyczny dla zabezpieczeń jest ogólnie objęty inspekcją w celu uzyskania dostępu do jego interfejsu publicznego. Nie oczekuje się, że stan prywatny lub wewnętrzny będzie dostępny poza zestawem; należy zachować stan izolowany. Ten <xref:System.Security.SecuritySafeCriticalAttribute> atrybut utrzymuje izolację stanu między kodem nieprzezroczystym i krytycznym dla zabezpieczeń, jednocześnie zapewniając możliwość przesłonięcia izolacji, gdy jest to konieczne. Kod przezroczysty pod względem zabezpieczeń nie może uzyskać dostępu do prywatnego lub wewnętrznego kodu krytycznego zabezpieczeń, chyba <xref:System.Security.SecuritySafeCriticalAttribute>że te elementy członkowskie zostały oznaczone za pomocą. Przed zastosowaniem <xref:System.Security.SecuritySafeCriticalAttribute>, Przeprowadź inspekcję tego elementu członkowskiego tak, jakby był on ujawniony publicznie.  
  
### <a name="assembly-wide-annotation"></a>Adnotacja w całej zestawie  
 W poniższej tabeli opisano efekty używania atrybutów zabezpieczeń na poziomie zestawu.  
  
|Atrybut zestawu|Stan zestawu|  
|------------------------|--------------------|  
|Brak atrybutu dla częściowo zaufanego zestawu|Wszystkie typy i elementy członkowskie są przezroczyste.|  
|Brak atrybutu w w pełni zaufanym zestawie (w globalnej pamięci podręcznej zestawów lub zidentyfikowanym jako `AppDomain`pełne zaufanie)|Wszystkie typy są przezroczyste i wszystkie elementy członkowskie są bezpieczne-krytyczne.|  
|`SecurityTransparent`|Wszystkie typy i elementy członkowskie są przezroczyste.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Wszystkie typy i elementy członkowskie są krytyczne dla zabezpieczeń.|  
|`SecurityCritical`|Wszystkie wartości domyślne kodu są przezroczyste. Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Przykłady przezroczystości zabezpieczeń  
 Aby użyć reguł przezroczystości .NET Framework 2,0 (przezroczystość poziomu 1), użyj następującej adnotacji zestawu:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Jeśli chcesz, aby cały zestaw był przezroczysty, aby wskazać, że zestaw nie zawiera kodu krytycznego i nie Podnieś poziomu uprawnień w dowolny sposób, można jawnie dodać przezroczystość do zestawu przy użyciu następującego atrybutu:  
  
```  
[assembly: SecurityTransparent]  
```  
  
 Jeśli chcesz mieszać kod krytyczny i przezroczysty w tym samym zestawie, Zacznij od oznaczenia zestawu przy użyciu <xref:System.Security.SecurityCriticalAttribute> atrybutu, aby wskazać, że zestaw może zawierać kod krytyczny w następujący sposób:  
  
```  
[assembly: SecurityCritical]  
```  
  
 Jeśli chcesz wykonać akcje krytyczne dla zabezpieczeń, musisz jawnie oznaczyć kod, który wykona akcję krytyczną z innym <xref:System.Security.SecurityCriticalAttribute> atrybutem, jak pokazano w poniższym przykładzie kodu:  
  
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
  
 Poprzedni kod jest przezroczysty z wyjątkiem `Critical` metody, która jest jawnie oznaczona jako krytyczna dla zabezpieczeń. Przezroczystość jest ustawieniem domyślnym, nawet z atrybutem na <xref:System.Security.SecurityCriticalAttribute> poziomie zestawu.  
  
## <a name="see-also"></a>Zobacz także

- [Kod przezroczysty pod względem zabezpieczeń, poziom 2](security-transparent-code-level-2.md)
- [Zmiany zabezpieczeń](../security/security-changes.md)
