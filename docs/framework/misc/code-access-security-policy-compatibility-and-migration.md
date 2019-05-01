---
title: Zgodność i migracja zasad zabezpieczenia dostępu kodu
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d9281e52de43391a92262f85084715ccabd5515
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868917"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="74b20-102">Zgodność i migracja zasad zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="74b20-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="74b20-103">Części zasad zabezpieczenia dostępu kodu (CAS) zostały ustawione jako przestarzałe w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74b20-103">The policy portion of code access security (CAS) has been made obsolete in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="74b20-104">W rezultacie mogą wystąpić ostrzeżenia kompilacji i wyjątki środowiska uruchomieniowego wywołanie zasad przestarzałych typów i członków [jawnie](#explicit_use) lub [niejawnie](#implicit_use) (za pośrednictwem innych typów i elementów członkowskich).</span><span class="sxs-lookup"><span data-stu-id="74b20-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="74b20-105">Ostrzeżenia i błędy można uniknąć przez:</span><span class="sxs-lookup"><span data-stu-id="74b20-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="74b20-106">[Migrowanie](#migration) do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zamiany wywołania przestarzały.</span><span class="sxs-lookup"><span data-stu-id="74b20-106">[Migrating](#migration) to the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] replacements for the obsolete calls.</span></span>

   <span data-ttu-id="74b20-107">\- lub —</span><span class="sxs-lookup"><span data-stu-id="74b20-107">\- or -</span></span>

- <span data-ttu-id="74b20-108">Za pomocą [element konfiguracji < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) do dołączenia do starsze zachowanie zasady CAS.</span><span class="sxs-lookup"><span data-stu-id="74b20-108">Using the [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="74b20-109">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="74b20-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="74b20-110">Użyj jawnego</span><span class="sxs-lookup"><span data-stu-id="74b20-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="74b20-111">Użycia niejawnego</span><span class="sxs-lookup"><span data-stu-id="74b20-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="74b20-112">Błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="74b20-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="74b20-113">Migracja: Zastąpienie dla wywołań przestarzałe</span><span class="sxs-lookup"><span data-stu-id="74b20-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="74b20-114">Zgodność: Za pomocą opcji starsza wersja zasady CAS</span><span class="sxs-lookup"><span data-stu-id="74b20-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="74b20-115">Użyj jawnego</span><span class="sxs-lookup"><span data-stu-id="74b20-115">Explicit Use</span></span>

<span data-ttu-id="74b20-116">Elementy członkowskie, które bezpośrednio modyfikować zasady zabezpieczeń lub zasady CAS ją w piaskownicy są przestarzałe i generuje błędy domyślnie.</span><span class="sxs-lookup"><span data-stu-id="74b20-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="74b20-117">Przykładem tego są:</span><span class="sxs-lookup"><span data-stu-id="74b20-117">Examples of these are:</span></span>

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

## <a name="implicit-use"></a><span data-ttu-id="74b20-118">Użycia niejawnego</span><span class="sxs-lookup"><span data-stu-id="74b20-118">Implicit Use</span></span>

<span data-ttu-id="74b20-119">Ładowanie zestawu kilka przeciążeń błędów produktu ze względu na ich użycie niejawnej urzędów certyfikacji zasad.</span><span class="sxs-lookup"><span data-stu-id="74b20-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="74b20-120">Wykonaj te przeciążenia <xref:System.Security.Policy.Evidence> parametr służący do rozwiązywania zasady CAS i podaj uprawnienia udzielić zestawu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="74b20-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="74b20-121">Oto kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="74b20-121">Here are some examples.</span></span> <span data-ttu-id="74b20-122">Przestarzałe przeciążenia są tymi, które przyjmują <xref:System.Security.Policy.Evidence> jako parametr:</span><span class="sxs-lookup"><span data-stu-id="74b20-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

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

## <a name="errors-and-warnings"></a><span data-ttu-id="74b20-123">Błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="74b20-123">Errors and Warnings</span></span>

<span data-ttu-id="74b20-124">Przestarzałe typy i członków generuje następujące komunikaty o błędach, gdy są one używane.</span><span class="sxs-lookup"><span data-stu-id="74b20-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="74b20-125">Należy pamiętać, że <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> samego typu nie jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="74b20-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="74b20-126">Ostrzeżenie kompilacji:</span><span class="sxs-lookup"><span data-stu-id="74b20-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="74b20-127">Wyjątek czasu wykonywania:</span><span class="sxs-lookup"><span data-stu-id="74b20-127">Run-time exception:</span></span>

<span data-ttu-id="74b20-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="74b20-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="74b20-129">Migracja: Zastąpienie dla wywołań przestarzałe</span><span class="sxs-lookup"><span data-stu-id="74b20-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="74b20-130">Określanie poziom zaufania zestawu</span><span class="sxs-lookup"><span data-stu-id="74b20-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="74b20-131">Urzędy certyfikacji zasad jest często używany do określenia zestawu lub uprawnienie domeny aplikacji zestaw uprawnień lub poziom zaufania.</span><span class="sxs-lookup"><span data-stu-id="74b20-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="74b20-132">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Udostępnia następujące właściwości przydatne, które nie powinny być rozwiązać zasady zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="74b20-132">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="74b20-133">Tryb piaskownicy domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="74b20-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="74b20-134"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Metoda jest zwykle używane dla piaskownicy zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="74b20-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="74b20-135">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Uwidacznia elementy członkowskie, które nie mają używać <xref:System.Security.Policy.PolicyLevel> do tego celu.</span><span class="sxs-lookup"><span data-stu-id="74b20-135">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="74b20-136">Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie częściowo zaufanego kodu w piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="74b20-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="74b20-137">Określanie bezpieczny lub uzasadnione dla ustawione uprawnienie częściowo zaufanego kodu</span><span class="sxs-lookup"><span data-stu-id="74b20-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="74b20-138">Hosty często trzeba określić uprawnienia, które są odpowiednie dla kodu w piaskownicy hostowanej.</span><span class="sxs-lookup"><span data-stu-id="74b20-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="74b20-139">Przed [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zasady CAS podany sposób, aby zrobić to za pomocą <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="74b20-139">Before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="74b20-140">W zastępstwie [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zapewnia <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metody, która zwraca bezpieczną, standardowe zestawu uprawnień dla podanego dowodów.</span><span class="sxs-lookup"><span data-stu-id="74b20-140">As a replacement, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="74b20-141">Scenariusze bez piaskownicy: Przeciążenia Załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="74b20-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="74b20-142">Przyczyna za pomocą przeciążenia ładowania zestawu może być korzystanie z parametrów, które nie są dostępne, zamiast piaskownicy zestawu.</span><span class="sxs-lookup"><span data-stu-id="74b20-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="74b20-143">Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zestawu obciążenia przeciążenia, które nie wymagają <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> obiektu jako parametr, na przykład <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, realizacji tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="74b20-143">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="74b20-144">Jeśli chcesz piaskownicy zestawu, należy użyć <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="74b20-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="74b20-145">Zgodność: Za pomocą opcji starsza wersja zasady CAS</span><span class="sxs-lookup"><span data-stu-id="74b20-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="74b20-146">[Element konfiguracji < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) pozwala określić, że proces lub biblioteki używa starsza zasada CAS.</span><span class="sxs-lookup"><span data-stu-id="74b20-146">The [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="74b20-147">Po włączeniu tego elementu, zasad i dowody przeciążenia będzie działać tak samo, jak w poprzednich wersjach programu framework.</span><span class="sxs-lookup"><span data-stu-id="74b20-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="74b20-148">Urzędów certyfikacji zasad zachowanie jest określone na podstawie wersji środowiska uruchomieniowego, więc modyfikowanie zasad urzędów certyfikacji dla jednej wersji środowiska uruchomieniowego nie wpływa na zasady CAS w innej wersji.</span><span class="sxs-lookup"><span data-stu-id="74b20-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="74b20-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74b20-149">See also</span></span>

- [<span data-ttu-id="74b20-150">Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy</span><span class="sxs-lookup"><span data-stu-id="74b20-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="74b20-151">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="74b20-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
