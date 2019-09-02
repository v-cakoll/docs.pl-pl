---
title: Zgodność i migracja zasad zabezpieczenia dostępu kodu
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9563dae9ba5d144300549e7f33f5f5a9feb1d410
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205630"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Zgodność i migracja zasad zabezpieczenia dostępu kodu

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Część zasad zabezpieczeń dostępu kodu (CAS) była przestarzała w .NET Framework 4. W związku z tym mogą wystąpić ostrzeżenia kompilacji i wyjątki czasu wykonywania w przypadku wywołania przestarzałych typów zasad i elementów członkowskich [jawnie](#explicit_use) lub niejawnie (za pomocą innych typów i elementów członkowskich). [](#implicit_use)

Ostrzeżenia i błędy można uniknąć:

- [Migrowanie](#migration) do .NET Framework 4 zamienników dla przestarzałych wywołań.

   \- lub —

- Użyj [elementu konfiguracji > NetFx40_LegacySecurityPolicy,abyzrezygnowaćzestarszejwersjizasadCAS.\<](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)

Ten temat zawiera następujące sekcje:

- [Jawne użycie](#explicit_use)

- [Niejawne użycie](#implicit_use)

- [Błędy i ostrzeżenia](#errors_and_warnings)

- [Migracji Zastępowanie dla przestarzałych wywołań](#migration)

- [Zgodna Korzystanie z opcji starszej wersji zasad CAS](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a>Jawne użycie

Elementy członkowskie, które bezpośrednio manipulują zasadami zabezpieczeń lub wymagają zasad CAS do piaskownicy, są przestarzałe i domyślnie generują błędy.

Przykłady są następujące:

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a>Niejawne użycie

Niektóre przeciążenia ładowania zestawów generują błędy ze względu na niejawne użycie zasad CAS. Te przeciążenia mają <xref:System.Security.Policy.Evidence> parametr, który jest używany do rozpoznawania zasad CAS i zapewniają zestaw uprawnień dla zestawu.

Oto kilka przykładów. Przestarzałe przeciążenia to te, które <xref:System.Security.Policy.Evidence> przyjmują jako parametr:

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia

Przestarzałe typy i elementy członkowskie generują następujące komunikaty o błędach, gdy są używane. Należy pamiętać, <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> że sam typ nie jest przestarzały.

Ostrzeżenie czasu kompilacji:

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

Wyjątek czasu wykonywania:

<xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a>Migracji Zastępowanie dla przestarzałych wywołań

### <a name="determining-an-assemblys-trust-level"></a>Określanie poziomu zaufania zestawu

Zasady urzędów certyfikacji są często używane do określania uprawnień do zestawu lub poziomu zaufania domeny aplikacji. .NET Framework 4 uwidacznia następujące przydatne właściwości, które nie muszą rozwiązywać zasad zabezpieczeń:

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a>Tryb piaskownicy domeny aplikacji

Metoda <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> ta jest zwykle używana do wypełniania zestawów w domenie aplikacji. .NET Framework 4 uwidacznia składowe, które nie muszą być używane <xref:System.Security.Policy.PolicyLevel> do tego celu. Aby uzyskać więcej informacji, zobacz [jak: Uruchom częściowo zaufany kod w piaskownicy](how-to-run-partially-trusted-code-in-a-sandbox.md).

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Określanie bezpiecznego lub uzasadnionego zestawu uprawnień dla częściowo zaufanego kodu

Hosty często muszą określić uprawnienia, które są odpowiednie dla hostowanego kodu w trybie piaskownicy. Przed przystąpieniem do .NET Framework 4 zasady urzędów certyfikacji udostępniają <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metodę. Jako zamiennik, .NET Framework 4 udostępnia <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metodę, która zwraca bezpieczny, standardowy zestaw uprawnień dla dostarczonych dowodów.

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Scenariusze spoza piaskownicy: Przeciążenia dla obciążeń zestawów

Przyczyną użycia przeciążenia ładowania zestawu może być użycie parametrów, które nie są dostępne w inny sposób, zamiast w piaskownicy zestawu. Począwszy od .NET Framework 4, przeciążenia ładowania zestawów, które nie wymagają <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> obiektu jako parametru, na <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>przykład, Włącz ten scenariusz.

Jeśli chcesz piaskownicy zestawu, użyj <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia.

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Zgodna Korzystanie z opcji starszej wersji zasad CAS

[Element konfiguracji > NetFx40_LegacySecurityPolicyumożliwiaokreślenie,żeproceslubbibliotekakorzystazestarszychzasadCAS.\<](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) Po włączeniu tego elementu przeciążenia zasad i dowodów będą działały tak, jak w poprzednich wersjach platformy.

> [!NOTE]
> Zachowanie zasad CAS jest określone w wersji środowiska uruchomieniowego, więc modyfikowanie zasad CAS dla jednej wersji środowiska uruchomieniowego nie ma wpływu na zasady CAS innej wersji.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
