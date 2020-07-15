---
title: Kod o przezroczystym poziomie bezpieczeństwa, poziom 2
description: Opis przezroczystego kodu poziomu 2. Zobacz przykłady użycia i zachowania, Zastąp wzorce, reguły dziedziczenia i nie tylko.
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 3b87a48ac3f9925fd868be9e58d5904014ca6c09
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309212"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="d46e5-104">Kod o przezroczystym poziomie bezpieczeństwa, poziom 2</span><span class="sxs-lookup"><span data-stu-id="d46e5-104">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="d46e5-105">Poziom 2 przejrzystości został wprowadzony w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d46e5-105">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="d46e5-106">Trzy założenia tego modelu to kod przezroczysty, kod zabezpieczeń bezpieczny-krytyczny i kod krytyczny dla bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="d46e5-106">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="d46e5-107">Kod przezroczysty, w tym kod, który jest uruchomiony jako pełne zaufanie, może wywoływać inny kod przezroczysty lub tylko kod krytyczny bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="d46e5-107">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="d46e5-108">Może wykonywać tylko akcje dozwolone przez zestaw uprawnień częściowej relacji zaufania domeny (jeśli taki istnieje).</span><span class="sxs-lookup"><span data-stu-id="d46e5-108">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="d46e5-109">Kod przezroczysty nie może wykonać następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d46e5-109">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="d46e5-110">Wykonanie <xref:System.Security.CodeAccessPermission.Assert%2A> lub podniesienie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="d46e5-110">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="d46e5-111">Zawiera kod niebezpieczny lub niemożliwy do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="d46e5-111">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="d46e5-112">Bezpośrednie Wywoływanie kodu krytycznego.</span><span class="sxs-lookup"><span data-stu-id="d46e5-112">Directly call critical code.</span></span>

  - <span data-ttu-id="d46e5-113">Wywoływanie kodu natywnego lub kodu przy użyciu <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d46e5-113">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="d46e5-114">Wywoływanie elementu członkowskiego, który jest chroniony przez <xref:System.Security.Permissions.SecurityAction.LinkDemand> .</span><span class="sxs-lookup"><span data-stu-id="d46e5-114">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="d46e5-115">Dziedzicz z typów krytycznych.</span><span class="sxs-lookup"><span data-stu-id="d46e5-115">Inherit from critical types.</span></span>

  <span data-ttu-id="d46e5-116">Ponadto metody przezroczyste nie mogą przesłaniać krytycznych metod wirtualnych ani implementować metod interfejsu krytycznego.</span><span class="sxs-lookup"><span data-stu-id="d46e5-116">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="d46e5-117">Kod bezpieczny-krytyczny jest w pełni zaufany, ale jest wywoływany przez kod przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="d46e5-117">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="d46e5-118">Ujawnia on ograniczony obszar, w którym znajduje się kod pełnego zaufania; Sprawdzanie poprawności i zabezpieczeń odbywa się w kodzie krytycznym.</span><span class="sxs-lookup"><span data-stu-id="d46e5-118">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="d46e5-119">Kod krytyczny dla zabezpieczeń może wywołać dowolny kod i jest w pełni zaufany, ale nie może być wywoływany przez kod przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="d46e5-119">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="d46e5-120">Przykłady użycia i zachowania</span><span class="sxs-lookup"><span data-stu-id="d46e5-120">Usage Examples and Behaviors</span></span>

<span data-ttu-id="d46e5-121">Aby określić reguły .NET Framework 4 (poziom 2 przezroczystości), użyj następującej adnotacji dla zestawu:</span><span class="sxs-lookup"><span data-stu-id="d46e5-121">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="d46e5-122">Aby zablokować reguły .NET Framework 2,0 (poziom 1 przejrzystości), użyj następującej adnotacji:</span><span class="sxs-lookup"><span data-stu-id="d46e5-122">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="d46e5-123">Jeśli nie podasz adnotacji z zestawem, domyślnie używane są reguły .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d46e5-123">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="d46e5-124">Jednak zalecanym najlepszym rozwiązaniem jest użycie <xref:System.Security.SecurityRulesAttribute> atrybutu zamiast wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="d46e5-124">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="d46e5-125">Adnotacja w całej zestawie</span><span class="sxs-lookup"><span data-stu-id="d46e5-125">Assembly-wide Annotation</span></span>

<span data-ttu-id="d46e5-126">Następujące reguły mają zastosowanie do korzystania z atrybutów na poziomie zestawu:</span><span class="sxs-lookup"><span data-stu-id="d46e5-126">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="d46e5-127">Brak atrybutów: Jeśli nie określisz żadnych atrybutów, środowisko uruchomieniowe interpretuje cały kod jako krytyczny dla zabezpieczeń, z wyjątkiem sytuacji, w których zabezpieczenia krytyczne naruszają regułę dziedziczenia (na przykład podczas zastępowania lub implementowania przezroczystej metody wirtualnej lub interfejsu).</span><span class="sxs-lookup"><span data-stu-id="d46e5-127">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="d46e5-128">W takich przypadkach metody są bezpieczne-krytyczne.</span><span class="sxs-lookup"><span data-stu-id="d46e5-128">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="d46e5-129">Określenie braku atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego nie określi reguł przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="d46e5-129">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="d46e5-130">`SecurityTransparent`: Cały kod jest przezroczysty; cały zestaw nie będzie miał żadnego uprzywilejowanego ani niebezpiecznego.</span><span class="sxs-lookup"><span data-stu-id="d46e5-130">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="d46e5-131">`SecurityCritical`: Cały kod wprowadzony przez typy w tym zestawie ma krytyczne znaczenie. cały inny kod jest przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="d46e5-131">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="d46e5-132">Ten scenariusz jest podobny do nieokreślania atrybutów; jednak środowisko uruchomieniowe języka wspólnego nie ustala automatycznie reguł przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="d46e5-132">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="d46e5-133">Na przykład jeśli zastąpisz metodę wirtualną lub abstrakcyjną lub implementuje metodę interfejsu, domyślnie ta metoda jest przezroczysta.</span><span class="sxs-lookup"><span data-stu-id="d46e5-133">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="d46e5-134">Należy jawnie dodać adnotację do metody jako `SecurityCritical` lub `SecuritySafeCritical` ; w przeciwnym razie <xref:System.TypeLoadException> zostanie wygenerowane w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="d46e5-134">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="d46e5-135">Ta reguła ma zastosowanie również wtedy, gdy zarówno Klasa bazowa, jak i Klasa pochodna znajdują się w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="d46e5-135">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="d46e5-136">`AllowPartiallyTrustedCallers`(tylko poziom 2): wszystkie wartości domyślne kodu są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="d46e5-136">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="d46e5-137">Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="d46e5-137">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="d46e5-138">Poniższa tabela zawiera porównanie zachowania poziomu zestawu dla poziomu 2 z poziomem 1.</span><span class="sxs-lookup"><span data-stu-id="d46e5-138">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="d46e5-139">Atrybut zestawu</span><span class="sxs-lookup"><span data-stu-id="d46e5-139">Assembly attribute</span></span>|<span data-ttu-id="d46e5-140">Poziom 2</span><span class="sxs-lookup"><span data-stu-id="d46e5-140">Level 2</span></span>|<span data-ttu-id="d46e5-141">Poziom 1</span><span class="sxs-lookup"><span data-stu-id="d46e5-141">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="d46e5-142">Brak atrybutu dla częściowo zaufanego zestawu</span><span class="sxs-lookup"><span data-stu-id="d46e5-142">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="d46e5-143">Typy i elementy członkowskie są domyślnie przezroczyste, ale mogą mieć zabezpieczenia krytyczne lub zabezpieczenia-krytyczne.</span><span class="sxs-lookup"><span data-stu-id="d46e5-143">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="d46e5-144">Wszystkie typy i elementy członkowskie są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="d46e5-144">All types and members are transparent.</span></span>|
|<span data-ttu-id="d46e5-145">Brak atrybutu</span><span class="sxs-lookup"><span data-stu-id="d46e5-145">No attribute</span></span>|<span data-ttu-id="d46e5-146">Określenie braku atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego nie określi reguł przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="d46e5-146">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="d46e5-147">Wszystkie typy i elementy członkowskie mają krytyczne znaczenie dla zabezpieczeń, z wyjątkiem sytuacji, w których krytyczne zabezpieczenia naruszają regułę dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="d46e5-147">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="d46e5-148">W pełni zaufany zestaw (w globalnej pamięci podręcznej zestawów lub zidentyfikowane jako pełne zaufanie w `AppDomain` ) wszystkie typy są przezroczyste i wszystkie elementy członkowskie są bezpieczne-krytyczne.</span><span class="sxs-lookup"><span data-stu-id="d46e5-148">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="d46e5-149">Wszystkie typy i elementy członkowskie są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="d46e5-149">All types and members are transparent.</span></span>|<span data-ttu-id="d46e5-150">Wszystkie typy i elementy członkowskie są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="d46e5-150">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="d46e5-151">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="d46e5-151">Not applicable.</span></span>|<span data-ttu-id="d46e5-152">Wszystkie typy i elementy członkowskie są krytyczne dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d46e5-152">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="d46e5-153">Cały kod, który jest wprowadzany przez typy w tym zestawie, ma krytyczne znaczenie. cały inny kod jest przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="d46e5-153">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="d46e5-154">Jeśli zastąpisz wirtualną lub abstrakcyjną metodę lub implementuje metodę interfejsu, należy jawnie dodać adnotację do metody jako `SecurityCritical` lub `SecuritySafeCritical` .</span><span class="sxs-lookup"><span data-stu-id="d46e5-154">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="d46e5-155">Wszystkie wartości domyślne kodu są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="d46e5-155">All code defaults to transparent.</span></span> <span data-ttu-id="d46e5-156">Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="d46e5-156">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="d46e5-157">Typ i adnotacja członkowska</span><span class="sxs-lookup"><span data-stu-id="d46e5-157">Type and Member Annotation</span></span>

<span data-ttu-id="d46e5-158">Atrybuty zabezpieczeń stosowane do typu mają również zastosowanie do elementów członkowskich, które są wprowadzane przez typ.</span><span class="sxs-lookup"><span data-stu-id="d46e5-158">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="d46e5-159">Jednak nie mają zastosowania do wirtualnych lub abstrakcyjnych zastąpień klasy bazowej lub implementacji interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d46e5-159">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="d46e5-160">Następujące reguły mają zastosowanie do używania atrybutów na poziomie typu i elementu członkowskiego:</span><span class="sxs-lookup"><span data-stu-id="d46e5-160">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="d46e5-161">`SecurityCritical`: Typ lub element członkowski jest krytyczny i może być wywoływany tylko przez kod pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="d46e5-161">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="d46e5-162">Metody wprowadzane w zabezpieczeniach typu krytycznego są krytyczne.</span><span class="sxs-lookup"><span data-stu-id="d46e5-162">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d46e5-163">Metody wirtualne i abstrakcyjne wprowadzone w klasach bazowych lub interfejsach, a także zastąpione lub zaimplementowane w klasie o krytycznym znaczeniu są domyślnie przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="d46e5-163">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="d46e5-164">Muszą one być zidentyfikowane jako `SecuritySafeCritical` lub `SecurityCritical` .</span><span class="sxs-lookup"><span data-stu-id="d46e5-164">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="d46e5-165">`SecuritySafeCritical`: Typ lub element członkowski jest bezpieczny-krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d46e5-165">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="d46e5-166">Jednak typ lub element członkowski może być wywoływany z przezroczystego (częściowo zaufanego) kodu i jest tak jak każdy inny kod krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d46e5-166">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="d46e5-167">Kod musi być poddany inspekcji pod kątem bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="d46e5-167">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="d46e5-168">Zastępowanie wzorów</span><span class="sxs-lookup"><span data-stu-id="d46e5-168">Override Patterns</span></span>

<span data-ttu-id="d46e5-169">W poniższej tabeli przedstawiono metody przesłaniania dozwolone dla przezroczystości poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="d46e5-169">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="d46e5-170">Podstawowy element członkowski wirtualnego/interfejsu</span><span class="sxs-lookup"><span data-stu-id="d46e5-170">Base virtual/interface member</span></span>|<span data-ttu-id="d46e5-171">Zastąpienie/interfejs</span><span class="sxs-lookup"><span data-stu-id="d46e5-171">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="d46e5-172">Zasady dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="d46e5-172">Inheritance Rules</span></span>

<span data-ttu-id="d46e5-173">W tej sekcji następująca kolejność jest przypisana do `Transparent` , `Critical` i `SafeCritical` kodu na podstawie dostępu i możliwości:</span><span class="sxs-lookup"><span data-stu-id="d46e5-173">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="d46e5-174">Reguły dla typów: od lewej do prawej, dostęp staną się bardziej restrykcyjne.</span><span class="sxs-lookup"><span data-stu-id="d46e5-174">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="d46e5-175">Typy pochodne muszą być co najmniej tak restrykcyjne jak typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="d46e5-175">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="d46e5-176">Reguły dla metod: metody pochodne nie mogą zmieniać dostępności z metody podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d46e5-176">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="d46e5-177">W przypadku zachowania domyślnego wszystkie metody pochodne, które nie są adnotacjami, są `Transparent` .</span><span class="sxs-lookup"><span data-stu-id="d46e5-177">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="d46e5-178">Pochodne typów krytycznych powodują, że wyjątek jest zgłaszany, jeśli zastąpiona metoda nie jest jawnie oznaczona adnotacją `SecurityCritical` .</span><span class="sxs-lookup"><span data-stu-id="d46e5-178">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="d46e5-179">W poniższej tabeli przedstawiono wzorce dziedziczenia typów dozwolonych.</span><span class="sxs-lookup"><span data-stu-id="d46e5-179">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="d46e5-180">Klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="d46e5-180">Base class</span></span>|<span data-ttu-id="d46e5-181">Klasa pochodna może być</span><span class="sxs-lookup"><span data-stu-id="d46e5-181">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="d46e5-182">W poniższej tabeli przedstawiono wzorce dziedziczenia typu niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="d46e5-182">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="d46e5-183">Klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="d46e5-183">Base class</span></span>|<span data-ttu-id="d46e5-184">Klasa pochodna nie może być</span><span class="sxs-lookup"><span data-stu-id="d46e5-184">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="d46e5-185">W poniższej tabeli przedstawiono dozwolone wzorce dziedziczenia metody.</span><span class="sxs-lookup"><span data-stu-id="d46e5-185">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="d46e5-186">Metoda bazowa</span><span class="sxs-lookup"><span data-stu-id="d46e5-186">Base method</span></span>|<span data-ttu-id="d46e5-187">Pochodna Metoda może być</span><span class="sxs-lookup"><span data-stu-id="d46e5-187">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="d46e5-188">W poniższej tabeli przedstawiono niedozwolone wzorce dziedziczenia metody.</span><span class="sxs-lookup"><span data-stu-id="d46e5-188">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="d46e5-189">Metoda bazowa</span><span class="sxs-lookup"><span data-stu-id="d46e5-189">Base method</span></span>|<span data-ttu-id="d46e5-190">Metoda pochodna nie może być</span><span class="sxs-lookup"><span data-stu-id="d46e5-190">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="d46e5-191">Te reguły dziedziczenia mają zastosowanie do typów i elementów członkowskich poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="d46e5-191">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="d46e5-192">Typy zestawów na poziomie 1 mogą dziedziczyć z typów i elementów krytycznych zabezpieczeń poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="d46e5-192">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="d46e5-193">W związku z tym typy i elementy członkowskie poziomu 2 muszą mieć oddzielne żądania dziedziczenia dla dziedziczeń poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="d46e5-193">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="d46e5-194">Dodatkowe informacje i zasady</span><span class="sxs-lookup"><span data-stu-id="d46e5-194">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="d46e5-195">Obsługa LinkDemand</span><span class="sxs-lookup"><span data-stu-id="d46e5-195">LinkDemand Support</span></span>

<span data-ttu-id="d46e5-196">Model przezroczystości poziomu 2 zastępuje <xref:System.Security.Permissions.SecurityAction.LinkDemand> <xref:System.Security.SecurityCriticalAttribute> atrybut i.</span><span class="sxs-lookup"><span data-stu-id="d46e5-196">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="d46e5-197">W starszej wersji (poziom 1) kod <xref:System.Security.Permissions.SecurityAction.LinkDemand> jest automatycznie traktowany jako <xref:System.Security.Permissions.SecurityAction.Demand> .</span><span class="sxs-lookup"><span data-stu-id="d46e5-197">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="d46e5-198">Odbicie</span><span class="sxs-lookup"><span data-stu-id="d46e5-198">Reflection</span></span>

<span data-ttu-id="d46e5-199">Wywołanie krytycznej metody lub odczytanie pola krytycznego wyzwala żądanie pełnego zaufania (podobnie jak w przypadku wywołania metody prywatnej lub pola).</span><span class="sxs-lookup"><span data-stu-id="d46e5-199">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="d46e5-200">W związku z tym kod pełnego zaufania może wywołać metodę krytyczną, natomiast kod częściowego zaufania nie może.</span><span class="sxs-lookup"><span data-stu-id="d46e5-200">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="d46e5-201">Do przestrzeni nazw dodano następujące właściwości, <xref:System.Reflection> Aby określić, czy typ, metoda lub pole to `SecurityCritical` , `SecuritySafeCritical` , lub `SecurityTransparent` : <xref:System.Type.IsSecurityCritical%2A> , <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> , i <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A> .</span><span class="sxs-lookup"><span data-stu-id="d46e5-201">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="d46e5-202">Te właściwości umożliwiają określanie przejrzystości przy użyciu odbicia zamiast sprawdzania obecności atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d46e5-202">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="d46e5-203">Reguły przezroczystości są złożone i sprawdzanie, czy atrybut może być niewystarczający.</span><span class="sxs-lookup"><span data-stu-id="d46e5-203">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="d46e5-204">`SafeCritical`Metoda zwraca `true` dla obu <xref:System.Type.IsSecurityCritical%2A> i <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> , ponieważ `SafeCritical` jest rzeczywiście krytyczne (ma takie same możliwości jak kod krytyczny, ale może być wywoływana z kodu przezroczystego).</span><span class="sxs-lookup"><span data-stu-id="d46e5-204">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="d46e5-205">Metody dynamiczne dziedziczą przezroczystości modułów, do których są dołączone; nie dziedziczą przezroczystości typu (jeśli są dołączone do typu).</span><span class="sxs-lookup"><span data-stu-id="d46e5-205">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="d46e5-206">Pomiń weryfikację w trybie całkowitego zaufania</span><span class="sxs-lookup"><span data-stu-id="d46e5-206">Skip Verification in Full Trust</span></span>

<span data-ttu-id="d46e5-207">Możesz pominąć weryfikację dla w pełni zaufanych zestawów przezroczystych przez ustawienie <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> właściwości na `true` wartość w <xref:System.Security.SecurityRulesAttribute> atrybucie:</span><span class="sxs-lookup"><span data-stu-id="d46e5-207">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="d46e5-208"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A>Właściwość jest `false` Domyślnie, więc właściwość musi być ustawiona na, aby `true` pominąć weryfikację.</span><span class="sxs-lookup"><span data-stu-id="d46e5-208">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="d46e5-209">Należy to zrobić tylko w celach optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="d46e5-209">This should be done for optimization purposes only.</span></span> <span data-ttu-id="d46e5-210">Upewnij się, że przezroczysty kod w zestawie jest możliwy do zweryfikowania przy użyciu `transparent` opcji w [narzędziu PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d46e5-210">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d46e5-211">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d46e5-211">See also</span></span>

- [<span data-ttu-id="d46e5-212">Kod przezroczysty pod względem zabezpieczeń, poziom 1</span><span class="sxs-lookup"><span data-stu-id="d46e5-212">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="d46e5-213">Zmiany zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d46e5-213">Security Changes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
