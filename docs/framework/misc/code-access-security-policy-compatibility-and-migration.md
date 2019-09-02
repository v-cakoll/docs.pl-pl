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
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="1442f-102">Zgodność i migracja zasad zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="1442f-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="1442f-103">Część zasad zabezpieczeń dostępu kodu (CAS) była przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1442f-103">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="1442f-104">W związku z tym mogą wystąpić ostrzeżenia kompilacji i wyjątki czasu wykonywania w przypadku wywołania przestarzałych typów zasad i elementów członkowskich [jawnie](#explicit_use) lub niejawnie (za pomocą innych typów i elementów członkowskich). [](#implicit_use)</span><span class="sxs-lookup"><span data-stu-id="1442f-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="1442f-105">Ostrzeżenia i błędy można uniknąć:</span><span class="sxs-lookup"><span data-stu-id="1442f-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="1442f-106">[Migrowanie](#migration) do .NET Framework 4 zamienników dla przestarzałych wywołań.</span><span class="sxs-lookup"><span data-stu-id="1442f-106">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="1442f-107">\- lub —</span><span class="sxs-lookup"><span data-stu-id="1442f-107">\- or -</span></span>

- <span data-ttu-id="1442f-108">Użyj [elementu konfiguracji > NetFx40_LegacySecurityPolicy,abyzrezygnowaćzestarszejwersjizasadCAS.\<](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)</span><span class="sxs-lookup"><span data-stu-id="1442f-108">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="1442f-109">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="1442f-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="1442f-110">Jawne użycie</span><span class="sxs-lookup"><span data-stu-id="1442f-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="1442f-111">Niejawne użycie</span><span class="sxs-lookup"><span data-stu-id="1442f-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="1442f-112">Błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="1442f-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="1442f-113">Migracji Zastępowanie dla przestarzałych wywołań</span><span class="sxs-lookup"><span data-stu-id="1442f-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="1442f-114">Zgodna Korzystanie z opcji starszej wersji zasad CAS</span><span class="sxs-lookup"><span data-stu-id="1442f-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="1442f-115">Jawne użycie</span><span class="sxs-lookup"><span data-stu-id="1442f-115">Explicit Use</span></span>

<span data-ttu-id="1442f-116">Elementy członkowskie, które bezpośrednio manipulują zasadami zabezpieczeń lub wymagają zasad CAS do piaskownicy, są przestarzałe i domyślnie generują błędy.</span><span class="sxs-lookup"><span data-stu-id="1442f-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="1442f-117">Przykłady są następujące:</span><span class="sxs-lookup"><span data-stu-id="1442f-117">Examples of these are:</span></span>

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

## <a name="implicit-use"></a><span data-ttu-id="1442f-118">Niejawne użycie</span><span class="sxs-lookup"><span data-stu-id="1442f-118">Implicit Use</span></span>

<span data-ttu-id="1442f-119">Niektóre przeciążenia ładowania zestawów generują błędy ze względu na niejawne użycie zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="1442f-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="1442f-120">Te przeciążenia mają <xref:System.Security.Policy.Evidence> parametr, który jest używany do rozpoznawania zasad CAS i zapewniają zestaw uprawnień dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="1442f-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="1442f-121">Oto kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="1442f-121">Here are some examples.</span></span> <span data-ttu-id="1442f-122">Przestarzałe przeciążenia to te, które <xref:System.Security.Policy.Evidence> przyjmują jako parametr:</span><span class="sxs-lookup"><span data-stu-id="1442f-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

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

## <a name="errors-and-warnings"></a><span data-ttu-id="1442f-123">Błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="1442f-123">Errors and Warnings</span></span>

<span data-ttu-id="1442f-124">Przestarzałe typy i elementy członkowskie generują następujące komunikaty o błędach, gdy są używane.</span><span class="sxs-lookup"><span data-stu-id="1442f-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="1442f-125">Należy pamiętać, <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> że sam typ nie jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="1442f-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="1442f-126">Ostrzeżenie czasu kompilacji:</span><span class="sxs-lookup"><span data-stu-id="1442f-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="1442f-127">Wyjątek czasu wykonywania:</span><span class="sxs-lookup"><span data-stu-id="1442f-127">Run-time exception:</span></span>

<span data-ttu-id="1442f-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="1442f-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="1442f-129">Migracji Zastępowanie dla przestarzałych wywołań</span><span class="sxs-lookup"><span data-stu-id="1442f-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="1442f-130">Określanie poziomu zaufania zestawu</span><span class="sxs-lookup"><span data-stu-id="1442f-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="1442f-131">Zasady urzędów certyfikacji są często używane do określania uprawnień do zestawu lub poziomu zaufania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1442f-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="1442f-132">.NET Framework 4 uwidacznia następujące przydatne właściwości, które nie muszą rozwiązywać zasad zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="1442f-132">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="1442f-133">Tryb piaskownicy domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1442f-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="1442f-134">Metoda <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> ta jest zwykle używana do wypełniania zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1442f-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="1442f-135">.NET Framework 4 uwidacznia składowe, które nie muszą być używane <xref:System.Security.Policy.PolicyLevel> do tego celu.</span><span class="sxs-lookup"><span data-stu-id="1442f-135">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="1442f-136">Aby uzyskać więcej informacji, zobacz [jak: Uruchom częściowo zaufany kod w piaskownicy](how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="1442f-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="1442f-137">Określanie bezpiecznego lub uzasadnionego zestawu uprawnień dla częściowo zaufanego kodu</span><span class="sxs-lookup"><span data-stu-id="1442f-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="1442f-138">Hosty często muszą określić uprawnienia, które są odpowiednie dla hostowanego kodu w trybie piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="1442f-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="1442f-139">Przed przystąpieniem do .NET Framework 4 zasady urzędów certyfikacji udostępniają <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="1442f-139">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1442f-140">Jako zamiennik, .NET Framework 4 udostępnia <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metodę, która zwraca bezpieczny, standardowy zestaw uprawnień dla dostarczonych dowodów.</span><span class="sxs-lookup"><span data-stu-id="1442f-140">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="1442f-141">Scenariusze spoza piaskownicy: Przeciążenia dla obciążeń zestawów</span><span class="sxs-lookup"><span data-stu-id="1442f-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="1442f-142">Przyczyną użycia przeciążenia ładowania zestawu może być użycie parametrów, które nie są dostępne w inny sposób, zamiast w piaskownicy zestawu.</span><span class="sxs-lookup"><span data-stu-id="1442f-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="1442f-143">Począwszy od .NET Framework 4, przeciążenia ładowania zestawów, które nie wymagają <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> obiektu jako parametru, na <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>przykład, Włącz ten scenariusz.</span><span class="sxs-lookup"><span data-stu-id="1442f-143">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="1442f-144">Jeśli chcesz piaskownicy zestawu, użyj <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="1442f-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="1442f-145">Zgodna Korzystanie z opcji starszej wersji zasad CAS</span><span class="sxs-lookup"><span data-stu-id="1442f-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="1442f-146">[Element konfiguracji > NetFx40_LegacySecurityPolicyumożliwiaokreślenie,żeproceslubbibliotekakorzystazestarszychzasadCAS.\<](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)</span><span class="sxs-lookup"><span data-stu-id="1442f-146">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="1442f-147">Po włączeniu tego elementu przeciążenia zasad i dowodów będą działały tak, jak w poprzednich wersjach platformy.</span><span class="sxs-lookup"><span data-stu-id="1442f-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="1442f-148">Zachowanie zasad CAS jest określone w wersji środowiska uruchomieniowego, więc modyfikowanie zasad CAS dla jednej wersji środowiska uruchomieniowego nie ma wpływu na zasady CAS innej wersji.</span><span class="sxs-lookup"><span data-stu-id="1442f-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1442f-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1442f-149">See also</span></span>

- [<span data-ttu-id="1442f-150">Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy</span><span class="sxs-lookup"><span data-stu-id="1442f-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="1442f-151">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="1442f-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
