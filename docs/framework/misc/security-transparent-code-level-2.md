---
title: Kod o przezroczystym poziomie bezpieczeństwa, poziom 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 7ac5660c2c431505f4992f5e687974c2b9d06672
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216995"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="02063-102">Kod o przezroczystym poziomie bezpieczeństwa, poziom 2</span><span class="sxs-lookup"><span data-stu-id="02063-102">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="02063-103">Poziom 2 przejrzystości został wprowadzony w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="02063-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="02063-104">Trzy założenia tego modelu to kod przezroczysty, kod zabezpieczeń bezpieczny-krytyczny i kod krytyczny dla bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="02063-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="02063-105">Kod przezroczysty, w tym kod, który jest uruchomiony jako pełne zaufanie, może wywoływać inny kod przezroczysty lub tylko kod krytyczny bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="02063-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="02063-106">Może wykonywać tylko akcje dozwolone przez zestaw uprawnień częściowej relacji zaufania domeny (jeśli taki istnieje).</span><span class="sxs-lookup"><span data-stu-id="02063-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="02063-107">Kod przezroczysty nie może wykonać następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="02063-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="02063-108">Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> lub podniesienie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="02063-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="02063-109">Zawiera kod niebezpieczny lub niemożliwy do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="02063-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="02063-110">Bezpośrednie Wywoływanie kodu krytycznego.</span><span class="sxs-lookup"><span data-stu-id="02063-110">Directly call critical code.</span></span>

  - <span data-ttu-id="02063-111">Wywoływanie kodu natywnego lub kodu z atrybutem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.</span><span class="sxs-lookup"><span data-stu-id="02063-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="02063-112">Wywołaj element członkowski, który jest chroniony przez <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="02063-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="02063-113">Dziedzicz z typów krytycznych.</span><span class="sxs-lookup"><span data-stu-id="02063-113">Inherit from critical types.</span></span>

  <span data-ttu-id="02063-114">Ponadto metody przezroczyste nie mogą przesłaniać krytycznych metod wirtualnych ani implementować metod interfejsu krytycznego.</span><span class="sxs-lookup"><span data-stu-id="02063-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="02063-115">Kod bezpieczny-krytyczny jest w pełni zaufany, ale jest wywoływany przez kod przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="02063-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="02063-116">Ujawnia on ograniczony obszar, w którym znajduje się kod pełnego zaufania; Sprawdzanie poprawności i zabezpieczeń odbywa się w kodzie krytycznym.</span><span class="sxs-lookup"><span data-stu-id="02063-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="02063-117">Kod krytyczny dla zabezpieczeń może wywołać dowolny kod i jest w pełni zaufany, ale nie może być wywoływany przez kod przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="02063-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="02063-118">Przykłady użycia i zachowania</span><span class="sxs-lookup"><span data-stu-id="02063-118">Usage Examples and Behaviors</span></span>

<span data-ttu-id="02063-119">Aby określić reguły .NET Framework 4 (poziom 2 przezroczystości), użyj następującej adnotacji dla zestawu:</span><span class="sxs-lookup"><span data-stu-id="02063-119">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="02063-120">Aby zablokować reguły .NET Framework 2,0 (poziom 1 przejrzystości), użyj następującej adnotacji:</span><span class="sxs-lookup"><span data-stu-id="02063-120">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="02063-121">Jeśli nie podasz adnotacji z zestawem, domyślnie używane są reguły .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="02063-121">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="02063-122">Zalecanym najlepszym rozwiązaniem jest użycie atrybutu <xref:System.Security.SecurityRulesAttribute> zamiast wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="02063-122">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="02063-123">Adnotacja w całej zestawie</span><span class="sxs-lookup"><span data-stu-id="02063-123">Assembly-wide Annotation</span></span>

<span data-ttu-id="02063-124">Następujące reguły mają zastosowanie do korzystania z atrybutów na poziomie zestawu:</span><span class="sxs-lookup"><span data-stu-id="02063-124">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="02063-125">Brak atrybutów: Jeśli nie określisz żadnych atrybutów, środowisko uruchomieniowe interpretuje cały kod jako krytyczny dla zabezpieczeń, z wyjątkiem sytuacji, w których zabezpieczenia krytyczne naruszają regułę dziedziczenia (na przykład podczas zastępowania lub implementowania przezroczystej metody wirtualnej lub interfejsu ).</span><span class="sxs-lookup"><span data-stu-id="02063-125">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="02063-126">W takich przypadkach metody są bezpieczne-krytyczne.</span><span class="sxs-lookup"><span data-stu-id="02063-126">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="02063-127">Określenie braku atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego nie określi reguł przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="02063-127">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="02063-128">`SecurityTransparent`: cały kod jest przezroczysty; cały zestaw nie będzie miał żadnego uprzywilejowanego ani niebezpiecznego.</span><span class="sxs-lookup"><span data-stu-id="02063-128">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="02063-129">`SecurityCritical`: cały kod wprowadzony przez typy w tym zestawie ma krytyczne znaczenie. cały inny kod jest przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="02063-129">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="02063-130">Ten scenariusz jest podobny do nieokreślania atrybutów; jednak środowisko uruchomieniowe języka wspólnego nie ustala automatycznie reguł przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="02063-130">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="02063-131">Na przykład jeśli zastąpisz metodę wirtualną lub abstrakcyjną lub implementuje metodę interfejsu, domyślnie ta metoda jest przezroczysta.</span><span class="sxs-lookup"><span data-stu-id="02063-131">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="02063-132">Należy jawnie dodać adnotację do metody jako `SecurityCritical` lub `SecuritySafeCritical`; w przeciwnym razie <xref:System.TypeLoadException> zostanie wygenerowane w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="02063-132">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="02063-133">Ta reguła ma zastosowanie również wtedy, gdy zarówno Klasa bazowa, jak i Klasa pochodna znajdują się w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="02063-133">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="02063-134">`AllowPartiallyTrustedCallers` (tylko poziom 2): wszystkie wartości domyślne kodu są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="02063-134">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="02063-135">Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="02063-135">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="02063-136">Poniższa tabela zawiera porównanie zachowania poziomu zestawu dla poziomu 2 z poziomem 1.</span><span class="sxs-lookup"><span data-stu-id="02063-136">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="02063-137">Atrybut zestawu</span><span class="sxs-lookup"><span data-stu-id="02063-137">Assembly attribute</span></span>|<span data-ttu-id="02063-138">Poziom 2</span><span class="sxs-lookup"><span data-stu-id="02063-138">Level 2</span></span>|<span data-ttu-id="02063-139">Poziom 1</span><span class="sxs-lookup"><span data-stu-id="02063-139">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="02063-140">Brak atrybutu dla częściowo zaufanego zestawu</span><span class="sxs-lookup"><span data-stu-id="02063-140">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="02063-141">Typy i elementy członkowskie są domyślnie przezroczyste, ale mogą mieć zabezpieczenia krytyczne lub zabezpieczenia-krytyczne.</span><span class="sxs-lookup"><span data-stu-id="02063-141">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="02063-142">Wszystkie typy i elementy członkowskie są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="02063-142">All types and members are transparent.</span></span>|
|<span data-ttu-id="02063-143">Brak atrybutu</span><span class="sxs-lookup"><span data-stu-id="02063-143">No attribute</span></span>|<span data-ttu-id="02063-144">Określenie braku atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego nie określi reguł przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="02063-144">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="02063-145">Wszystkie typy i elementy członkowskie mają krytyczne znaczenie dla zabezpieczeń, z wyjątkiem sytuacji, w których krytyczne zabezpieczenia naruszają regułę dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="02063-145">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="02063-146">W w pełni zaufanym zestawie (w globalnej pamięci podręcznej zestawów lub zidentyfikowanym jako pełne zaufanie w `AppDomain`) wszystkie typy są przezroczyste i wszystkie elementy członkowskie są bezpieczne-krytyczne.</span><span class="sxs-lookup"><span data-stu-id="02063-146">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="02063-147">Wszystkie typy i elementy członkowskie są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="02063-147">All types and members are transparent.</span></span>|<span data-ttu-id="02063-148">Wszystkie typy i elementy członkowskie są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="02063-148">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="02063-149">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="02063-149">Not applicable.</span></span>|<span data-ttu-id="02063-150">Wszystkie typy i elementy członkowskie są krytyczne dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="02063-150">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="02063-151">Cały kod, który jest wprowadzany przez typy w tym zestawie, ma krytyczne znaczenie. cały inny kod jest przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="02063-151">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="02063-152">Jeśli zastąpisz wirtualną lub abstrakcyjną metodę lub implementuje metodę interfejsu, należy jawnie dodać adnotację do metody jako `SecurityCritical` lub `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="02063-152">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="02063-153">Wszystkie wartości domyślne kodu są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="02063-153">All code defaults to transparent.</span></span> <span data-ttu-id="02063-154">Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="02063-154">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="02063-155">Typ i adnotacja członkowska</span><span class="sxs-lookup"><span data-stu-id="02063-155">Type and Member Annotation</span></span>

<span data-ttu-id="02063-156">Atrybuty zabezpieczeń stosowane do typu mają również zastosowanie do elementów członkowskich, które są wprowadzane przez typ.</span><span class="sxs-lookup"><span data-stu-id="02063-156">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="02063-157">Jednak nie mają zastosowania do wirtualnych lub abstrakcyjnych zastąpień klasy bazowej lub implementacji interfejsów.</span><span class="sxs-lookup"><span data-stu-id="02063-157">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="02063-158">Następujące reguły mają zastosowanie do używania atrybutów na poziomie typu i elementu członkowskiego:</span><span class="sxs-lookup"><span data-stu-id="02063-158">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="02063-159">`SecurityCritical`: typ lub element członkowski jest krytyczny i może być wywoływany tylko przez kod pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="02063-159">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="02063-160">Metody wprowadzane w zabezpieczeniach typu krytycznego są krytyczne.</span><span class="sxs-lookup"><span data-stu-id="02063-160">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="02063-161">Metody wirtualne i abstrakcyjne wprowadzone w klasach bazowych lub interfejsach, a także zastąpione lub zaimplementowane w klasie o krytycznym znaczeniu są domyślnie przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="02063-161">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="02063-162">Muszą one być zidentyfikowane jako `SecuritySafeCritical` lub `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="02063-162">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="02063-163">`SecuritySafeCritical`: typ lub element członkowski jest bezpieczny-krytyczny.</span><span class="sxs-lookup"><span data-stu-id="02063-163">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="02063-164">Jednak typ lub element członkowski może być wywoływany z przezroczystego (częściowo zaufanego) kodu i jest tak jak każdy inny kod krytyczny.</span><span class="sxs-lookup"><span data-stu-id="02063-164">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="02063-165">Kod musi być poddany inspekcji pod kątem bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="02063-165">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="02063-166">Zastępowanie wzorów</span><span class="sxs-lookup"><span data-stu-id="02063-166">Override Patterns</span></span>

<span data-ttu-id="02063-167">W poniższej tabeli przedstawiono metody przesłaniania dozwolone dla przezroczystości poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="02063-167">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="02063-168">Podstawowy element członkowski wirtualnego/interfejsu</span><span class="sxs-lookup"><span data-stu-id="02063-168">Base virtual/interface member</span></span>|<span data-ttu-id="02063-169">Zastąpienie/interfejs</span><span class="sxs-lookup"><span data-stu-id="02063-169">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="02063-170">Zasady dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="02063-170">Inheritance Rules</span></span>

<span data-ttu-id="02063-171">W tej sekcji następująca kolejność jest przypisana do `Transparent`, `Critical`i kodu `SafeCritical` na podstawie dostępu i możliwości:</span><span class="sxs-lookup"><span data-stu-id="02063-171">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="02063-172">Reguły dla typów: od lewej do prawej, dostęp staną się bardziej restrykcyjne.</span><span class="sxs-lookup"><span data-stu-id="02063-172">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="02063-173">Typy pochodne muszą być co najmniej tak restrykcyjne jak typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="02063-173">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="02063-174">Reguły dla metod: metody pochodne nie mogą zmieniać dostępności z metody podstawowej.</span><span class="sxs-lookup"><span data-stu-id="02063-174">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="02063-175">W przypadku zachowania domyślnego wszystkie metody pochodne, które nie są adnotacjami, są `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="02063-175">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="02063-176">Pochodne typów krytycznych powodują, że wyjątek jest zgłaszany, jeśli zastąpiona metoda nie jest jawnie oznaczona jako `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="02063-176">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="02063-177">W poniższej tabeli przedstawiono wzorce dziedziczenia typów dozwolonych.</span><span class="sxs-lookup"><span data-stu-id="02063-177">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="02063-178">Klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="02063-178">Base class</span></span>|<span data-ttu-id="02063-179">Klasa pochodna może być</span><span class="sxs-lookup"><span data-stu-id="02063-179">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="02063-180">W poniższej tabeli przedstawiono wzorce dziedziczenia typu niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="02063-180">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="02063-181">Klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="02063-181">Base class</span></span>|<span data-ttu-id="02063-182">Klasa pochodna nie może być</span><span class="sxs-lookup"><span data-stu-id="02063-182">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="02063-183">W poniższej tabeli przedstawiono dozwolone wzorce dziedziczenia metody.</span><span class="sxs-lookup"><span data-stu-id="02063-183">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="02063-184">Metoda bazowa</span><span class="sxs-lookup"><span data-stu-id="02063-184">Base method</span></span>|<span data-ttu-id="02063-185">Pochodna Metoda może być</span><span class="sxs-lookup"><span data-stu-id="02063-185">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="02063-186">W poniższej tabeli przedstawiono niedozwolone wzorce dziedziczenia metody.</span><span class="sxs-lookup"><span data-stu-id="02063-186">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="02063-187">Metoda bazowa</span><span class="sxs-lookup"><span data-stu-id="02063-187">Base method</span></span>|<span data-ttu-id="02063-188">Metoda pochodna nie może być</span><span class="sxs-lookup"><span data-stu-id="02063-188">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="02063-189">Te reguły dziedziczenia mają zastosowanie do typów i elementów członkowskich poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="02063-189">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="02063-190">Typy zestawów na poziomie 1 mogą dziedziczyć z typów i elementów krytycznych zabezpieczeń poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="02063-190">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="02063-191">W związku z tym typy i elementy członkowskie poziomu 2 muszą mieć oddzielne żądania dziedziczenia dla dziedziczeń poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="02063-191">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="02063-192">Dodatkowe informacje i zasady</span><span class="sxs-lookup"><span data-stu-id="02063-192">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="02063-193">Obsługa LinkDemand</span><span class="sxs-lookup"><span data-stu-id="02063-193">LinkDemand Support</span></span>

<span data-ttu-id="02063-194">Model przezroczystości poziomu 2 zastępuje <xref:System.Security.Permissions.SecurityAction.LinkDemand> z atrybutem <xref:System.Security.SecurityCriticalAttribute>.</span><span class="sxs-lookup"><span data-stu-id="02063-194">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="02063-195">W przypadku starszego kodu (poziom 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> jest automatycznie traktowany jako <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="02063-195">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="02063-196">Odbicie</span><span class="sxs-lookup"><span data-stu-id="02063-196">Reflection</span></span>

<span data-ttu-id="02063-197">Wywołanie krytycznej metody lub odczytanie pola krytycznego wyzwala żądanie pełnego zaufania (podobnie jak w przypadku wywołania metody prywatnej lub pola).</span><span class="sxs-lookup"><span data-stu-id="02063-197">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="02063-198">W związku z tym kod pełnego zaufania może wywołać metodę krytyczną, natomiast kod częściowego zaufania nie może.</span><span class="sxs-lookup"><span data-stu-id="02063-198">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="02063-199">Następujące właściwości zostały dodane do przestrzeni nazw <xref:System.Reflection>, aby określić, czy typ, metoda lub pole jest `SecurityCritical`, `SecuritySafeCritical`lub `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>i <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="02063-199">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="02063-200">Te właściwości umożliwiają określanie przejrzystości przy użyciu odbicia zamiast sprawdzania obecności atrybutu.</span><span class="sxs-lookup"><span data-stu-id="02063-200">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="02063-201">Reguły przezroczystości są złożone i sprawdzanie, czy atrybut może być niewystarczający.</span><span class="sxs-lookup"><span data-stu-id="02063-201">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="02063-202">Metoda `SafeCritical` zwraca `true` zarówno dla <xref:System.Type.IsSecurityCritical%2A>, jak i <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, ponieważ `SafeCritical` jest rzeczywiście krytyczne (ma takie same możliwości jak kod krytyczny, ale może być wywoływana z kodu przezroczystego).</span><span class="sxs-lookup"><span data-stu-id="02063-202">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="02063-203">Metody dynamiczne dziedziczą przezroczystości modułów, do których są dołączone; nie dziedziczą przezroczystości typu (jeśli są dołączone do typu).</span><span class="sxs-lookup"><span data-stu-id="02063-203">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="02063-204">Pomiń weryfikację w trybie całkowitego zaufania</span><span class="sxs-lookup"><span data-stu-id="02063-204">Skip Verification in Full Trust</span></span>

<span data-ttu-id="02063-205">Możesz pominąć weryfikację dla w pełni zaufanych, przezroczystych zestawów, ustawiając właściwość <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> na `true` w atrybucie <xref:System.Security.SecurityRulesAttribute>:</span><span class="sxs-lookup"><span data-stu-id="02063-205">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="02063-206">Właściwość <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> jest `false` domyślnie, więc właściwość musi być ustawiona na `true`, aby pominąć weryfikację.</span><span class="sxs-lookup"><span data-stu-id="02063-206">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="02063-207">Należy to zrobić tylko w celach optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="02063-207">This should be done for optimization purposes only.</span></span> <span data-ttu-id="02063-208">Upewnij się, że przezroczysty kod w zestawie jest możliwy do zweryfikowania przy użyciu opcji `transparent` w [narzędziu PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="02063-208">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02063-209">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02063-209">See also</span></span>

- [<span data-ttu-id="02063-210">Kod przezroczysty pod względem zabezpieczeń, poziom 1</span><span class="sxs-lookup"><span data-stu-id="02063-210">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="02063-211">Zmiany zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="02063-211">Security Changes</span></span>](../security/security-changes.md)
