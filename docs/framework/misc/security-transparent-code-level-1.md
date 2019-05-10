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
ms.openlocfilehash: 01f9784cc2263c282d75251556a1f000027ca2ae
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639789"
---
# <a name="security-transparent-code-level-1"></a>Kod o przezroczystym poziomie bezpieczeństwa, poziom 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Przezroczystość ułatwia deweloperom wpisywanie bezpieczniejsze biblioteki .NET Framework, które udostępniają funkcje częściowo zaufanego kodu. Poziom 1 przejrzystości wprowadzono w programie .NET Framework w wersji 2.0 i głównie była używana tylko w ramach firmy Microsoft. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], możesz użyć [przezroczystości poziomu 2](../../../docs/framework/misc/security-transparent-code-level-2.md). Jednak poziom 1 przejrzystości została zatrzymana, dzięki czemu można zidentyfikować starszego kodu, który należy uruchomić przy użyciu starszych reguł zabezpieczeń.  
  
> [!IMPORTANT]
>  Należy określić poziom 1 przejrzystości, zgodności. oznacza to, określ poziom 1 tylko dla kodu, który został opracowany z .NET Framework 3.5 lub starszym korzystającego z <xref:System.Security.AllowPartiallyTrustedCallersAttribute> lub nie używa modelu przezroczystości. Na przykład użyć poziomu przezroczystości 1 dla zestawów .NET Framework 2.0, które umożliwiają wywołania z częściowo zaufanych obiektów wywołujących (APTCA). Dla kodu, który został opracowany dla [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zawsze używać przezroczystości poziomu 2.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Model przejrzystości poziomu 1](#the_level_1_transparency_model)  
  
- [Atrybuty przezroczystości](#transparency_attributes)  
  
- [Przykłady przezroczystości zabezpieczeń](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>Model przejrzystości poziomu 1  
 Gdy używasz poziom 1 przejrzystości, używany jest model zabezpieczeń, która oddziela kod do metody przezroczyste dla zabezpieczeń, zabezpieczenia bezpieczny krytyczny i krytyczne dla bezpieczeństwa.  
  
 Możesz oznaczyć całego zestawu, niektóre klasy w zestawie lub niektóre metody w klasie jako zabezpieczenia przejrzysty. Kod o przezroczystym poziomie bezpieczeństwa nie podniesienia uprawnień. Ograniczenie to ma trzy skutki:  
  
- Nie można wykonać kod o przezroczystym poziomie bezpieczeństwa <xref:System.Security.Permissions.SecurityAction.Assert> akcji.  
  
- Wszelkie zapotrzebowania na łącza będą spełnione przez kod o przezroczystym poziomie bezpieczeństwa staje się pełnego żądania.  
  
- Niebezpieczny kod (nieweryfikowalnego), które muszą być wykonywane w kod o przezroczystym poziomie bezpieczeństwa powoduje pełnego żądania dla <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> uprawnienia zabezpieczeń.  
  
 Te zasady są wymuszane podczas wykonywania przez środowisko uruchomieniowe języka wspólnego (CLR). Kod o przezroczystym poziomie bezpieczeństwa przekazuje wszystkie wymagania bezpieczeństwa kod, który ją wywołuje wywołujące. Żądania przepływać przez kod o przezroczystym poziomie bezpieczeństwa nie podniesienia uprawnień. Aplikacji niskiego zaufania wywołuje kod o przezroczystym poziomie bezpieczeństwa, powoduje, że zapotrzebowanie na wysokim poziomie uprawnień zapotrzebowanie przepływ niski zaufany kod i zakończyć się niepowodzeniem. Kod o przezroczystym poziomie bezpieczeństwa nie można zatrzymać żądania, ponieważ nie może wykonywać akcje potwierdzenia. Ten sam kod zabezpieczenia przejrzysty wywoływane z wyników pełni zaufany kod w pomyślnym żądanie.  
  
 Zabezpieczenia krytyczny jest przeciwieństwem zabezpieczenia przejrzysty. Kod zabezpieczenia krytyczny wykonuje z pełnym zaufaniem i mogą wykonywać wszystkie operacje uprzywilejowane. Kod zabezpieczenia bezpieczny krytyczny jest uprzywilejowanych kod, który znajduje się za pomocą inspekcji zabezpieczeń rozbudowane, aby upewnić się, że nie zezwala na częściowo zaufanych wywołań korzystać z zasobów, które nie mają uprawnień dostępu do.  
  
 Masz jawne stosowanie przezroczystości. Większość swój kod, który obsługuje do manipulowania danymi i logiki zazwyczaj może być oznaczona jako przezroczystym poziomie bezpieczeństwa, natomiast mniejsza ilość kodu, który wykonuje podniesienia uprawnień jest oznaczone jako krytyczne dla bezpieczeństwa lub zabezpieczenia bezpieczny krytyczny.  
  
> [!IMPORTANT]
>  Poziom 1 przejrzystości jest ograniczone do zakresu zestawu; nie są wymuszane między zestawami. Poziom 1 przejrzystości był używany przede wszystkim w firmie Microsoft, do celów inspekcji zabezpieczeń. Krytyczne dla bezpieczeństwa typy i elementy członkowskie w zestawie poziom 1 jest możliwy przez kod o przezroczystym poziomie bezpieczeństwa w innych zestawach. Jest ważne, wykonywania zapotrzebowania na łącza pełnego zaufania do poziomu 1 krytyczne dla bezpieczeństwa typy i członków. Zabezpieczenia bezpieczny krytyczny typy i elementy członkowskie muszą również upewnij się, że obiekty wywołujące mają uprawnienia do chronionych zasobów, które są dostępne dla typu lub elementu członkowskiego.  
  
 Dla zgodności z poprzednimi wersjami z wcześniejszymi wersjami programu .NET Framework wszystkie elementy członkowskie, które nie posiadają adnotację, za pomocą atrybuty przezroczystości są uznawane za zabezpieczenia bezpieczny krytyczny. Wszystkie typy, które nie posiadają adnotację, są traktowane jako przezroczysty. Brak reguł analizy statycznej do sprawdzania poprawności przezroczystości. Dlatego może być konieczne Debugowanie błędów przezroczystości w czasie wykonywania.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Atrybuty przezroczystości  
 W poniższej tabeli opisano trzy atrybuty, które umożliwiają dodawanie adnotacji do kodu przezroczystości.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Dozwolone tylko na poziomie zestawu. Określa wszystkie typy i elementy członkowskie w zestawie jako zabezpieczenia przejrzysty. Zestawu nie może zawierać dowolny kod zabezpieczenia krytyczny.|  
|<xref:System.Security.SecurityCriticalAttribute>|Gdy jest używana na poziomie zestawu bez <xref:System.Security.SecurityCriticalAttribute.Scope%2A> właściwość identyfikuje cały kod w zestawie jako przezroczyste dla zabezpieczeń domyślnie, ale wskazuje, że zestaw może zawierać kod zabezpieczenia krytyczny.<br /><br /> W przypadku użycia tej opcji na poziomie klasy, identyfikuje klasy lub metody jako krytyczne dla bezpieczeństwa, ale nie składowych klasy. Aby wszystkie elementy członkowskie krytyczne dla bezpieczeństwa, ustaw <xref:System.Security.SecurityCriticalAttribute.Scope%2A> właściwość <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> W przypadku użycia tej opcji na poziomie członka, ten atrybut dotyczy tylko tego członka.<br /><br /> Klasa lub członek identyfikowane jako krytyczne dla zabezpieczeń mogą wykonywać podniesienia uprawnień. **Ważne:**  Przezroczystości poziomu 1 krytyczne dla bezpieczeństwa typy i elementy członkowskie są traktowane jak zabezpieczenia bezpieczny krytyczny, gdy zostaną wywołane spoza zestawu. Należy chronić krytyczne dla bezpieczeństwa typy i elementy członkowskie z zapotrzebowania na łącza, aby uzyskać pełne zaufanie w celu uniknięcia nieautoryzowanych podniesienie uprawnień.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Określa kod zabezpieczenia krytyczny, który może zostać oceniony przez kod o przezroczystym poziomie bezpieczeństwa w zestawie. W przeciwnym razie kod o przezroczystym poziomie bezpieczeństwa nie można uzyskać dostępu prywatne lub wewnętrzne elementy członkowskie krytyczne dla zabezpieczeń z tego samego zestawu. Ten sposób wpłynąć na kod zabezpieczenia krytyczny i nieoczekiwany podniesienia uprawnień, umożliwiają. Kod zabezpieczenia bezpieczny krytyczny powinny zostać poddane inspekcji rygorystyczne. **Uwaga:**  Zabezpieczenia bezpieczny krytyczny typów i elementów członkowskich należy zweryfikować uprawnienia obiekty wywołujące do określenia, czy obiekt wywołujący ma uprawnienia dostępu do chronionych zasobów.|  
  
 <xref:System.Security.SecuritySafeCriticalAttribute> Atrybut umożliwia dostęp do krytycznych dla zabezpieczeń elementów członkowskich z tego samego zestawu kod zabezpieczenia przejrzysty. Jak podzielić na dwa zestawy, należy wziąć pod uwagę przezroczyste dla zabezpieczeń i krytyczne dla bezpieczeństwa kod w swoim zestawie. Kod o przezroczystym poziomie bezpieczeństwa, nie będzie można zobaczyć prywatne lub wewnętrzne elementy członkowskie kod zabezpieczenia krytyczny. Ponadto kod zabezpieczenia krytyczny ogólnie podlega inspekcji dostępu do jego interfejsu publicznego. Nie można oczekiwać stanie prywatne lub wewnętrzne dostępne spoza zestawu; Czy chcesz zachować stan samodzielnie. <xref:System.Security.SecuritySafeCriticalAttribute> Atrybut utrzymuje izolację stanu między kodem przezroczyste dla zabezpieczeń i krytyczne dla bezpieczeństwa, zapewniając możliwość przesłaniania izolację, gdy jest to konieczne. Kod o przezroczystym poziomie bezpieczeństwa nie można uzyskać dostępu prywatny lub wewnętrzny kod zabezpieczenia krytyczny, chyba że te elementy członkowskie zostały oznaczone <xref:System.Security.SecuritySafeCriticalAttribute>. Przed zastosowaniem <xref:System.Security.SecuritySafeCriticalAttribute>, inspekcji ten element członkowski, tak, jakby były publicznie widoczne.  
  
### <a name="assembly-wide-annotation"></a>Adnotacja całego zestawu  
 W poniższej tabeli opisano efektów atrybutów zabezpieczeń na poziomie zestawu.  
  
|Atrybutu zestawu|Stan zestawu|  
|------------------------|--------------------|  
|Brak atrybutu w częściowo zaufanym zestawie|Wszystkie typy i elementy członkowskie są niewidoczne.|  
|Nie atrybutu w zestawie całkowicie zaufanym (w globalnej pamięci podręcznej lub zidentyfikowane jako pełne zaufanie w `AppDomain`)|Wszystkie typy są niewidoczne, a wszystkie elementy członkowskie są zabezpieczenia bezpieczny krytyczny.|  
|`SecurityTransparent`|Wszystkie typy i elementy członkowskie są niewidoczne.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Wszystkie typy i elementy członkowskie są krytyczne dla bezpieczeństwa.|  
|`SecurityCritical`|Wartość domyślna to przezroczyste wszystkie kodu. Jednak poszczególne typy i składowe mogą mieć inne atrybuty.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Przykłady przezroczystości zabezpieczeń  
 Aby użyć zasady przejrzystości programu .NET Framework 2.0 (poziom 1 przejrzystości), należy użyć następujących adnotacji zestawu:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Chcąc przezroczystego wskazywać, że zestaw nie zawiera żadnego kodu krytycznego i nie podniesienia uprawnień w jakikolwiek sposób całego zestawu, należy jawnie dodać przezroczystości do zestawu za pomocą następującego atrybutu:  
  
```  
[assembly: SecurityTransparent]  
```  
  
 Jeśli użytkownik chce mieszać krytycznych i przejrzysty kod z tego samego zestawu, Rozpocznij od oznaczenia zestawu z <xref:System.Security.SecurityCriticalAttribute> atrybutu, aby wskazać, że zestaw może zawierać kodu krytycznego w następujący sposób:  
  
```  
[assembly: SecurityCritical]  
```  
  
 Jeśli chcesz wykonywać działania krytyczne dla bezpieczeństwa kod, który będzie wykonywać krytyczne akcji z inną musi wyraźnie oznaczyć <xref:System.Security.SecurityCriticalAttribute> atrybutu, jak pokazano w poniższym przykładzie kodu:  
  
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
  
 Powyższy kod jest przezroczysty z wyjątkiem `Critical` metody, która jest jawnie oznaczone jako krytyczne dla bezpieczeństwa. Przezroczystość jest ustawienie domyślne, nawet w przypadku poziomu zestawu <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
## <a name="see-also"></a>Zobacz także

- [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
- [Zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md)
