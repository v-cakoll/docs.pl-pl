---
title: Problemy związane z zabezpieczeniami w emisji odbicia
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- emitting dynamic assemblies, security
- reflection emit, security
- reflection emit, partial trust scenarios
- partial trust,emitting dynamic methods
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- dynamic assemblies, security
ms.assetid: 0f8bf8fa-b993-478f-87ab-1a1a7976d298
ms.openlocfilehash: 11eb4c9bc4ba1b1fe9051a04d12f893e693fb175
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180461"
---
# <a name="security-issues-in-reflection-emit"></a>Problemy związane z zabezpieczeniami w emisji odbicia
Program .NET Framework udostępnia trzy sposoby emitowania języka pośredniego firmy Microsoft (MSIL), z których każdy ma własne problemy z zabezpieczeniami:  
  
- [Zespoły dynamiczne](#Dynamic_Assemblies)  
  
- [Anonimowo hostowane metody dynamiczne](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Metody dynamiczne skojarzone z istniejącymi złożeniami](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Niezależnie od sposobu generowania kodu dynamicznego, wykonywanie wygenerowanego kodu wymaga wszystkich uprawnień, które są wymagane przez typy i metody generowane kodu używa.  
  
> [!NOTE]
> Uprawnienia, które są wymagane do odzwierciedlenia kodu i emitowania kodu uległy zmianie wraz z wersjami programu .NET Framework. Zobacz [informacje o wersji](#Version_Information), w dalszej części tego tematu.  
  
<a name="Dynamic_Assemblies"></a>
## <a name="dynamic-assemblies"></a>Zespoły dynamiczne  
 Zestawy dynamiczne są tworzone przy użyciu <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> przeciążenia metody. Większość przeciążeń tej metody są przestarzałe w .NET Framework 4, ze względu na eliminację zasad zabezpieczeń dla całego komputera. (Zobacz [Zmiany zabezpieczeń](../security/security-changes.md).) Pozostałe przeciążenia mogą być wykonywane przez dowolny kod, niezależnie od poziomu zaufania. Te przeciążenia dzielą się na dwie grupy: te, które określają listę atrybutów, które mają być stosowane do zestawu dynamicznego podczas jego tworzenia, oraz te, które nie są tworzone. Jeśli nie określisz modelu przezroczystości dla złożenia, <xref:System.Security.SecurityRulesAttribute> stosując atrybut podczas jego tworzenia, model przezroczystości jest dziedziczony z zestawu emitującego.  
  
> [!NOTE]
> Atrybuty, które można zastosować do zestawu dynamicznego <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> po jego utworzeniu, przy użyciu metody, nie są skuteczne, dopóki zestaw został zapisany na dysku i załadowany do pamięci ponownie.  
  
 Kod w zestawie dynamicznym może uzyskać dostęp do widocznych typów i elementów członkowskich w innych zestawach.  
  
> [!NOTE]
> Zestawy dynamiczne nie <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> używają <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i flagi, które umożliwiają metody dynamiczne dostęp do typów niepublicznych i elementów członkowskich.  
  
 Zestawy przejściowe dynamiczne są tworzone w pamięci i nigdy nie zapisywane na dysku, więc nie wymagają uprawnień dostępu do plików. Zapisywanie zestawu dynamicznego <xref:System.Security.Permissions.FileIOPermission> na dysku wymaga odpowiednich flag.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Generowanie zestawów dynamicznych z częściowo zaufanego kodu  
 Należy wziąć pod uwagę warunki, w których zestaw z uprawnieniami do Internetu może generować przejściowy zestaw dynamiczny i wykonać jego kod:  
  
- Zestaw dynamiczny używa tylko typów publicznych i elementów członkowskich innych zestawów.  
  
- Uprawnienia wymagane przez te typy i elementy członkowskie są uwzględniane w zestawie dotacji częściowo zaufanego zestawu.  
  
- Zestaw nie jest zapisywany na dysku.  
  
- Symbole debugowania nie są generowane. (`Internet` `LocalIntranet` i zestawy uprawnień nie zawierają niezbędnych uprawnień.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>
## <a name="anonymously-hosted-dynamic-methods"></a>Anonimowo hostowane metody dynamiczne  
 Anonimowo hostowane metody dynamiczne są <xref:System.Reflection.Emit.DynamicMethod> tworzone przy użyciu dwóch konstruktorów, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>które nie określają skojarzonego typu lub modułu oraz <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> . Konstruktory te umieszczają metody dynamiczne w zestawie zapewnianym przez system, w pełni zaufanym, przezroczystym dla zabezpieczeń. Żadne uprawnienia nie są wymagane do korzystania z tych konstruktorów lub emitować kod dla metod dynamicznych.  
  
 Zamiast tego po utworzeniu anonimowo hostowane metody dynamicznej, stos wywołań jest przechwytywany. Gdy metoda jest skonstruowana, wymagania zabezpieczeń są dokonywane względem stosu przechwyconych wywołań.  
  
> [!NOTE]
> Koncepcyjnie, wymagania są dokonywane podczas budowy metody. Oznacza to, że żądania mogą być dokonywane, jak każda instrukcja MSIL jest emitowany. W bieżącej implementacji wszystkie żądania <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> są wywoływane, gdy wywoływana jest metoda lub gdy wywoływany jest kompilator just-in-time (JIT), jeśli metoda jest wywoływana bez wywoływania <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Jeśli domena aplikacji na to zezwala, anonimowo hostowane metody dynamiczne mogą pomijać kontrole widoczności JIT, z zastrzeżeniem następujących ograniczeń: Typy niepubliczne i elementy członkowskie, do których ma dostęp anonimowo obsługiwana metoda dynamiczna, muszą znajdować się w zestawach, których zestawy dotacji są równe lub podzbiory zestawu dotacji stosu wywołań emitujących. Ta ograniczona możliwość pominięcia kontroli widoczności JIT <xref:System.Security.Permissions.ReflectionPermission> jest <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> włączona, jeśli domena aplikacji udziela flagą.  
  
- Jeśli metoda używa tylko typów publicznych i elementów członkowskich, żadne uprawnienia nie są wymagane podczas budowy.  
  
- Jeśli określisz, że kontrole widoczności JIT powinny zostać pominięte, żądanie, które jest tworzone podczas konstruowania metody zawiera <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagą i zestaw dotacji zestawu, który zawiera niepubliczny element członkowski, który jest dostępny.  
  
 Ponieważ zestaw dotacji niepublicznych jest brany pod uwagę, częściowo <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> zaufany kod, który został przyznany, nie może podnieść jego uprawnień, wykonując niepubliczne elementy członkowskie zaufanych zestawów.  
  
 Podobnie jak w przypadku innych wyemitowanych kodu, wykonywanie metody dynamicznej wymaga żadnych uprawnień wymaganych przez metody używane przez metodę dynamiczną.  
  
 Zestaw systemowy, który obsługuje anonimowo hostowane <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> metody dynamiczne używa modelu przezroczystości, który jest model przezroczystości, który został użyty w programie .NET Framework przed .NET Framework 4.  
  
 Aby uzyskać więcej <xref:System.Reflection.Emit.DynamicMethod> informacji, zobacz klasę.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Generowanie anonimowo hostowanych metod dynamicznych z częściowo zaufanego kodu  
 Należy wziąć pod uwagę warunki, w których zestaw z uprawnieniami do Internetu może wygenerować anonimowo hostowane metody dynamicznej i wykonać go:  
  
- Metoda dynamiczna używa tylko typów publicznych i elementów członkowskich. Jeśli jego zestaw <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>dotacji zawiera , może używać typów niepublicznych i członków dowolnego zestawu, którego zestaw dotacji jest równy lub podzbiór zestawu dotacji zestawu emisji.  
  
- Uprawnienia, które są wymagane przez wszystkie typy i elementy członkowskie używane przez metodę dynamiczną są uwzględniane w zestawie dotacji częściowo zaufanego zestawu.  
  
> [!NOTE]
> Metody dynamiczne nie obsługują symboli debugowania.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Metody dynamiczne skojarzone z istniejącymi złożeniami  
 Aby skojarzyć metodę dynamiczną z typem lub modułem w istniejącym zestawie, należy użyć dowolnego <xref:System.Reflection.Emit.DynamicMethod> konstruktora, który określi skojarzony typ lub moduł. Uprawnienia, które są wymagane do wywołania tych konstruktorów różnią się, ponieważ kojarzenie metody dynamicznej z istniejącym typem lub modułem daje metodę dynamiczną dostęp do typów niepublicznych i elementów członkowskich:  
  
- Metoda dynamiczna, która jest skojarzona z typem ma dostęp do wszystkich elementów członkowskich tego typu, nawet prywatnych elementów członkowskich oraz do wszystkich typów wewnętrznych i elementów członkowskich w zestawie, który zawiera skojarzony typ.  
  
- Metoda dynamiczna, która jest skojarzona z `internal` modułem ma`Friend` dostęp do `assembly` wszystkich typów i elementów członkowskich (w języku Visual Basic, we wspólnym języku metadanych środowiska wykonawczego) w module.  
  
 Ponadto można użyć konstruktora, który określa możliwość pominąć kontroli widoczności kompilatora JIT. W ten sposób daje dostęp do metody dynamicznej do wszystkich typów i elementów członkowskich we wszystkich zestawach, niezależnie od poziomu dostępu.  
  
 Uprawnienia wymagane przez konstruktora zależą od tego, ile dostępu zdecydujesz się nadać dynamicznej metody:  
  
- Jeśli metoda używa tylko typów publicznych i członków i skojarzyć go z własnym typem lub własnego modułu, nie są wymagane żadne uprawnienia.  
  
- Jeśli określisz, że kontrole widoczności JIT powinny <xref:System.Security.Permissions.ReflectionPermission> zostać <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> pominięte, konstruktor wymaga z flagą.  
  
- Jeśli metoda dynamiczna zostanie skojarzona z innym typem, nawet innym <xref:System.Security.Permissions.ReflectionPermission> typem <xref:System.Security.Permissions.SecurityPermission> we <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> własnym zestawie, konstruktor wymaga <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi i flagi.  
  
- Jeśli metoda dynamiczna zostanie skojarzona z typem lub modułem w <xref:System.Security.Permissions.ReflectionPermission> innym <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> zestawie, konstruktor wymaga dwóch rzeczy: z flagą i zestawem grantów zestawu zawierającego inny moduł. Oznacza to, że stos wywołań musi zawierać wszystkie uprawnienia w <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>zestawie dotacji modułu docelowego, a także .  
  
    > [!NOTE]
    > W przypadku zgodności z powrotem, jeśli żądanie <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> dla docelowego zestawu <xref:System.Security.Permissions.SecurityPermission> dotacji <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> plus kończy się niepowodzeniem, konstruktor wymaga z flagą.  
  
 Mimo że elementy na tej liście są opisane w kategoriach zestawu dotacji zestawu emitującego, należy pamiętać, że wymagania są dokonywane względem pełnego stosu wywołań, w tym granicy domeny aplikacji.  
  
 Aby uzyskać więcej <xref:System.Reflection.Emit.DynamicMethod> informacji, zobacz klasę.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Generowanie metod dynamicznych z częściowo zaufanego kodu  
  
> [!NOTE]
> Zalecanym sposobem generowania metod dynamicznych z częściowo zaufanego kodu jest użycie [anonimowo hostowanych metod dynamicznych.](#Anonymously_Hosted_Dynamic_Methods)  
  
 Należy wziąć pod uwagę warunki, w których zestaw z uprawnieniami do Internetu może wygenerować metodę dynamiczną i wykonać ją:  
  
- Metoda dynamiczna jest skojarzona z modułem lub typem, który <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> go emituje, lub jego zestaw dotacji zawiera i jest skojarzony z modułem w zestawie, którego zestaw dotacji jest równy lub podzbiór zestawu grantów zestawu emisji.  
  
- Metoda dynamiczna używa tylko typów publicznych i elementów członkowskich. Jeśli jego zestaw <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> dotacji zawiera i jest skojarzony z modułem w zestawie, którego zestaw dotacji jest równy lub podzbiór `internal` zestawu`Friend` dotacji zestawu `assembly` emisji, może używać typów i elementów członkowskich oznaczonych (w języku Visual Basic, w metadanych środowiska wykonawczego języka wspólnego) w skojarzonym module.  
  
- Uprawnienia wymagane przez wszystkie typy i elementy członkowskie używane przez metodę dynamiczną są uwzględniane w zestawie dotacji częściowo zaufanego zestawu.  
  
- Metoda dynamiczna nie pomija kontroli widoczności JIT.  
  
> [!NOTE]
> Metody dynamiczne nie obsługują symboli debugowania.  
  
<a name="Version_Information"></a>
## <a name="version-information"></a>Informacje o wersji  
 Począwszy od programu .NET Framework 4, zasady zabezpieczeń dla całego komputera są eliminowane, a przezroczystość zabezpieczeń staje się domyślnym mechanizmem wymuszania. Zobacz [Zmiany zabezpieczeń](../security/security-changes.md).  
  
 Począwszy od dodatku Service Pack 1 .NET Framework 2.0, <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> nie jest już wymagane podczas emitowania zestawów dynamicznych i metod dynamicznych. Ta flaga jest wymagana we wszystkich wcześniejszych wersjach programu .NET Framework.  
  
> [!NOTE]
> <xref:System.Security.Permissions.ReflectionPermission>z <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> flagą jest domyślnie `FullTrust` uwzględniona w zestawach uprawnień i `LocalIntranet` nazwanych, ale nie w zestawie `Internet` uprawnień. W związku z tym we wcześniejszych wersjach programu .NET Framework biblioteka może <xref:System.Security.PermissionSet.Assert%2A> być <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>używana z uprawnieniami do Internetu tylko wtedy, gdy wykonuje for . Takie biblioteki wymagają starannego przeglądu zabezpieczeń, ponieważ błędy kodowania mogą spowodować luki w zabezpieczeniach. .NET Framework 2.0 SP1 umożliwia emitowanie kodu w scenariuszach częściowego zaufania bez wystawiania żadnych żądań zabezpieczeń, ponieważ generowanie kodu nie jest z natury uprzywilejowaną operacją. Oznacza to, że wygenerowany kod nie ma więcej uprawnień niż zestaw, który go emituje. Dzięki temu biblioteki, które emitują kod, są <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>przezroczyste i eliminuje konieczność potwierdzenia , co upraszcza zadanie pisania bezpiecznej biblioteki.  
  
 Ponadto .NET Framework 2.0 SP1 wprowadza <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagę dostępu do typów niepublicznych i elementów członkowskich z częściowo zaufanych metod dynamicznych. Starsze wersje programu .NET <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> Framework wymagają flagi dla metod dynamicznych, które uzyskują dostęp do typów niepublicznych i elementów członkowskich; jest to uprawnienie, które nigdy nie powinno być przyznane częściowo zaufanemu kodowi.  
  
 Na koniec .NET Framework 2.0 SP1 wprowadza metody anonimowo hostowane.  
  
### <a name="obtaining-information-on-types-and-members"></a>Uzyskiwanie informacji o typach i członkach  
 Począwszy od programu .NET Framework 2.0, żadne uprawnienia nie są wymagane do uzyskania informacji o typach niepublicznych i członków. Odbicie służy do uzyskania informacji potrzebnych do emitowania metod dynamicznych. Na przykład <xref:System.Reflection.MethodInfo> obiekty są używane do emitowania wywołań metody. Starsze wersje programu .NET <xref:System.Security.Permissions.ReflectionPermission> Framework <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> wymagają flagi. Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące zabezpieczeń dla refleksji](security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zagadnienia dotyczące zabezpieczeń dla odbicia](security-considerations-for-reflection.md)
- [Emitowanie dynamicznych metod i zestawów](emitting-dynamic-methods-and-assemblies.md)
