---
title: Zgodność i migracja zasad zabezpieczenia dostępu kodu
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: 949739b3336a9182eef583cc405e60e09d7ec09d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217161"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="65514-102">Zgodność i migracja zasad zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="65514-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="65514-103">Część zasad zabezpieczeń dostępu kodu (CAS) była przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="65514-103">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="65514-104">W związku z tym mogą wystąpić ostrzeżenia kompilacji i wyjątki czasu wykonywania w przypadku wywołania przestarzałych typów zasad i elementów członkowskich [jawnie](#explicit_use) lub [niejawnie](#implicit_use) (za pomocą innych typów i elementów członkowskich).</span><span class="sxs-lookup"><span data-stu-id="65514-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="65514-105">Ostrzeżenia i błędy można uniknąć:</span><span class="sxs-lookup"><span data-stu-id="65514-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="65514-106">[Migrowanie](#migration) do .NET Framework 4 zamienników dla przestarzałych wywołań.</span><span class="sxs-lookup"><span data-stu-id="65514-106">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="65514-107">\- lub-</span><span class="sxs-lookup"><span data-stu-id="65514-107">\- or -</span></span>

- <span data-ttu-id="65514-108">Użyj [\<NetFx40_LegacySecurityPolicy > elementu konfiguracji](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) , aby zrezygnować ze starszego zachowania zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="65514-108">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="65514-109">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="65514-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="65514-110">Jawne użycie</span><span class="sxs-lookup"><span data-stu-id="65514-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="65514-111">Niejawne użycie</span><span class="sxs-lookup"><span data-stu-id="65514-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="65514-112">Błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="65514-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="65514-113">Migracja: zastępowanie dla przestarzałych wywołań</span><span class="sxs-lookup"><span data-stu-id="65514-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="65514-114">Zgodność: korzystanie z opcji starszej wersji zasad CAS</span><span class="sxs-lookup"><span data-stu-id="65514-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="65514-115">Jawne użycie</span><span class="sxs-lookup"><span data-stu-id="65514-115">Explicit Use</span></span>

<span data-ttu-id="65514-116">Elementy członkowskie, które bezpośrednio manipulują zasadami zabezpieczeń lub wymagają zasad CAS do piaskownicy, są przestarzałe i domyślnie generują błędy.</span><span class="sxs-lookup"><span data-stu-id="65514-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="65514-117">Przykłady są następujące:</span><span class="sxs-lookup"><span data-stu-id="65514-117">Examples of these are:</span></span>

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

## <a name="implicit-use"></a><span data-ttu-id="65514-118">Niejawne użycie</span><span class="sxs-lookup"><span data-stu-id="65514-118">Implicit Use</span></span>

<span data-ttu-id="65514-119">Niektóre przeciążenia ładowania zestawów generują błędy ze względu na niejawne użycie zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="65514-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="65514-120">Te przeciążenia pobierają <xref:System.Security.Policy.Evidence> parametr, który jest używany do rozpoznawania zasad CAS i zapewniają zestaw uprawnień ustawiony dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="65514-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="65514-121">Oto kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="65514-121">Here are some examples.</span></span> <span data-ttu-id="65514-122">Przestarzałe przeciążenia to te, które przyjmują <xref:System.Security.Policy.Evidence> jako parametr:</span><span class="sxs-lookup"><span data-stu-id="65514-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

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

## <a name="errors-and-warnings"></a><span data-ttu-id="65514-123">Błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="65514-123">Errors and Warnings</span></span>

<span data-ttu-id="65514-124">Przestarzałe typy i elementy członkowskie generują następujące komunikaty o błędach, gdy są używane.</span><span class="sxs-lookup"><span data-stu-id="65514-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="65514-125">Należy zauważyć, że sam typ <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> nie jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="65514-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="65514-126">Ostrzeżenie czasu kompilacji:</span><span class="sxs-lookup"><span data-stu-id="65514-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="65514-127">Wyjątek czasu wykonywania:</span><span class="sxs-lookup"><span data-stu-id="65514-127">Run-time exception:</span></span>

<span data-ttu-id="65514-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="65514-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="65514-129">Migracja: zastępowanie dla przestarzałych wywołań</span><span class="sxs-lookup"><span data-stu-id="65514-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="65514-130">Określanie poziomu zaufania zestawu</span><span class="sxs-lookup"><span data-stu-id="65514-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="65514-131">Zasady urzędów certyfikacji są często używane do określania uprawnień do zestawu lub poziomu zaufania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65514-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="65514-132">.NET Framework 4 uwidacznia następujące przydatne właściwości, które nie muszą rozwiązywać zasad zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="65514-132">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="65514-133">Tryb piaskownicy domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="65514-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="65514-134">Metoda <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> jest zwykle używana do wypełniania zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65514-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="65514-135">.NET Framework 4 uwidacznia członkom, którzy nie muszą używać <xref:System.Security.Policy.PolicyLevel> do tego celu.</span><span class="sxs-lookup"><span data-stu-id="65514-135">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="65514-136">Aby uzyskać więcej informacji, zobacz [jak: uruchamiać częściowo zaufany kod w piaskownicy](how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="65514-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="65514-137">Określanie bezpiecznego lub uzasadnionego zestawu uprawnień dla częściowo zaufanego kodu</span><span class="sxs-lookup"><span data-stu-id="65514-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="65514-138">Hosty często muszą określić uprawnienia, które są odpowiednie dla hostowanego kodu w trybie piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="65514-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="65514-139">Przed przystąpieniem do .NET Framework 4 zasady urzędów certyfikacji udostępniają metodę <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65514-139">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="65514-140">Jako zamiennik, .NET Framework 4 udostępnia metodę <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType>, która zwraca bezpieczny, standardowy zestaw uprawnień dla dostarczonych dowodów.</span><span class="sxs-lookup"><span data-stu-id="65514-140">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="65514-141">Scenariusze spoza piaskownicy: przeciążenia dla obciążeń zestawu</span><span class="sxs-lookup"><span data-stu-id="65514-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="65514-142">Przyczyną użycia przeciążenia ładowania zestawu może być użycie parametrów, które nie są dostępne w inny sposób, zamiast w piaskownicy zestawu.</span><span class="sxs-lookup"><span data-stu-id="65514-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="65514-143">Począwszy od .NET Framework 4, przeciążenia ładowania zestawów, które nie wymagają obiektu <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> jako parametru, na przykład <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, Włącz ten scenariusz.</span><span class="sxs-lookup"><span data-stu-id="65514-143">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="65514-144">Jeśli chcesz piaskownicy zestawu, Użyj przeciążenia <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65514-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="65514-145">Zgodność: korzystanie z opcji starszej wersji zasad CAS</span><span class="sxs-lookup"><span data-stu-id="65514-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="65514-146">[\<NetFx40_LegacySecurityPolicy > elementu konfiguracji](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) pozwala określić, że proces lub biblioteka korzysta ze starszych zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="65514-146">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="65514-147">Po włączeniu tego elementu przeciążenia zasad i dowodów będą działały tak, jak w poprzednich wersjach platformy.</span><span class="sxs-lookup"><span data-stu-id="65514-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="65514-148">Zachowanie zasad CAS jest określone w wersji środowiska uruchomieniowego, więc modyfikowanie zasad CAS dla jednej wersji środowiska uruchomieniowego nie ma wpływu na zasady CAS innej wersji.</span><span class="sxs-lookup"><span data-stu-id="65514-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="65514-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65514-149">See also</span></span>

- [<span data-ttu-id="65514-150">Instrukcje: uruchamianie częściowo zaufanego kodu w piaskownicy</span><span class="sxs-lookup"><span data-stu-id="65514-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="65514-151">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="65514-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
