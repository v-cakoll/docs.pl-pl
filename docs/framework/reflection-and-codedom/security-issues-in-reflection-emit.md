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
ms.openlocfilehash: f04b40edde0755315f3b4fd4284fc7c804a54313
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130044"
---
# <a name="security-issues-in-reflection-emit"></a>Problemy związane z zabezpieczeniami w emisji odbicia
.NET Framework udostępnia trzy sposoby emisji języka pośredniego firmy Microsoft (MSIL), z których każdy ma własne problemy z zabezpieczeniami:  
  
- [Zestawy dynamiczne](#Dynamic_Assemblies)  
  
- [Anonimowo hostowane metody dynamiczne](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Metody dynamiczne skojarzone z istniejącymi zestawami](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Niezależnie od sposobu generowania kodu dynamicznego wykonywanie wygenerowanego kodu wymaga wszystkich uprawnień, które są wymagane przez typy i metody używane przez wygenerowany kod.  
  
> [!NOTE]
> Uprawnienia, które są wymagane do odzwierciedlenia kodu i emitowania kodu, zostały zmienione wraz z pomyślnymi wersjami .NET Framework. [Informacje o wersji](#Version_Information)znajdują się w dalszej części tego tematu.  
  
<a name="Dynamic_Assemblies"></a>   
## <a name="dynamic-assemblies"></a>Zestawy dynamiczne  
 Zestawy dynamiczne są tworzone przy użyciu przeciążenia metody <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>. Większość przeciążeń tej metody jest przestarzałych w .NET Framework 4 z powodu usunięcia zasad zabezpieczeń dla całego komputera. (Zobacz [zmiany zabezpieczeń](../security/security-changes.md)). Pozostałe przeciążenia mogą być wykonywane przez dowolny kod niezależnie od poziomu zaufania. Te przeciążenia dzielą się na dwie grupy: te, które określają listę atrybutów, które mają być stosowane do zestawu dynamicznego podczas jego tworzenia, a te, które nie. Jeśli nie określisz modelu przezroczystości dla zestawu, stosując atrybut <xref:System.Security.SecurityRulesAttribute> podczas jego tworzenia, model przezroczystości jest Dziedziczony z zestawu emitującego.  
  
> [!NOTE]
> Atrybuty, które są stosowane do zestawu dynamicznego po jego utworzeniu, przy użyciu metody <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> nie są uwzględniane, dopóki zestaw nie zostanie zapisany na dysku i ponownie załadowany do pamięci.  
  
 Kod w zestawie dynamicznym ma dostęp do widocznych typów i elementów członkowskich w innych zestawach.  
  
> [!NOTE]
> Zestawy dynamiczne nie używają flag <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> i <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, które umożliwiają metodom dynamicznym dostęp do niepublicznych typów i elementów członkowskich.  
  
 Przejściowe zestawy dynamiczne są tworzone w pamięci i nigdy nie są zapisywane na dysku, więc nie wymagają uprawnień dostępu do plików. Zapisywanie dynamicznego zestawu na dysku wymaga <xref:System.Security.Permissions.FileIOPermission> z odpowiednimi flagami.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Generowanie zestawów dynamicznych przy użyciu częściowo zaufanego kodu  
 Rozważ warunki, w których zestaw z uprawnieniami internetowymi może generować tymczasowy dynamiczny zestaw i wykonać swój kod:  
  
- W zestawie dynamicznym są stosowane tylko typy publiczne i elementy członkowskie innych zestawów.  
  
- Uprawnienia wymagane przez te typy i członków są zawarte w zestawie uprawnień częściowo zaufanego zestawu.  
  
- Zestaw nie został zapisany na dysku.  
  
- Symbole debugowania nie są generowane. (`Internet` i `LocalIntranet` zestawy uprawnień nie obejmują wymaganych uprawnień).  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonimowo hostowane metody dynamiczne  
 Anonimowo hostowane metody dynamiczne są tworzone przy użyciu dwóch konstruktorów <xref:System.Reflection.Emit.DynamicMethod>, które nie określają skojarzonego typu lub modułu, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> i <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Te konstruktory umieszczają metody dynamiczne w wbudowanym, w pełni zaufanym, nieprzezroczystym zestawie zabezpieczeń. Do korzystania z tych konstruktorów lub do emitowania kodu dla metod dynamicznych nie są wymagane żadne uprawnienia.  
  
 Zamiast tego, gdy tworzona jest anonimowo obsługiwana metoda dynamiczna, stos wywołań jest przechwytywany. Gdy metoda jest zbudowana, wymagania dotyczące zabezpieczeń są wykonywane względem przechwyconego stosu wywołań.  
  
> [!NOTE]
> Koncepcje są wykonywane w czasie konstruowania metody. Oznacza to, że żądania mogą zostać wykonane, ponieważ każda instrukcja MSIL jest emitowana. W bieżącej implementacji wszystkie wymagania są wykonywane, gdy wywoływana jest metoda <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> lub gdy wywoływany jest kompilator just-in-Time (JIT), jeśli metoda jest wywoływana bez wywoływania <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Jeśli domena aplikacji zezwoli na to, anonimowo hostowane metody dynamiczne mogą pominąć testy widoczności JIT, z zastrzeżeniem następującego ograniczenia: typy niepubliczne i składowe, do których uzyskuje dostęp anonimowo obsługiwana metoda dynamiczna, muszą znajdować się w zestawach, których zbiory przydziału są równe lub podzbiory zestawu, który emituje stos wywołań. Ta ograniczona możliwość pomijania sprawdzania widoczności JIT jest włączona, jeśli domena aplikacji udzieli <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
- Jeśli metoda używa tylko typów publicznych i członków, podczas konstruowania nie są wymagane żadne uprawnienia.  
  
- Jeśli określisz, że testy widoczności JIT powinny być pomijane, żądanie, które jest wykonywane, gdy tworzona jest metoda zawiera <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i zestawem przydzielenia zestawu zawierającego niepubliczny element członkowski, do którego jest uzyskiwany dostęp.  
  
 Ponieważ nie jest brany pod uwagę zestaw dotacji niepublicznego elementu członkowskiego, częściowo zaufany kod, który został udzielony <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> nie może podwyższyć poziomu uprawnień, wykonując niepubliczne elementy członkowskie zaufanych zestawów.  
  
 Podobnie jak w przypadku każdego innego emitowanego kodu, wykonanie metody dynamicznej wymaga dowolnych uprawnień wymaganych przez metodę dynamiczną.  
  
 Zestaw systemowy, który hostuje anonimowo obsługiwane metody dynamiczne, używa modelu przezroczystości <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType>, który jest modelem przezroczystości, który został użyty w .NET Framework przed .NET Framework 4.  
  
 Aby uzyskać więcej informacji, zobacz Klasa <xref:System.Reflection.Emit.DynamicMethod>.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Generowanie anonimowo obsługiwanych metod dynamicznych z poziomu częściowo zaufanego kodu  
 Rozważ warunki, w których zestaw z uprawnieniami internetowymi może generować anonimowo hostowaną metodę dynamiczną i wykonać ją:  
  
- Metoda dynamiczna używa tylko typów publicznych i elementów członkowskich. Jeśli jego zestaw uprawnień zawiera <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, może używać typów niepublicznych i elementów członkowskich dowolnego zestawu, którego zestaw dotacji jest równy lub podzbiór, a także zestaw przyznany zestaw emitujący.  
  
- Uprawnienia, które są wymagane przez wszystkie typy i elementy członkowskie używane przez metodę dynamiczną, są uwzględniane w zestawie uprawnień częściowo zaufanego zestawu.  
  
> [!NOTE]
> Metody dynamiczne nie obsługują symboli debugowania.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Metody dynamiczne skojarzone z istniejącymi zestawami  
 Aby skojarzyć metodę dynamiczną z typem lub modułem w istniejącym zestawie, użyj dowolnego z konstruktorów <xref:System.Reflection.Emit.DynamicMethod>, które określają skojarzony typ lub moduł. Uprawnienia, które są wymagane do wywołania tych konstruktorów, różnią się, ponieważ kojarzenie metody dynamicznej z istniejącym typem lub modułem zapewnia metodę dynamiczną dostęp do typów niepublicznych i członków:  
  
- Metoda dynamiczna, która jest skojarzona z typem, ma dostęp do wszystkich elementów członkowskich tego typu, nawet prywatnych składowych i wszystkich typów wewnętrznych i członków zestawu, który zawiera skojarzony typ.  
  
- Metoda dynamiczna skojarzona z modułem ma dostęp do wszystkich typów `internal` i członków (`Friend` w Visual Basic `assembly` w metadanych środowiska uruchomieniowego języka wspólnego) w module.  
  
 Ponadto można użyć konstruktora, który określa możliwość pomijania kontroli widoczności kompilatora JIT. Dzięki temu metoda dynamiczna zapewnia dostęp do wszystkich typów i elementów członkowskich we wszystkich zestawach, niezależnie od poziomu dostępu.  
  
 Uprawnienia wymagane przez konstruktora zależą od tego, jak dużo dostępu decyduje o przydzieleniu metody dynamicznej:  
  
- Jeśli metoda używa tylko typów publicznych i elementów członkowskich i kojarzy ją z własnym typem lub własnym modułem, nie są wymagane żadne uprawnienia.  
  
- Jeśli określisz, że testy widoczności JIT mają być pomijane, Konstruktor wymaga <xref:System.Security.Permissions.ReflectionPermission> ze flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>.  
  
- Jeśli metoda dynamiczna zostanie skojarzona z innym typem, nawet innym typem we własnym zestawie, Konstruktor wymaga <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> i <xref:System.Security.Permissions.SecurityPermission> z flagą <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType>.  
  
- W przypadku skojarzenia metody dynamicznej z typem lub modułem w innym zestawie, Konstruktor wymaga dwóch rzeczy: <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i zestawem przydzielenia zestawu zawierającego inny moduł. Oznacza to, że stos wywołań musi zawierać wszystkie uprawnienia w zestawie udzielania modułu docelowego, a <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    > W celu zapewnienia zgodności z poprzednimi wersjami, jeśli żądanie dotyczące zestawu dotacji docelowej Plus <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> nie powiedzie się, Konstruktor wymaga <xref:System.Security.Permissions.SecurityPermission> z flagą <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType>.  
  
 Chociaż elementy znajdujące się na tej liście są opisane w artykule dotyczącym zestawu emisji, należy pamiętać, że żądania są wykonywane względem pełnego stosu wywołań, w tym granicy domeny aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz Klasa <xref:System.Reflection.Emit.DynamicMethod>.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Generowanie metod dynamicznych z częściowo zaufanego kodu  
  
> [!NOTE]
> Zalecanym sposobem generowania metod dynamicznych z częściowo zaufanego kodu jest użycie [anonimowo obsługiwanych metod dynamicznych](#Anonymously_Hosted_Dynamic_Methods).  
  
 Rozważ warunki, w których zestaw z uprawnieniami internetowymi może generować metodę dynamiczną i wykonać ją:  
  
- Metoda dynamiczna jest skojarzona z modułem lub typem, który emituje go, lub jego zestaw przydzielenia zawiera <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i jest skojarzony z modułem w zestawie, którego przystawka jest równa lub podzbiorem przydzielonego zestawu emisji.  
  
- Metoda dynamiczna używa tylko typów publicznych i elementów członkowskich. Jeśli jego zestaw uprawnień zawiera <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i jest skojarzony z modułem w zestawie, którego przystawka jest równa lub podzbiorem zestawu emisji, może używać typów i składowych oznaczonych `internal` (`Friend` w Visual Basic , `assembly` w skojarzonym module metadanych aparatu plików wykonywalnych języka wspólnego.  
  
- Uprawnienia wymagane przez wszystkie typy i elementy członkowskie używane przez metodę dynamiczną są zawarte w zestawie uprawnień częściowo zaufanego zestawu.  
  
- Metoda dynamiczna nie pomija sprawdzania widoczności JIT.  
  
> [!NOTE]
> Metody dynamiczne nie obsługują symboli debugowania.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Informacje o wersji  
 Począwszy od .NET Framework 4, zasady zabezpieczeń dla całego komputera są eliminowane i przezroczystość zabezpieczeń staną się domyślnym mechanizmem wymuszania. Zobacz [zmiany zabezpieczeń](../security/security-changes.md).  
  
 Począwszy od .NET Framework 2,0 z dodatkiem Service Pack 1 <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> nie jest już wymagane podczas emitowania zestawów dynamicznych i metod dynamicznych. Ta flaga jest wymagana we wszystkich wcześniejszych wersjach .NET Framework.  
  
> [!NOTE]
> <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> jest uwzględniana domyślnie w `FullTrust` i `LocalIntranet` o nazwanych zestawach uprawnień, ale nie w zestawie uprawnień `Internet`. W związku z tym we wcześniejszych wersjach .NET Framework Biblioteka może być używana z uprawnieniami internetowymi tylko wtedy, gdy wykonuje <xref:System.Security.PermissionSet.Assert%2A> dla <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Takie biblioteki wymagają starannej oceny zabezpieczeń, ponieważ błędy kodowania mogą spowodować powstanie luk w zabezpieczeniach. Program .NET Framework 2,0 z dodatkiem SP1 umożliwia emitowanie kodu w scenariuszach częściowej relacji zaufania bez wydawania jakichkolwiek wymagań dotyczących zabezpieczeń, ponieważ generowanie kodu nie jest z założenia uprzywilejowanej operacji. Oznacza to, że wygenerowany kod nie ma więcej uprawnień niż zestaw, który emituje go. Pozwala to na używanie bibliotek, które emitują kod jako przezroczysty, i eliminuje konieczność potwierdzenia <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, co upraszcza zadanie pisania bezpiecznej biblioteki.  
  
 Ponadto w .NET Framework 2,0 SP1 wprowadzono flagę <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> do uzyskiwania dostępu do niepublicznych typów i członków z częściowo zaufanych metod dynamicznych. Wcześniejsze wersje .NET Framework wymagają flagi <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> dla metod dynamicznych, które uzyskują dostęp do typów niepublicznych i członków; jest to uprawnienie, które nigdy nie powinno zostać przyznane do częściowo zaufanego kodu.  
  
 Na koniec .NET Framework 2,0 z dodatkiem SP1 wprowadza anonimowo hostowane metody.  
  
### <a name="obtaining-information-on-types-and-members"></a>Uzyskiwanie informacji na temat typów i członków  
 Począwszy od .NET Framework 2,0, żadne uprawnienia nie są wymagane do uzyskania informacji na temat typów niepublicznych i członków. Odbicie służy do uzyskiwania informacji niezbędnych do emitowania metod dynamicznych. Na przykład obiekty <xref:System.Reflection.MethodInfo> są używane do emitowania wywołań metod. Wcześniejsze wersje .NET Framework wymagają <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń dotyczące odbicia](security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące zabezpieczeń dla odbicia](security-considerations-for-reflection.md)
- [Emitowanie dynamicznych metod i zestawów](emitting-dynamic-methods-and-assemblies.md)
