---
title: Zgodność i migracja zasad zabezpieczenia dostępu kodu
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 219b511662a2e59fb6e0e55b6630bd54015fcc79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620100"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Zgodność i migracja zasad zabezpieczenia dostępu kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Części zasad zabezpieczenia dostępu kodu (CAS) zostały ustawione jako przestarzałe w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. W rezultacie mogą wystąpić ostrzeżenia kompilacji i wyjątki środowiska uruchomieniowego wywołanie zasad przestarzałych typów i członków [jawnie](#explicit_use) lub [niejawnie](#implicit_use) (za pośrednictwem innych typów i elementów członkowskich).  
  
 Ostrzeżenia i błędy można uniknąć przez:  
  
-   [Migrowanie](#migration) do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zamiany wywołania przestarzały.  
  
     \- lub —  
  
-   Za pomocą [element konfiguracji < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) do dołączenia do starsze zachowanie zasady CAS.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Użyj jawnego](#explicit_use)  
  
-   [Użycia niejawnego](#implicit_use)  
  
-   [Błędy i ostrzeżenia](#errors_and_warnings)  
  
-   [Migracja: Zastąpienie dla wywołań przestarzałe](#migration)  
  
-   [Zgodność: Za pomocą opcji starsza wersja zasady CAS](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a>Użyj jawnego  
 Elementy członkowskie, które bezpośrednio modyfikować zasady zabezpieczeń lub zasady CAS ją w piaskownicy są przestarzałe i generuje błędy domyślnie.  
  
 Przykładem tego są:  
  
-   <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>  
  
<a name="implicit_use"></a>   
## <a name="implicit-use"></a>Użycia niejawnego  
 Ładowanie zestawu kilka przeciążeń błędów produktu ze względu na ich użycie niejawnej urzędów certyfikacji zasad. Wykonaj te przeciążenia <xref:System.Security.Policy.Evidence> parametr służący do rozwiązywania zasady CAS i podaj uprawnienia udzielić zestawu dla zestawu.  
  
 Oto kilka przykładów. Przestarzałe przeciążenia są tymi, które przyjmują <xref:System.Security.Policy.Evidence> jako parametr:  
  
-   <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
<a name="errors_and_warnings"></a>   
## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia  
 Przestarzałe typy i członków generuje następujące komunikaty o błędach, gdy są one używane. Należy pamiętać, że <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> samego typu nie jest przestarzały.  
  
 Ostrzeżenie kompilacji:  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 Wyjątek czasu wykonywania:  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a>Migracja: Zastąpienie dla wywołań przestarzałe  
  
### <a name="determining-an-assemblys-trust-level"></a>Określanie poziom zaufania zestawu  
 Urzędy certyfikacji zasad jest często używany do określenia zestawu lub uprawnienie domeny aplikacji zestaw uprawnień lub poziom zaufania. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Udostępnia następujące właściwości przydatne, które nie powinny być rozwiązać zasady zabezpieczeń:  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a>Tryb piaskownicy domeny aplikacji  
 <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Metoda jest zwykle używane dla piaskownicy zestawów w domenie aplikacji. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Uwidacznia elementy członkowskie, które nie mają używać <xref:System.Security.Policy.PolicyLevel> do tego celu. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie częściowo zaufanego kodu w piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Określanie bezpieczny lub uzasadnione dla ustawione uprawnienie częściowo zaufanego kodu  
 Hosty często trzeba określić uprawnienia, które są odpowiednie dla kodu w piaskownicy hostowanej. Przed [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zasady CAS podany sposób, aby zrobić to za pomocą <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metody. W zastępstwie [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zapewnia <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metody, która zwraca bezpieczną, standardowe zestawu uprawnień dla podanego dowodów.  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Scenariusze bez piaskownicy: Przeciążenia Załadowań zestawów  
 Przyczyna za pomocą przeciążenia ładowania zestawu może być korzystanie z parametrów, które nie są dostępne, zamiast piaskownicy zestawu. Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zestawu obciążenia przeciążenia, które nie wymagają <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> obiektu jako parametr, na przykład <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, realizacji tego scenariusza.  
  
 Jeśli chcesz piaskownicy zestawu, należy użyć <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia.  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Zgodność: Za pomocą opcji starsza wersja zasady CAS  
 [Element konfiguracji < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) pozwala określić, że proces lub biblioteki używa starsza zasada CAS. Po włączeniu tego elementu, zasad i dowody przeciążenia będzie działać tak samo, jak w poprzednich wersjach programu framework.  
  
> [!NOTE]
>  Urzędów certyfikacji zasad zachowanie jest określone na podstawie wersji środowiska uruchomieniowego, więc modyfikowanie zasad urzędów certyfikacji dla jednej wersji środowiska uruchomieniowego nie wpływa na zasady CAS w innej wersji.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
