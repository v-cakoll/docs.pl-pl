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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2bdaef52bbc4cac0abfcbf8724f3c5c602bc8f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045797"
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
 Zestawy dynamiczne są tworzone przy użyciu przeciążenia <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> metody. Większość przeciążeń tej metody jest przestarzałych w .NET Framework 4 z powodu usunięcia zasad zabezpieczeń dla całego komputera. (Zobacz [zmiany zabezpieczeń](../security/security-changes.md)). Pozostałe przeciążenia mogą być wykonywane przez dowolny kod niezależnie od poziomu zaufania. Te przeciążenia dzielą się na dwie grupy: te, które określają listę atrybutów, które mają być stosowane do zestawu dynamicznego podczas jego tworzenia, a te, które nie. Jeśli nie określisz modelu przezroczystości dla zestawu, stosując <xref:System.Security.SecurityRulesAttribute> atrybut podczas tworzenia, model przezroczystości jest Dziedziczony z zestawu emitującego.  
  
> [!NOTE]
> Atrybuty, które są stosowane do zestawu dynamicznego po jego utworzeniu przy użyciu <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> metody, nie są uwzględniane do momentu zapisania zestawu na dysku i ponownego załadowania do pamięci.  
  
 Kod w zestawie dynamicznym ma dostęp do widocznych typów i elementów członkowskich w innych zestawach.  
  
> [!NOTE]
> Zestawy dynamiczne nie używają <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flag i <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> , które umożliwiają metodom dynamicznym dostęp do niepublicznych typów i elementów członkowskich.  
  
 Przejściowe zestawy dynamiczne są tworzone w pamięci i nigdy nie są zapisywane na dysku, więc nie wymagają uprawnień dostępu do plików. Zapisywanie dynamicznego zestawu na dysku wymaga <xref:System.Security.Permissions.FileIOPermission> odpowiedniej flagi.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Generowanie zestawów dynamicznych przy użyciu częściowo zaufanego kodu  
 Rozważ warunki, w których zestaw z uprawnieniami internetowymi może generować tymczasowy dynamiczny zestaw i wykonać swój kod:  
  
- W zestawie dynamicznym są stosowane tylko typy publiczne i elementy członkowskie innych zestawów.  
  
- Uprawnienia wymagane przez te typy i członków są zawarte w zestawie uprawnień częściowo zaufanego zestawu.  
  
- Zestaw nie został zapisany na dysku.  
  
- Symbole debugowania nie są generowane. (`Internet` i`LocalIntranet` zestawy uprawnień nie obejmują wymaganych uprawnień).  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonimowo hostowane metody dynamiczne  
 Anonimowo hostowane metody dynamiczne są tworzone przy użyciu dwóch <xref:System.Reflection.Emit.DynamicMethod> konstruktorów, które nie określają skojarzonego typu lub modułu, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> i <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Te konstruktory umieszczają metody dynamiczne w wbudowanym, w pełni zaufanym, nieprzezroczystym zestawie zabezpieczeń. Do korzystania z tych konstruktorów lub do emitowania kodu dla metod dynamicznych nie są wymagane żadne uprawnienia.  
  
 Zamiast tego, gdy tworzona jest anonimowo obsługiwana metoda dynamiczna, stos wywołań jest przechwytywany. Gdy metoda jest zbudowana, wymagania dotyczące zabezpieczeń są wykonywane względem przechwyconego stosu wywołań.  
  
> [!NOTE]
> Koncepcje są wykonywane w czasie konstruowania metody. Oznacza to, że żądania mogą zostać wykonane, ponieważ każda instrukcja MSIL jest emitowana. W bieżącej implementacji wszystkie wymagania są wykonywane, gdy <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> wywoływana jest metoda lub gdy wywoływany jest kompilator just-in-Time (JIT), jeśli metoda jest wywoływana bez wywoływania. <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>  
  
 Jeśli domena aplikacji zezwoli na to, anonimowo obsługiwane metody dynamiczne mogą pominąć sprawdzanie widoczności JIT, z uwzględnieniem następujących ograniczeń: Typy niepubliczne i elementy członkowskie, do których uzyskuje dostęp anonimowo hostowaną metodę dynamiczną, muszą znajdować się w zestawach, których zbiory przydziału są równe lub podzbiory, zestaw przydzielania wyemitowanego stosu wywołań. Ta ograniczona możliwość pomijania sprawdzania widoczności JIT jest włączona, jeśli domena aplikacji przyznaje <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> z flagą.  
  
- Jeśli metoda używa tylko typów publicznych i członków, podczas konstruowania nie są wymagane żadne uprawnienia.  
  
- Jeśli określisz, że testy widoczności JIT powinny być pomijane, żądanie, które jest wykonywane, gdy metoda jest zbudowana <xref:System.Security.Permissions.ReflectionPermission> , obejmuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagę i zestaw dotacji zestawu, który zawiera niepubliczny element członkowski, do którego jest uzyskiwany dostęp.  
  
 Ze względu na to, że dla niepublicznego elementu członkowskiego jest brany pod uwagę, częściowo zaufany kod <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> , który został udzielony, nie może podwyższyć poziomu uprawnień, wykonując niepubliczne elementy członkowskie zaufanych zestawów.  
  
 Podobnie jak w przypadku każdego innego emitowanego kodu, wykonanie metody dynamicznej wymaga dowolnych uprawnień wymaganych przez metodę dynamiczną.  
  
 Zestaw systemowy, który hostuje anonimowo obsługiwane metody dynamiczne, <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> korzysta z modelu przezroczystości, który jest modelem przezroczystości, który został użyty w .NET Framework przed .NET Framework 4.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.Emit.DynamicMethod> Klasa.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Generowanie anonimowo obsługiwanych metod dynamicznych z poziomu częściowo zaufanego kodu  
 Rozważ warunki, w których zestaw z uprawnieniami internetowymi może generować anonimowo hostowaną metodę dynamiczną i wykonać ją:  
  
- Metoda dynamiczna używa tylko typów publicznych i elementów członkowskich. Jeśli jego zestaw uprawnień zawiera <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, może używać typów niepublicznych i elementów członkowskich dowolnego zestawu, którego przydzielenie jest równe lub podzestawu zestawu, który emitujący zestaw.  
  
- Uprawnienia, które są wymagane przez wszystkie typy i elementy członkowskie używane przez metodę dynamiczną, są uwzględniane w zestawie uprawnień częściowo zaufanego zestawu.  
  
> [!NOTE]
> Metody dynamiczne nie obsługują symboli debugowania.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Metody dynamiczne skojarzone z istniejącymi zestawami  
 Aby skojarzyć metodę dynamiczną z typem lub modułem w istniejącym zestawie, użyj dowolnego <xref:System.Reflection.Emit.DynamicMethod> konstruktora, który określa skojarzony typ lub moduł. Uprawnienia, które są wymagane do wywołania tych konstruktorów, różnią się, ponieważ kojarzenie metody dynamicznej z istniejącym typem lub modułem zapewnia metodę dynamiczną dostęp do typów niepublicznych i członków:  
  
- Metoda dynamiczna, która jest skojarzona z typem, ma dostęp do wszystkich elementów członkowskich tego typu, nawet prywatnych składowych i wszystkich typów wewnętrznych i członków zestawu, który zawiera skojarzony typ.  
  
- Metoda dynamiczna skojarzona z modułem ma dostęp do wszystkich `internal` typów i elementów członkowskich (`Friend` w Visual Basic `assembly` w metadanych środowiska uruchomieniowego języka wspólnego) w module.  
  
 Ponadto można użyć konstruktora, który określa możliwość pomijania kontroli widoczności kompilatora JIT. Dzięki temu metoda dynamiczna zapewnia dostęp do wszystkich typów i elementów członkowskich we wszystkich zestawach, niezależnie od poziomu dostępu.  
  
 Uprawnienia wymagane przez konstruktora zależą od tego, jak dużo dostępu decyduje o przydzieleniu metody dynamicznej:  
  
- Jeśli metoda używa tylko typów publicznych i elementów członkowskich i kojarzy ją z własnym typem lub własnym modułem, nie są wymagane żadne uprawnienia.  
  
- Jeśli określisz, że testy widoczności JIT powinny być pomijane, Konstruktor wymaga <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi z flagą.  
  
- Jeśli metoda dynamiczna zostanie skojarzona z innym typem, nawet innym typem <xref:System.Security.Permissions.ReflectionPermission> we własnym zestawie, Konstruktor wymaga <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi i <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> flagą.  
  
- Jeśli metoda dynamiczna zostanie skojarzona z typem lub modułem w innym zestawie, Konstruktor wymaga dwóch rzeczy: <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ze flagą i zestawem przydzielenia zestawu zawierającego inny moduł. Oznacza to, że stos wywołań musi zawierać wszystkie uprawnienia w zestawie przyznawania modułu docelowego, a także <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    > W celu zapewnienia zgodności z poprzednimi wersjami, jeśli żądanie dotyczące <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> zestawu dotacji docelowej Plus nie <xref:System.Security.Permissions.SecurityPermission> powiedzie <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> się, Konstruktor wymaga flagi z flagą.  
  
 Chociaż elementy znajdujące się na tej liście są opisane w artykule dotyczącym zestawu emisji, należy pamiętać, że żądania są wykonywane względem pełnego stosu wywołań, w tym granicy domeny aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.Emit.DynamicMethod> Klasa.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Generowanie metod dynamicznych z częściowo zaufanego kodu  
  
> [!NOTE]
> Zalecanym sposobem generowania metod dynamicznych z częściowo zaufanego kodu jest użycie [anonimowo obsługiwanych metod dynamicznych](#Anonymously_Hosted_Dynamic_Methods).  
  
 Rozważ warunki, w których zestaw z uprawnieniami internetowymi może generować metodę dynamiczną i wykonać ją:  
  
- Metoda dynamiczna jest skojarzona z modułem lub typem, który emituje go, lub jego zestaw przydzielenia zawiera <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i jest skojarzony z modułem w zestawie, którego przystawka jest równa lub podzbiorowi przydzielonego zestawu emisji.  
  
- Metoda dynamiczna używa tylko typów publicznych i elementów członkowskich. Jeśli zestaw przyznanych <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> elementów zawiera i jest skojarzony z modułem w zestawie, którego przystawka jest równa lub podzbiorem zestawu, można użyć typów i członków oznaczonych `internal` (`Friend` w Visual Basic, `assembly`w obszarze metadane środowiska uruchomieniowego języka wspólnego w skojarzonym module.  
  
- Uprawnienia wymagane przez wszystkie typy i elementy członkowskie używane przez metodę dynamiczną są zawarte w zestawie uprawnień częściowo zaufanego zestawu.  
  
- Metoda dynamiczna nie pomija sprawdzania widoczności JIT.  
  
> [!NOTE]
> Metody dynamiczne nie obsługują symboli debugowania.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Informacje o wersji  
 Począwszy od .NET Framework 4, zasady zabezpieczeń dla całego komputera są eliminowane i przezroczystość zabezpieczeń staną się domyślnym mechanizmem wymuszania. Zobacz [zmiany zabezpieczeń](../security/security-changes.md).  
  
 Począwszy od .NET Framework 2,0 z dodatkiem Service Pack <xref:System.Security.Permissions.ReflectionPermission> 1, <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> z flagą nie jest już wymagane w przypadku emitowania zestawów dynamicznych i metod dynamicznych. Ta flaga jest wymagana we wszystkich wcześniejszych wersjach .NET Framework.  
  
> [!NOTE]
> <xref:System.Security.Permissions.ReflectionPermission>z flagą jest uwzględniana domyślnie `FullTrust` w zestawach `LocalIntranet` uprawnień i `Internet` nazwanych, ale nie w zestawie uprawnień. <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> W związku z tym we wcześniejszych wersjach .NET Framework Biblioteka może być używana z uprawnieniami internetowymi tylko wtedy, gdy jest wykonywana <xref:System.Security.PermissionSet.Assert%2A> przez <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Takie biblioteki wymagają starannej oceny zabezpieczeń, ponieważ błędy kodowania mogą spowodować powstanie luk w zabezpieczeniach. Program .NET Framework 2,0 z dodatkiem SP1 umożliwia emitowanie kodu w scenariuszach częściowej relacji zaufania bez wydawania jakichkolwiek wymagań dotyczących zabezpieczeń, ponieważ generowanie kodu nie jest z założenia uprzywilejowanej operacji. Oznacza to, że wygenerowany kod nie ma więcej uprawnień niż zestaw, który emituje go. Pozwala to na używanie bibliotek, które emitują kod jako przezroczysty i eliminuje konieczność potwierdzenia <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, co upraszcza zadanie pisania bezpiecznej biblioteki.  
  
 Ponadto w .NET Framework 2,0 SP1 wprowadzono <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagę uzyskiwania dostępu do niepublicznych typów i członków z częściowo zaufanych metod dynamicznych. Wcześniejsze wersje .NET Framework wymagają <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi metoda dynamiczna, która uzyskuje dostęp do niepublicznych typów i składowych; jest to uprawnienie, które nigdy nie powinno być przyznane do częściowo zaufanego kodu.  
  
 Na koniec .NET Framework 2,0 z dodatkiem SP1 wprowadza anonimowo hostowane metody.  
  
### <a name="obtaining-information-on-types-and-members"></a>Uzyskiwanie informacji na temat typów i członków  
 Począwszy od .NET Framework 2,0, żadne uprawnienia nie są wymagane do uzyskania informacji na temat typów niepublicznych i członków. Odbicie służy do uzyskiwania informacji niezbędnych do emitowania metod dynamicznych. Na przykład <xref:System.Reflection.MethodInfo> obiekty są używane do emisji wywołań metod. Wcześniejsze wersje .NET Framework wymagają <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> flagi z flagą. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń dotyczące odbicia](security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące zabezpieczeń dla odbicia](security-considerations-for-reflection.md)
- [Emitowanie dynamicznych metod i zestawów](emitting-dynamic-methods-and-assemblies.md)
