---
title: Zgodność i migracja zasad zabezpieczenia dostępu kodu
description: Zapoznaj się z podsumowaniem i zobacz linki dotyczące zgodności i migracji zasad zabezpieczeń w programie .NET 4.
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: e5affd9d16635fa28342b5b7390a083185975f2b
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281735"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Zgodność i migracja zasad zabezpieczenia dostępu kodu

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Część zasad zabezpieczeń dostępu kodu (CAS) była przestarzała w .NET Framework 4. W związku z tym mogą wystąpić ostrzeżenia kompilacji i wyjątki czasu wykonywania w przypadku wywołania przestarzałych typów zasad i elementów członkowskich [jawnie](#explicit_use) lub [niejawnie](#implicit_use) (za pomocą innych typów i elementów członkowskich).

Ostrzeżenia i błędy można uniknąć:

- [Migrowanie](#migration) do .NET Framework 4 zamienników dla przestarzałych wywołań.

   \-oraz

- Korzystanie z [ \<NetFx40_LegacySecurityPolicy> elementu konfiguracji](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) w celu wyboru zgodności ze starszymi zasadami CAS.

Ten temat zawiera następujące sekcje:

- [Jawne użycie](#explicit_use)

- [Niejawne użycie](#implicit_use)

- [Błędy i ostrzeżenia](#errors_and_warnings)

- [Migracja: zastępowanie dla przestarzałych wywołań](#migration)

- [Zgodność: korzystanie z opcji starszej wersji zasad CAS](#compatibility)

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

Oto kilka przykładów. Przestarzałe przeciążenia to te, które przyjmują <xref:System.Security.Policy.Evidence> jako parametr:

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

Przestarzałe typy i elementy członkowskie generują następujące komunikaty o błędach, gdy są używane. Należy pamiętać, że <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> sam typ nie jest przestarzały.

Ostrzeżenie czasu kompilacji:

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

Wyjątek czasu wykonywania:

<xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a>Migracja: zastępowanie dla przestarzałych wywołań

### <a name="determining-an-assemblys-trust-level"></a>Określanie poziomu zaufania zestawu

Zasady urzędów certyfikacji są często używane do określania uprawnień do zestawu lub poziomu zaufania domeny aplikacji. .NET Framework 4 uwidacznia następujące przydatne właściwości, które nie muszą rozwiązywać zasad zabezpieczeń:

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a>Tryb piaskownicy domeny aplikacji

<xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>Metoda ta jest zwykle używana do wypełniania zestawów w domenie aplikacji. .NET Framework 4 uwidacznia składowe, które nie muszą być używane <xref:System.Security.Policy.PolicyLevel> do tego celu. Aby uzyskać więcej informacji, zobacz [jak: uruchamiać częściowo zaufany kod w piaskownicy](how-to-run-partially-trusted-code-in-a-sandbox.md).

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Określanie bezpiecznego lub uzasadnionego zestawu uprawnień dla częściowo zaufanego kodu

Hosty często muszą określić uprawnienia, które są odpowiednie dla hostowanego kodu w trybie piaskownicy. Przed przystąpieniem do .NET Framework 4 zasady urzędów certyfikacji udostępniają <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metodę. Jako zamiennik, .NET Framework 4 udostępnia <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metodę, która zwraca bezpieczny, standardowy zestaw uprawnień dla dostarczonych dowodów.

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Scenariusze spoza piaskownicy: przeciążenia dla obciążeń zestawu

Przyczyną użycia przeciążenia ładowania zestawu może być użycie parametrów, które nie są dostępne w inny sposób, zamiast w piaskownicy zestawu. Począwszy od .NET Framework 4, przeciążenia ładowania zestawów, które nie wymagają <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> obiektu jako parametru, na przykład, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType> Włącz ten scenariusz.

Jeśli chcesz piaskownicy zestawu, użyj <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia.

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Zgodność: korzystanie z opcji starszej wersji zasad CAS

[ \<NetFx40_LegacySecurityPolicy> Element Configuration](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) pozwala określić, że proces lub biblioteka korzysta ze starszych zasad CAS. Po włączeniu tego elementu przeciążenia zasad i dowodów będą działały tak, jak w poprzednich wersjach platformy.

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

- [Porady: uruchamianie częściowo zaufanego kodu w bibliotece](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
