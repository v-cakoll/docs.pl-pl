---
title: "Problemy związane z zabezpieczeniami w emisji odbicia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d143798c4344b385d954cc64bd63c8f81eb48750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="security-issues-in-reflection-emit"></a>Problemy związane z zabezpieczeniami w emisji odbicia
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Udostępnia trzy sposoby Emituj Microsoft pośredniego language (MSIL), każdy z własną problemy z zabezpieczeniami:  
  
-   [Dynamiczne zestawy](#Dynamic_Assemblies)  
  
-   [Anonimowo hostowane metody dynamiczne](#Anonymously_Hosted_Dynamic_Methods)  
  
-   [Metody dynamiczne skojarzone z istniejących zestawów](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Niezależnie od sposobu generowania kodu dynamicznych wykonywania wygenerowany kod wymaga wszystkie uprawnienia, które są wymagane przez typy i metody, który korzysta z wygenerowanego kodu.  
  
> [!NOTE]
>  Uprawnienia, które są wymagane dla odbicia dla kodu i emitowanie kodu zostały zmienione z pomyślne wersje [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Zobacz [informacje o wersji](#Version_Information)w dalszej części tego tematu.  
  
<a name="Dynamic_Assemblies"></a>   
## <a name="dynamic-assemblies"></a>Dynamiczne zestawy  
 Dynamiczne zestawy są tworzone za pomocą przeciążenia metody <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> metody. Większość przeciążenie tej metody nie są używane w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], z powodu eliminacji zasad zabezpieczeń komputera. (Zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).) Pozostałe przeciążeń mogą być wykonywane przez kod, niezależnie od poziomu zaufania. Te przeciążenia można podzielić na dwie grupy: te, które określają listę atrybutów, które mają zastosowanie do zestawu dynamicznego podczas jego tworzenia oraz te, które nie. Jeśli nie określisz modelu przezroczystości dla zestawu, stosując <xref:System.Security.SecurityRulesAttribute> atrybutu podczas tworzenia go modelu przezroczystości jest dziedziczona z zestawu emisji.  
  
> [!NOTE]
>  Atrybuty stosowane do zestawu dynamicznego, po utworzeniu, za pomocą <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> metody, nie zostały wprowadzone, dopóki zestawu został zapisany na dysku i ponownie załadowana do pamięci.  
  
 Kod w zestawie dynamicznym są dostępne typy widoczne i elementów członkowskich w innych zestawów.  
  
> [!NOTE]
>  Zestawy dynamiczne nie należy używać <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> i <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi, które umożliwia dynamiczne metody dostępu do niepubliczne typów i członków.  
  
 Przejściowa dynamiczne zestawy są tworzone w pamięci i nigdy nie zapisano na dysku, więc niezbędnych nie uprawnienia dostępu do pliku. Zapisanie zestawu dynamicznego dysku wymaga <xref:System.Security.Permissions.FileIOPermission> przy użyciu odpowiednich flag.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Generowanie zestawów dynamicznych pochodzących z częściowo zaufanego kodu  
 Należy wziąć pod uwagę warunki, w których zestaw z uprawnieniami Internet można wygenerować zestawu przejściowego dynamiczne i wykonaj jego kod:  
  
-   Zestaw dynamiczny używa tylko typy publiczne i elementów członkowskich innych zestawów.  
  
-   Uprawnienia wymagane przez te typy i składniki znajdują się w zestawie grant częściowo zaufanym zestawie.  
  
-   Zestaw nie jest zapisywany na dysku.  
  
-   Debugowanie symbole nie zostały wygenerowane. (`Internet` i `LocalIntranet` zestawów uprawnień nie ma wystarczających uprawnień.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonimowo hostowane metody dynamiczne  
 Hostowanej anonimowo metody dynamicznej są tworzone za pomocą dwóch <xref:System.Reflection.Emit.DynamicMethod> konstruktorów, które nie określają skojarzony typ lub moduł, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> i <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Te konstruktorów umieść metod dynamicznych w zestawie dostarczane przez system, pełni zaufany, przezroczystym poziomie bezpieczeństwa. Nie uprawnienia są wymagane, użyć tych konstruktorów lub wyemitować kodu dla metod dynamicznych.  
  
 Zamiast tego podczas tworzenia hostowanej anonimowo metody dynamicznej stosu wywołań są przechwytywane. Metoda jest tworzony, żądania kontroli zabezpieczeń są wprowadzane na stosie wywołań przechwycony.  
  
> [!NOTE]
>  Koncepcyjnie żądania są wprowadzane podczas konstruowania metody. Oznacza to wymagań można się jak jest emitowany każda instrukcja MSIL. W bieżącej implementacji wszystkich potrzeb są wprowadzane podczas <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> metoda jest wywoływana lub po wywołaniu kompilatora just-in-time (JIT), jeśli metoda jest wywoływana bez wywoływania elementu <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Domeny aplikacji to dopuszczalne, hostowanej anonimowo metody dynamicznej można pominąć sprawdzanie widoczność JIT, mogą ulec następujące ograniczenia: niepubliczne typów i członków dostęp do hostowanej anonimowo metody dynamicznej musi być w zestawy, których grant ustawia są równe lub podzbiór zestawu emisji stosu wywołań. Ograniczona możliwość pominąć widoczność JIT sprawdza jest włączone, jeśli domena aplikacji daje <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi.  
  
-   Jeśli stosowana metoda używa tylko typy publiczne i elementów członkowskich, żadne uprawnienia są wymagane podczas konstruowania.  
  
-   Jeśli określono, że widoczność JIT sprawdza ma być pomijana, żądanie, które są wysyłane w przypadku metody jest tworzony obejmuje <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi wraz z zestawem grant zestawu, który zawiera niepubliczny element członkowski, który jest dostępny.  
  
 Ponieważ zestaw grant niepubliczny element członkowski jest brana pod uwagę, częściowo zaufany kod, który został udzielony <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> nie podniesienia uprawnień jego wykonując członkowie niepubliczni zaufanych zestawów.  
  
 Z innego emitowany kodu, wykonanie metody dynamicznej wymaga wszelkie uprawnienia są wymagane przez metody, które używa metody dynamicznej.  
  
 Zestaw system, który jest hostem anonimowo hostowane metody dynamiczne używa <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> modelu przezroczystości, który jest modelu przezroczystości, który był używany w programie .NET Framework, przed [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.Emit.DynamicMethod> klasy.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Generowanie anonimowo hostowane metody dynamiczne pochodzących z częściowo zaufanego kodu  
 Należy wziąć pod uwagę warunki, w których można wygenerować hostowanej anonimowo metody dynamicznej zestawu z uprawnieniami Internet i wykonaj go:  
  
-   Dynamiczne metody używa tylko typy publiczne i elementów członkowskich. Jeśli jej zestaw uprawnień zawiera <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, można użyć typów niepubliczne i elementów członkowskich zestawu grant, którego wartość jest równy lub podzbiór, grant zbiór emisji zestawu.  
  
-   Uprawnienia, które są wymagane dla wszystkich typów i członków używany przez metodę dynamicznego znajdują się w zestawie grant częściowo zaufanym zestawie.  
  
> [!NOTE]
>  Metody dynamiczne nie obsługują symboli debugowania.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Metody dynamiczne skojarzone z istniejących zestawów  
 Aby skojarzyć dynamiczna metoda z typu lub modułu w istniejącego zestawu, należy użyć dowolnego z <xref:System.Reflection.Emit.DynamicMethod> konstruktorów, które określają skojarzonego typu lub modułu. Uprawnienia, które są wymagane do wywołania konstruktorów te zmieniają się, ponieważ skojarzenie metody dynamicznej z istniejącym typem lub moduł zapewnia dostęp metody dynamicznej do niepubliczne typy i składniki:  
  
-   Dynamiczne metody, która jest skojarzona z typem ma dostęp do wszystkich elementów członkowskich tego typu, a nawet prywatne elementy członkowskie, oraz do wszystkich typów wewnętrznych i elementów członkowskich w zestawie zawiera skojarzonego typu.  
  
-   Dynamiczne metody, która jest skojarzona z modułem ma dostęp do wszystkich `internal` typy i składniki (`Friend` w języku Visual Basic `assembly` w metadane środowiska wykonawczego języka wspólnego) w module.  
  
 Ponadto można użyć konstruktora, który określa, że możliwość pominąć widoczność sprawdza kompilatora JIT. W ten sposób umożliwia dynamiczne metody dostępu do wszystkich typów i członków do wszystkich zestawów, niezależnie od poziomu dostępu.  
  
 Uprawnienia wymagane przez konstruktora uzależnione dostępu ile zdecydujesz się podać metodę dynamicznego:  
  
-   Jeśli stosowana metoda używa tylko publiczne typy i składniki i skojarzyć go z własnego typu lub własny moduł, żadne uprawnienia są wymagane.  
  
-   Jeśli określisz JIT widoczność kontroli ma być pomijana, wymaga konstruktora <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi.  
  
-   Metody dynamicznej można skojarzyć z innego typu, nawet innego typu w własny zestaw wymaga konstruktora <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagę i <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> flagi.  
  
-   Jeśli skojarzysz metody dynamicznej z typu lub modułu w innym zestawie konstruktora wymaga dwóch sytuacji: <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi wraz z zestawem grant zestawu, który zawiera inny moduł. Oznacza to, stos wywołań musi zawierać wszystkie uprawnienia w zestawie grant modułu docelowej oraz <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    >  Dla zgodności z poprzednimi wersjami, jeśli żądanie dla obiekt docelowy zestaw uprawnień oraz <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> zakończy się niepowodzeniem, zapotrzebowanie konstruktora <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> flagi.  
  
 Mimo że pod względem zestawu emisji zestawu opisano elementy na tej liście, należy pamiętać, że zapotrzebowanie będą względem stosu wywołań pełne, w tym granice domeny aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.Emit.DynamicMethod> klasy.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Generowanie metod dynamicznych pochodzących z częściowo zaufanego kodu  
  
> [!NOTE]
>  Zalecanym sposobem Generowanie metod dynamicznych pochodzących z częściowo zaufanego kodu jest użycie [anonimowo hostowane metody dynamiczne](#Anonymously_Hosted_Dynamic_Methods).  
  
 Należy wziąć pod uwagę warunki, w których można wygenerować dynamiczne metody i wykonaj go zestawu z uprawnieniami Internet:  
  
-   Metody dynamicznej jest skojarzony z modułu lub typu, który emituje go albo obejmuje zestaw uprawnień, jego <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i są skojarzone z modułu w zestawie, do którego grant zestaw jest równa lub podzbiór, grant zbiór emisji zestawu.  
  
-   Dynamiczne metody używa tylko typy publiczne i elementów członkowskich. Jeśli jej zestaw uprawnień zawiera <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> i są skojarzone z modułu w zestawie, do którego grant zestaw jest równa lub podzbiór, grant zbiór emisji zestawu, można użyć, typy i elementy członkowskie oznaczone `internal` (`Friend` w języku Visual Basic `assembly`w metadane środowiska wykonawczego języka wspólnego) w module skojarzone.  
  
-   Uprawnienia wymagane przez wszystkie typy i używany przez metodę dynamicznych elementów członkowskich są uwzględnione w zestawie grant częściowo zaufanym zestawie.  
  
-   Metody dynamicznej nie pomijać kontroli widoczność JIT.  
  
> [!NOTE]
>  Metody dynamiczne nie obsługują symboli debugowania.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Informacje o wersji  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]przezroczystość zabezpieczeń staje się domyślnego mechanizmu wymuszania i wyeliminowania zasad zabezpieczeń komputera. Zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Począwszy od [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> flaga nie jest już wymagany podczas emitowanie dynamicznych zestawów i metod dynamicznych. Ta flaga jest wymagane we wszystkich wcześniejszych wersjach [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  <xref:System.Security.Permissions.ReflectionPermission>z <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> flaga jest domyślnie włączone w `FullTrust` i `LocalIntranet` ustawia uprawnienia nazwanego, ale nie w `Internet` zestaw uprawnień. W związku z tym w starszych wersjach [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], biblioteki mogą być używane z Internetu uprawnienia tylko w przypadku wykonywania <xref:System.Security.PermissionSet.Assert%2A> dla <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Takie biblioteki wymagają przeglądu zabezpieczeń zachować ostrożność, ponieważ błędy kodowania może skutkować luk w zabezpieczeniach. [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] Umożliwia kod, aby emitować w scenariuszach częściowo zaufanych bez wystawiania wszystkie żądania kontroli zabezpieczeń, ponieważ generowanie kodu nie jest z założenia uprzywilejowanych operacji. Oznacza to, że wygenerowany kod nie ma więcej uprawnień niż zestaw, który emituje go. Dzięki temu biblioteki, w których Emituj kod jest przezroczysta pod względem zabezpieczeń i eliminuje potrzebę do potwierdzenia <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, który upraszcza zapisywanie bezpiecznego biblioteki.  
  
 Ponadto [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] wprowadza <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi do uzyskiwania dostępu do niepubliczne typy i składniki z częściowo zaufanego metod dynamicznych. Starsze niż [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wymagają <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagę dla metod dynamicznych, których dostęp niepubliczne typy i składniki; to uprawnienia, które nigdy nie może być przyznany elementowi częściowo zaufany kod.  
  
 Na koniec [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] wprowadza hostowanej anonimowo metody.  
  
### <a name="obtaining-information-on-types-and-members"></a>Uzyskiwanie informacji dotyczących typów i członków  
 Począwszy od [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], aby uzyskać informacje o niepubliczne typy i składniki są wymagane żadne uprawnienia. Odbicie służy do uzyskiwania informacji potrzebnych do emitowanie metod dynamicznych. Na przykład <xref:System.Reflection.MethodInfo> obiekty służą do emisji wywołania metody. Starsze niż [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wymagają <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> flagi. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń dla odbicia](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zagadnienia dotyczące zabezpieczeń dla odbicia](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)  
 [Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)
