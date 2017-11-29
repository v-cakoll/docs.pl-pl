---
title: "Zgodność i migracja zasad zabezpieczenia dostępu kodu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29e81f5e83bc3cbf9467c7940ba6acfd0a8c99b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Zgodność i migracja zasad zabezpieczenia dostępu kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Część zasad zabezpieczeń dostępu kodu (CAS) wprowadzono przestarzałe w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. W związku z tym można napotkać ostrzeżenia dotyczące kompilacji i obsługi wyjątków można wywołać zasad przestarzałe typy i składniki [jawnie](#explicit_use) lub [niejawnie](#implicit_use) (za pośrednictwem innych typów i członków).  
  
 Ostrzeżenia i błędy można uniknąć przez:  
  
-   [Migrowanie](#migration) do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zastępujące przestarzałe wywołania.  
  
     \-lub -  
  
-   Przy użyciu [element konfiguracji < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) do uczestnictwa w starszej wersji zachowania zasad CAS.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Użyj jawnego](#explicit_use)  
  
-   [Użycia niejawnego](#implicit_use)  
  
-   [Błędy i ostrzeżenia](#errors_and_warnings)  
  
-   [Migracji: Zastępuje przestarzałe wywołania](#migration)  
  
-   [Zgodność: Przy użyciu opcji starsza wersja zasad CAS](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a>Użyj jawnego  
 Elementy członkowskie, które bezpośrednio manipulować zasady zabezpieczeń i wymagają zasad CAS ją w piaskownicy są przestarzałe i powodują błędy domyślnie.  
  
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
 Kilka ładowania zestawu overloads produktu błędy z powodu ich użycia niejawnego zasad CAS. Te przeciążenia zająć <xref:System.Security.Policy.Evidence> zestaw dla zestawu uprawnień parametr, który jest używany do rozpoznania zasad CAS i podać uprawnienia.  
  
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
 Przestarzałe typy i składniki należy utworzyć następujące komunikaty o błędach, gdy są one używane. Należy pamiętać, że <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> samego typu nie jest przestarzały.  
  
 Ostrzeżenie kompilacji:  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 Wyjątek czasu wykonywania:  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a>Migracji: Zastępuje przestarzałe wywołania  
  
### <a name="determining-an-assemblys-trust-level"></a>Określanie poziomu zaufania zestawu  
 Urzędy certyfikacji zasad jest często używany do określenia zestawu lub w domenie aplikacji uprawnienia zestaw uprawnień lub poziom zaufania. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Udostępnia następujące właściwości przydatne, które nie trzeba rozwiązać zasady zabezpieczeń:  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a>Sandboxing domeny aplikacji  
 <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Metoda jest zwykle używane do sandboxing zestawów w domenie aplikacji. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Udostępnia elementy członkowskie, które nie mają być <xref:System.Security.Policy.PolicyLevel> w tym celu. Aby uzyskać więcej informacji, zobacz [porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Określanie bezpiecznych lub uzasadnione uprawnienia ustawione dla częściowo zaufany kod  
 Hosty często muszą określić uprawnienia, które są odpowiednie dla kodu sandboxing hostowanej. Przed [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zasad CAS podać sposób, w tym z <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metody. Jako serwer zamienny [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zapewnia <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metody, która zwraca zestaw udostępnionego dowodu uprawnień bezpieczne, standard.  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Scenariusze z systemem innym niż Sandboxing: Przeciążenia dla Załadowań zestawów  
 Powód użycia przepełnienia obciążenia zestawu może być używania parametrów, które nie są dostępne, zamiast sandboxing zestawu. Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zestawu obciążenia przeciążeń, które nie wymagają <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> obiektu jako parametru, na przykład <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, realizacji tego scenariusza.  
  
 Jeśli chcesz piaskownicy zestawu, użyj <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia.  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Zgodność: Przy użyciu opcji starsza wersja zasad CAS  
 [Element konfiguracji < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) pozwala określić, że proces lub biblioteka używa starszej wersji zasad CAS. Po włączeniu tego elementu przeciążeń zasad i dokumenty będą działać tak samo jak w poprzednich wersjach platformy.  
  
> [!NOTE]
>  Urzędy certyfikacji zasad zachowania został określony na podstawie wersji środowiska wykonawczego, modyfikowanie zasad CAS dla jednej wersji środowiska uruchomieniowego nie wpływa na zasady CAS w innej wersji.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
