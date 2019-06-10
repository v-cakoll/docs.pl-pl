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
ms.openlocfilehash: 434a88e305f833a5a95bb62835b5badd4a2c4949
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816136"
---
# <a name="security-issues-in-reflection-emit"></a>Problemy związane z zabezpieczeniami w emisji odbicia
Program .NET Framework oferuje trzy sposoby, aby emitować języka Microsoft intermediate language (MSIL), każdy z własną problemy z zabezpieczeniami:  
  
- [Dynamicznych zestawów](#Dynamic_Assemblies)  
  
- [Anonimowo obsługiwane metody dynamiczne](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Metody dynamiczne są skojarzone z istniejących zestawów](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Niezależnie od tego, w sposób generowania kodu dynamiczne wykonywania wygenerowany kod wymaga uprawnień, które są wymagane przez używane typy i metody, które korzysta z wygenerowanego kodu.  
  
> [!NOTE]
>  Uprawnienia, które są wymagane przez odzwierciedlenie na kodzie i emitowanie kodu zmieniły się wraz z powodzeniem wersje programu .NET Framework. Zobacz [informacje o wersji](#Version_Information)w dalszej części tego tematu.  
  
<a name="Dynamic_Assemblies"></a>   
## <a name="dynamic-assemblies"></a>Dynamicznych zestawów  
 Dynamiczne zestawy są tworzone za pomocą przeciążenia <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> metody. Większość przeciążenia tej metody są przestarzałe w programie .NET Framework 4 z powodu zniesienie zasady zabezpieczeń komputera. (Zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).) Pozostałe przeciążenia mogą być wykonywane przez każdy kod, niezależnie od poziomu zaufania. Te przeciążone funkcje można podzielić na dwie grupy: te, które określają listę atrybutów, które mają zastosowanie do zestawu dynamicznego, podczas jego tworzenia, a także tych, które nie obsługują. Jeśli nie określisz modelu przezroczystości dla zestawu, stosując <xref:System.Security.SecurityRulesAttribute> atrybutu podczas tworzenia jej modelu przezroczystości jest dziedziczony z emitujące zgromadzenia.  
  
> [!NOTE]
>  Atrybuty stosowane do zestawu dynamicznego, po jego utworzeniu, za pomocą <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> metody, obowiązują do momentu zestawu został zapisany na dysku i ponownie załadowany do pamięci.  
  
 Kod w zestawie dynamicznym dostęp widoczne typy i elementy członkowskie w innych zestawach.  
  
> [!NOTE]
>  Nie należy używać dynamicznych zestawów <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> i <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi umożliwiające metod dynamicznych, aby uzyskać dostęp do niepublicznych typy i elementy członkowskie.  
  
 Przejściowy dynamicznych zestawów są tworzone w pamięci i nigdy nie była zapisywana na dysku, więc wymagają one nie uprawnienia dostępu do pliku. Zapisywanie zestawu dynamicznego dysku wymaga <xref:System.Security.Permissions.FileIOPermission> przy użyciu odpowiednich flag.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Generowanie zestawów dynamicznych z częściowo zaufanego kodu  
 Należy wziąć pod uwagę warunków, w których zestaw z uprawnieniami do Internetu można wygenerować przemijający zestaw dynamiczny i wykonać jego kod:  
  
- Zestaw dynamiczny używa tylko typy publiczne i innych zestawów.  
  
- Uprawnienia wymagane przez tych typów i elementów członkowskich znajdują się w przydzielonym zestawie częściowo zaufanym zestawem.  
  
- Zestaw nie jest zapisywana na dysku.  
  
- Debugowanie symbole nie są generowane. (`Internet` i `LocalIntranet` zestawy uprawnień nie ma wystarczających uprawnień.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonimowo hostowane metody dynamiczne  
 Anonimowo obsługiwane metody dynamiczne są tworzone za pomocą dwóch <xref:System.Reflection.Emit.DynamicMethod> konstruktorów, które nie określaj skojarzony typ nebo modul, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> i <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Te konstruktory umieść metod dynamicznych w zestawie dostarczane przez system, w pełni zaufany, zabezpieczenia przejrzysty. Nie uprawnienia są wymagane, użyj tych konstruktorów lub wyemitować kodu dla metod dynamicznych.  
  
 Zamiast tego po utworzeniu anonimowo obsługiwana metoda dynamiczna, stos wywołań są przechwytywane. Gdy metoda jest konstruowany, żądania kontroli zabezpieczeń są wykonywane względem stos wywołań przechwycony.  
  
> [!NOTE]
>  Model żądania są wprowadzane podczas konstruowania metody. Oznacza to, że żądania można ustanowić zgodnie z każdej instrukcji MSIL jest emitowany. W bieżącej implementacji wszystkich potrzeb zostały wprowadzone, gdy <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> metoda jest wywoływana lub kiedy kompilator just-in-time (JIT) zostanie wywołana, jeśli metoda jest wywoływana bez wywoływania <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Domeny aplikacji pozwala na on, anonimowo obsługiwane metody dynamiczne można pominąć kontrole widoczność JIT, z zastrzeżeniem następujące ograniczenia: Niepublicznych typy i składowe, które uzyskują dostęp anonimowo obsługiwana metoda dynamiczna musi być w zestawach, którego grant zestawy są równe lub podzestawy zestaw uprawnień emitowanie stosu wywołań. Ta ograniczona zdolność do pominięcia widoczności JIT sprawdza, czy jest włączone, jeśli domena aplikacji daje <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi.  
  
- Jeśli metoda używa tylko typy publiczne i elementy członkowskie, podczas konstruowania są wymagane żadne uprawnienia.  
  
- Jeśli określisz, że sprawdzenie widoczność JIT ma być pomijana, żądanie, w tym, gdy metoda jest konstruowany obejmuje <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagę i zestaw uprawnień zestawu, który zawiera niepubliczna składowa, który jest dostępny.  
  
 Ponieważ zestaw uprawnień niepubliczna składowa jest brana pod uwagę, częściowo zaufany kod, któremu udzielono <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> nie podniesienia jego uprawnień, wykonując niepubliczne elementy członkowskie zaufanych zestawów.  
  
 Jako przy użyciu innych emitowany kod, wykonywanie metody dynamicznej wymaga wszelkie uprawnienia są wymagane przez metody, które korzysta z metody dynamicznej.  
  
 Używa zestawu systemowego, który jest hostem anonimowo hostowane metody dynamiczne <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> modelu przezroczystości, czyli modelu przezroczystości, który był używany w programie .NET Framework przed programu .NET Framework 4.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.Emit.DynamicMethod> klasy.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Generowanie anonimowo obsługiwanych metod dynamicznych z częściowo zaufanego kodu  
 Należy wziąć pod uwagę warunków, w których zestawu z uprawnieniami do Internetu można wygenerować anonimowo obsługiwana metoda dynamiczna i uruchomić go:  
  
- Metoda dynamiczna używa tylko typy publiczne i elementy członkowskie. Jeśli jego zestawu uprawnień obejmuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, może użyć niepublicznych typy i elementy członkowskie dowolnego zestawu, którego przydział zestawu jest równy lub podzbiór, zestaw uprawnień emitujące zgromadzenia.  
  
- Uprawnienia, które są wymagane przez wszystkie typy i elementy członkowskie używane przez metodę dynamiczną znajdują się w przydzielonym zestawie częściowo zaufanym zestawem.  
  
> [!NOTE]
>  Metody dynamiczne nie obsługują symbole debugowania.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Metody dynamiczne są skojarzone z istniejących zestawów  
 Aby skojarzyć metodę dynamiczną z typu lub modułu w istniejącego zestawu, można użyć dowolnego z <xref:System.Reflection.Emit.DynamicMethod> konstruktorów, które określają skojarzony typ lub modułu. Uprawnienia, które są wymagane do wywołania tych konstruktorów różnią się, ponieważ skojarzyć metodę dynamiczną z istniejącego typu lub modułu udostępnia metodę dynamiczną niepublicznych typy i elementy członkowskie:  
  
- Metoda dynamiczna, która jest skojarzona z typem ma dostęp do wszystkich elementów członkowskich tego typu, a nawet prywatne składowe, i do wszystkich wewnętrznych typów i elementów członkowskich w zestawie, który zawiera skojarzony typ.  
  
- Metoda dynamiczna, która jest skojarzona z modułu ma dostęp do wszystkich `internal` typów i elementów członkowskich (`Friend` w języku Visual Basic `assembly` w typowych metadanych środowiska wykonawczego języka) w module.  
  
 Ponadto można użyć konstruktora, który określa, że zdolności do pominięcia widoczności kontroli kompilatora JIT. To daje dostęp metodę dynamiczną do wszystkich typów i elementów członkowskich w wszystkich zestawów, niezależnie od tego poziomu dostępu.  
  
 Uprawnienia wymagane przez Konstruktor zależeć na dostęp, ile zdecydujesz się Nadaj swojej metody dynamicznej:  
  
- Jeśli metoda używa tylko typy publiczne i elementy członkowskie i należy ją skojarzyć z swój własny typ lub własny moduł, nie są wymagane żadne uprawnienia.  
  
- Jeśli określisz, że należy pominąć kontrole widoczność JIT, Konstruktor zażąda <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi.  
  
- Jeśli metoda dynamiczna jest skojarzona z innym typem, nawet inny typ w zestawie z własnego konstruktora zapotrzebowania <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagę i <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> flagi.  
  
- Jeśli metoda dynamiczna jest skojarzona z typem lub moduł w innym zestawie, Konstruktor zapotrzebowania na dwie rzeczy: <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Flaga, a zestaw uprawnień zestawu, który zawiera inny moduł. Oznacza to, że stosu wywołań musi zawierać wszystkie uprawnienia w przydzielonym zestawie modułu docelowego, a także <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    >  Zgodności z poprzednimi wersjami, jeśli żądanie dla elementu docelowego zestaw uprawnień oraz <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> zakończy się niepowodzeniem, wymagań Konstruktor <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> flagi.  
  
 Mimo że elementy na tej liście są opisywana w kategoriach zestaw uprawnień zestawu emitującego, należy pamiętać, że wymagania będą wykonywane względem pełny stos wywołania, w tym granic domeny aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.Emit.DynamicMethod> klasy.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Generowanie metod dynamicznych na podstawie częściowo zaufany kod  
  
> [!NOTE]
>  Zalecanym sposobem Generowanie metod dynamicznych na podstawie częściowo zaufanego kodu jest użycie [anonimowo hostowane metody dynamiczne](#Anonymously_Hosted_Dynamic_Methods).  
  
 Należy wziąć pod uwagę warunków, w których zestaw z uprawnieniami do Internetu można generować metodę dynamiczną i uruchomić go:  
  
- Metoda dynamiczna jest skojarzony z modułu lub typu, który emituje go lub jego zestawu uprawnień obejmuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i jest skojarzona z modułu w zestawie, do którego przyznania zestaw jest równy lub podzbiór, zestaw uprawnień emitujące zgromadzenia.  
  
- Metoda dynamiczna używa tylko typy publiczne i elementy członkowskie. Jeśli jego zestawu uprawnień obejmuje <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i jest skojarzona z modułu w zestawie, do którego przydział zestawu jest równy lub podzbiór, zestaw uprawnień zestawu emitującego, można użyć, typy i składowe oznaczone `internal` (`Friend` w języku Visual Basic `assembly`w typowych metadanych środowiska wykonawczego języka) w module skojarzone.  
  
- Uprawnienia wymagane przez wszystkie typy i elementy członkowskie, używane przez metodę dynamiczną, znajdują się w przydzielonym zestawie częściowo zaufanym zestawem.  
  
- Metoda dynamiczna nie powoduje pominięcia widoczności JIT.  
  
> [!NOTE]
>  Metody dynamiczne nie obsługują symbole debugowania.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Informacje o wersji  
 Począwszy od programu .NET Framework 4, wyeliminowana zasady zabezpieczeń dla komputera i przezroczystości zabezpieczeń staje się domyślnego mechanizmu wymuszania. Zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Począwszy od .NET Framework 2.0 z dodatkiem Service Pack 1, <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> flaga nie jest już wymagany podczas emitowania dynamicznych zestawów i metod dynamicznych. Ta flaga jest wymagany we wcześniejszych wersjach programu .NET Framework.  
  
> [!NOTE]
>  <xref:System.Security.Permissions.ReflectionPermission> za pomocą <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> flaga jest domyślnie włączone w `FullTrust` i `LocalIntranet` zestawy nazwanych uprawnień, ale nie w `Internet` zestaw uprawnień. W związku z tym, we wcześniejszych wersjach programu .NET Framework, biblioteka może służyć z uprawnieniami do Internetu tylko wtedy, gdy wykonuje <xref:System.Security.PermissionSet.Assert%2A> dla <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Takie biblioteki wymagają weryfikacji zabezpieczeń zachowania ostrożność, ponieważ kodowanie błędów może spowodować luki w zabezpieczeniach. .NET Framework 2.0 z dodatkiem SP1 umożliwia kod był emitowany w scenariuszach częściowej relacji zaufania bez wydawania żadnych wymogów bezpieczeństwa, ponieważ generowanie kodu nie jest z natury uprzywilejowaną operacją. Oznacza to, że wygenerowany kod nie ma więcej uprawnień niż zestaw, który emituje go. Dzięki temu biblioteki, które emitują kod, aby być przezroczyste dla zabezpieczeń i usuwa potrzebę zapewnienia <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, która upraszcza proces bezpieczna biblioteka.  
  
 Ponadto program .NET Framework 2.0 z dodatkiem SP1 wprowadzono <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi do uzyskiwania dostępu do niepublicznych typy i elementy członkowskie z częściowo zaufanych metod dynamicznych. Wcześniejszych wersjach programu .NET Framework wymagają <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagę dla metod dynamicznych, które uzyskują dostęp do typów niepublicznych; jest to uprawnienia, które nigdy nie może być przyznany elementowi częściowo zaufanego kodu.  
  
 Na koniec .NET Framework 2.0 z dodatkiem SP1 wprowadzono anonimowo obsługiwane metody.  
  
### <a name="obtaining-information-on-types-and-members"></a>Uzyskiwanie informacji dotyczących typów i elementów członkowskich  
 Począwszy od [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], aby uzyskać informacje na temat niepublicznych typy i elementy członkowskie są wymagane żadne uprawnienia. Odbicie jest używany do uzyskiwania informacji potrzebnych do emitowania metody dynamicznej. Na przykład <xref:System.Reflection.MethodInfo> obiekty służą do emitowania wywołania metody. Wcześniejszych wersjach programu .NET Framework wymagają <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> flagi. Aby uzyskać więcej informacji, zobacz [Security Considerations for Reflection](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące zabezpieczeń dla odbicia](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
- [Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)
