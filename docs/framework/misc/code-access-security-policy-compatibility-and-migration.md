---
title: Zgodność i migracja zasad zabezpieczenia dostępu kodu
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5007e07340621fa76dc37a48eaf8c17bc048339
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="9fa86-102">Zgodność i migracja zasad zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="9fa86-102">Code Access Security Policy Compatibility and Migration</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="9fa86-103">Część zasad zabezpieczeń dostępu kodu (CAS) wprowadzono przestarzałe w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa86-103">The policy portion of code access security (CAS) has been made obsolete in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="9fa86-104">W związku z tym można napotkać ostrzeżenia dotyczące kompilacji i obsługi wyjątków można wywołać zasad przestarzałe typy i składniki [jawnie](#explicit_use) lub [niejawnie](#implicit_use) (za pośrednictwem innych typów i członków).</span><span class="sxs-lookup"><span data-stu-id="9fa86-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>  
  
 <span data-ttu-id="9fa86-105">Ostrzeżenia i błędy można uniknąć przez:</span><span class="sxs-lookup"><span data-stu-id="9fa86-105">You can avoid the warnings and errors by either:</span></span>  
  
-   <span data-ttu-id="9fa86-106">[Migrowanie](#migration) do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zastępujące przestarzałe wywołania.</span><span class="sxs-lookup"><span data-stu-id="9fa86-106">[Migrating](#migration) to the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] replacements for the obsolete calls.</span></span>  
  
     <span data-ttu-id="9fa86-107">\- lub -</span><span class="sxs-lookup"><span data-stu-id="9fa86-107">\- or -</span></span>  
  
-   <span data-ttu-id="9fa86-108">Przy użyciu [element konfiguracji < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) do uczestnictwa w starszej wersji zachowania zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="9fa86-108">Using the [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>  
  
 <span data-ttu-id="9fa86-109">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="9fa86-109">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="9fa86-110">Użyj jawnego</span><span class="sxs-lookup"><span data-stu-id="9fa86-110">Explicit Use</span></span>](#explicit_use)  
  
-   [<span data-ttu-id="9fa86-111">Użycia niejawnego</span><span class="sxs-lookup"><span data-stu-id="9fa86-111">Implicit Use</span></span>](#implicit_use)  
  
-   [<span data-ttu-id="9fa86-112">Błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="9fa86-112">Errors and Warnings</span></span>](#errors_and_warnings)  
  
-   [<span data-ttu-id="9fa86-113">Migracji: Zastępuje przestarzałe wywołania</span><span class="sxs-lookup"><span data-stu-id="9fa86-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)  
  
-   [<span data-ttu-id="9fa86-114">Zgodność: Przy użyciu opcji starsza wersja zasad CAS</span><span class="sxs-lookup"><span data-stu-id="9fa86-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a><span data-ttu-id="9fa86-115">Użyj jawnego</span><span class="sxs-lookup"><span data-stu-id="9fa86-115">Explicit Use</span></span>  
 <span data-ttu-id="9fa86-116">Elementy członkowskie, które bezpośrednio manipulować zasady zabezpieczeń i wymagają zasad CAS ją w piaskownicy są przestarzałe i powodują błędy domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9fa86-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>  
  
 <span data-ttu-id="9fa86-117">Przykładem tego są:</span><span class="sxs-lookup"><span data-stu-id="9fa86-117">Examples of these are:</span></span>  
  
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
## <a name="implicit-use"></a><span data-ttu-id="9fa86-118">Użycia niejawnego</span><span class="sxs-lookup"><span data-stu-id="9fa86-118">Implicit Use</span></span>  
 <span data-ttu-id="9fa86-119">Kilka ładowania zestawu overloads produktu błędy z powodu ich użycia niejawnego zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="9fa86-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="9fa86-120">Te przeciążenia zająć <xref:System.Security.Policy.Evidence> zestaw dla zestawu uprawnień parametr, który jest używany do rozpoznania zasad CAS i podać uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="9fa86-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>  
  
 <span data-ttu-id="9fa86-121">Oto kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="9fa86-121">Here are some examples.</span></span> <span data-ttu-id="9fa86-122">Przestarzałe przeciążenia są tymi, które przyjmują <xref:System.Security.Policy.Evidence> jako parametr:</span><span class="sxs-lookup"><span data-stu-id="9fa86-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>  
  
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
## <a name="errors-and-warnings"></a><span data-ttu-id="9fa86-123">Błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="9fa86-123">Errors and Warnings</span></span>  
 <span data-ttu-id="9fa86-124">Przestarzałe typy i składniki należy utworzyć następujące komunikaty o błędach, gdy są one używane.</span><span class="sxs-lookup"><span data-stu-id="9fa86-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="9fa86-125">Należy pamiętać, że <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> samego typu nie jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="9fa86-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>  
  
 <span data-ttu-id="9fa86-126">Ostrzeżenie kompilacji:</span><span class="sxs-lookup"><span data-stu-id="9fa86-126">Compile-time warning:</span></span>  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 <span data-ttu-id="9fa86-127">Wyjątek czasu wykonywania:</span><span class="sxs-lookup"><span data-stu-id="9fa86-127">Run-time exception:</span></span>  
  
 <span data-ttu-id="9fa86-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="9fa86-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="9fa86-129">Migracji: Zastępuje przestarzałe wywołania</span><span class="sxs-lookup"><span data-stu-id="9fa86-129">Migration: Replacement for Obsolete Calls</span></span>  
  
### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="9fa86-130">Określanie poziomu zaufania zestawu</span><span class="sxs-lookup"><span data-stu-id="9fa86-130">Determining an Assembly’s Trust Level</span></span>  
 <span data-ttu-id="9fa86-131">Urzędy certyfikacji zasad jest często używany do określenia zestawu lub w domenie aplikacji uprawnienia zestaw uprawnień lub poziom zaufania.</span><span class="sxs-lookup"><span data-stu-id="9fa86-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="9fa86-132">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Udostępnia następujące właściwości przydatne, które nie trzeba rozwiązać zasady zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="9fa86-132">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes the following useful properties that do not need to resolve security policy:</span></span>  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a><span data-ttu-id="9fa86-133">Sandboxing domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="9fa86-133">Application Domain Sandboxing</span></span>  
 <span data-ttu-id="9fa86-134"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Metoda jest zwykle używane do sandboxing zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9fa86-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="9fa86-135">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Udostępnia elementy członkowskie, które nie mają być <xref:System.Security.Policy.PolicyLevel> w tym celu.</span><span class="sxs-lookup"><span data-stu-id="9fa86-135">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="9fa86-136">Aby uzyskać więcej informacji, zobacz [porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="9fa86-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="9fa86-137">Określanie bezpiecznych lub uzasadnione uprawnienia ustawione dla częściowo zaufany kod</span><span class="sxs-lookup"><span data-stu-id="9fa86-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>  
 <span data-ttu-id="9fa86-138">Hosty często muszą określić uprawnienia, które są odpowiednie dla kodu sandboxing hostowanej.</span><span class="sxs-lookup"><span data-stu-id="9fa86-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="9fa86-139">Przed [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zasad CAS podać sposób, w tym z <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9fa86-139">Before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9fa86-140">Jako serwer zamienny [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zapewnia <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metody, która zwraca zestaw udostępnionego dowodu uprawnień bezpieczne, standard.</span><span class="sxs-lookup"><span data-stu-id="9fa86-140">As a replacement, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="9fa86-141">Scenariusze z systemem innym niż Sandboxing: Przeciążenia dla Załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="9fa86-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>  
 <span data-ttu-id="9fa86-142">Powód użycia przepełnienia obciążenia zestawu może być używania parametrów, które nie są dostępne, zamiast sandboxing zestawu.</span><span class="sxs-lookup"><span data-stu-id="9fa86-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="9fa86-143">Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zestawu obciążenia przeciążeń, które nie wymagają <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> obiektu jako parametru, na przykład <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, realizacji tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="9fa86-143">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>  
  
 <span data-ttu-id="9fa86-144">Jeśli chcesz piaskownicy zestawu, użyj <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="9fa86-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="9fa86-145">Zgodność: Przy użyciu opcji starsza wersja zasad CAS</span><span class="sxs-lookup"><span data-stu-id="9fa86-145">Compatibility: Using the CAS Policy Legacy Option</span></span>  
 <span data-ttu-id="9fa86-146">[Element konfiguracji < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) pozwala określić, że proces lub biblioteka używa starszej wersji zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="9fa86-146">The [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="9fa86-147">Po włączeniu tego elementu przeciążeń zasad i dokumenty będą działać tak samo jak w poprzednich wersjach platformy.</span><span class="sxs-lookup"><span data-stu-id="9fa86-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fa86-148">Urzędy certyfikacji zasad zachowania został określony na podstawie wersji środowiska wykonawczego, modyfikowanie zasad CAS dla jednej wersji środowiska uruchomieniowego nie wpływa na zasady CAS w innej wersji.</span><span class="sxs-lookup"><span data-stu-id="9fa86-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fa86-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fa86-149">See Also</span></span>  
 [<span data-ttu-id="9fa86-150">Porady: uruchamianie częściowo zaufanego kodu w bibliotece</span><span class="sxs-lookup"><span data-stu-id="9fa86-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [<span data-ttu-id="9fa86-151">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="9fa86-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
