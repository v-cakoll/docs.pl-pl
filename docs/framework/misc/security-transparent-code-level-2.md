---
title: Kod o przezroczystym poziomie bezpieczeństwa, poziom 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 12e991e4977b0866343158c05681ddf4bd0c869b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645731"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="12845-102">Kod o przezroczystym poziomie bezpieczeństwa, poziom 2</span><span class="sxs-lookup"><span data-stu-id="12845-102">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="12845-103">Przejrzystość poziomu 2 została wprowadzona w ramach .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="12845-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="12845-104">Trzy założenia tego modelu to przezroczysty kod, kod o znaczeniu krytycznym dla zabezpieczeń i kod krytyczny dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="12845-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="12845-105">Przezroczysty kod, w tym kod, który jest uruchomiony jako pełne zaufanie, można wywołać inny kod przezroczysty lub kod krytyczny dla bezpieczeństwa tylko.</span><span class="sxs-lookup"><span data-stu-id="12845-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="12845-106">Może wykonywać tylko akcje dozwolone przez zestaw uprawnień częściowego zaufania domeny (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="12845-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="12845-107">Nie można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="12845-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="12845-108">Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> lub podniesienie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="12845-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="12845-109">Zawierają niebezpieczny lub niemożliwy do wyczałkować kod.</span><span class="sxs-lookup"><span data-stu-id="12845-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="12845-110">Bezpośrednio wywołać kod krytyczny.</span><span class="sxs-lookup"><span data-stu-id="12845-110">Directly call critical code.</span></span>

  - <span data-ttu-id="12845-111">Wywołanie kodu macierzystego <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> lub kodu z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="12845-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="12845-112">Wywołanie członka, który jest <xref:System.Security.Permissions.SecurityAction.LinkDemand>chroniony przez .</span><span class="sxs-lookup"><span data-stu-id="12845-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="12845-113">Dziedzicz po typach krytycznych.</span><span class="sxs-lookup"><span data-stu-id="12845-113">Inherit from critical types.</span></span>

  <span data-ttu-id="12845-114">Ponadto metody przezroczyste nie można zastąpić krytycznych metod wirtualnych lub zaimplementować krytycznych metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="12845-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="12845-115">Bezpieczny kod krytyczny jest w pełni zaufany, ale można go wywołać za pomocą przezroczystego kodu.</span><span class="sxs-lookup"><span data-stu-id="12845-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="12845-116">Udostępnia ograniczoną powierzchnię kodu pełnego zaufania; weryfikacji poprawności i bezpieczeństwa w kodzie o znaczeniu krytycznym.</span><span class="sxs-lookup"><span data-stu-id="12845-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="12845-117">Kod krytyczny dla zabezpieczeń może wywołać dowolny kod i jest w pełni zaufany, ale nie można go wywołać za pomocą przezroczystego kodu.</span><span class="sxs-lookup"><span data-stu-id="12845-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="12845-118">Przykłady użycia i zachowania</span><span class="sxs-lookup"><span data-stu-id="12845-118">Usage Examples and Behaviors</span></span>

<span data-ttu-id="12845-119">Aby określić reguły programu .NET Framework 4 (przezroczystość poziomu 2), należy użyć następującej adnotacji dla zestawu:</span><span class="sxs-lookup"><span data-stu-id="12845-119">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="12845-120">Aby zablokować reguły programu .NET Framework 2.0 (przezroczystość poziomu 1), należy użyć następującej adnotacji:</span><span class="sxs-lookup"><span data-stu-id="12845-120">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="12845-121">Jeśli nie dodasz do adnotacji zestawu, reguły .NET Framework 4 są używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="12845-121">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="12845-122">Jednak zalecaną najlepszą praktyką <xref:System.Security.SecurityRulesAttribute> jest użycie atrybutu zamiast w zależności od wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="12845-122">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="12845-123">Adnotacja dla całego zestawu</span><span class="sxs-lookup"><span data-stu-id="12845-123">Assembly-wide Annotation</span></span>

<span data-ttu-id="12845-124">Następujące reguły mają zastosowanie do używania atrybutów na poziomie zestawu:</span><span class="sxs-lookup"><span data-stu-id="12845-124">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="12845-125">Brak atrybutów: Jeśli nie określisz żadnych atrybutów, środowisko wykonawcze interpretuje cały kod jako krytyczny dla zabezpieczeń, z wyjątkiem sytuacji, gdy krytyczne zabezpieczenia naruszają regułę dziedziczenia (na przykład podczas zastępowania lub implementowania przezroczystej metody wirtualnej lub interfejsu).</span><span class="sxs-lookup"><span data-stu-id="12845-125">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="12845-126">W takich przypadkach metody są bezpieczne krytyczne.</span><span class="sxs-lookup"><span data-stu-id="12845-126">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="12845-127">Określenie żadnego atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego określa reguły przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="12845-127">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="12845-128">`SecurityTransparent`: Cały kod jest przezroczysty; całe zgromadzenie nie zrobi nic uprzywilejowanego lub niebezpiecznego.</span><span class="sxs-lookup"><span data-stu-id="12845-128">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="12845-129">`SecurityCritical`: Cały kod, który jest wprowadzany przez typy w tym zestawie jest krytyczny; wszystkie inne kody są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="12845-129">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="12845-130">Ten scenariusz jest podobny do nie określania żadnych atrybutów; jednak środowisko uruchomieniowe języka wspólnego nie określa automatycznie reguł przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="12845-130">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="12845-131">Na przykład jeśli zastąpić metodę wirtualną lub abstrakcyjną lub zaimplementować metodę interfejsu, domyślnie ta metoda jest przezroczysta.</span><span class="sxs-lookup"><span data-stu-id="12845-131">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="12845-132">Należy jawnie dodawać adnotacje do metody jako `SecurityCritical` lub `SecuritySafeCritical`; w przeciwnym <xref:System.TypeLoadException> razie zostanie rzucony w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="12845-132">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="12845-133">Ta reguła ma również zastosowanie, gdy zarówno klasa podstawowa, jak i klasa pochodna znajdują się w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="12845-133">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="12845-134">`AllowPartiallyTrustedCallers`(tylko poziom 2): Wszystkie domyślne ustawienia kodu mają być przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="12845-134">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="12845-135">Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="12845-135">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="12845-136">W poniższej tabeli porównano zachowanie poziomu złożenia dla poziomu 2 z poziomem 1.</span><span class="sxs-lookup"><span data-stu-id="12845-136">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="12845-137">Atrybut zestawu</span><span class="sxs-lookup"><span data-stu-id="12845-137">Assembly attribute</span></span>|<span data-ttu-id="12845-138">Poziom 2</span><span class="sxs-lookup"><span data-stu-id="12845-138">Level 2</span></span>|<span data-ttu-id="12845-139">Poziom 1</span><span class="sxs-lookup"><span data-stu-id="12845-139">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="12845-140">Brak atrybutu w częściowo zaufanym zestawie</span><span class="sxs-lookup"><span data-stu-id="12845-140">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="12845-141">Typy i elementy członkowskie są domyślnie przezroczyste, ale mogą być krytyczne dla zabezpieczeń lub krytyczne dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="12845-141">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="12845-142">Wszystkie typy i elementy członkowskie są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="12845-142">All types and members are transparent.</span></span>|
|<span data-ttu-id="12845-143">Brak atrybutu</span><span class="sxs-lookup"><span data-stu-id="12845-143">No attribute</span></span>|<span data-ttu-id="12845-144">Określenie żadnego atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego określa reguły przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="12845-144">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="12845-145">Wszystkie typy i elementy członkowskie są krytyczne dla zabezpieczeń, z wyjątkiem sytuacji, gdy krytyczne zabezpieczenia naruszają regułę dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="12845-145">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="12845-146">W pełni zaufanym zestawie (w globalnej pamięci podręcznej `AppDomain`zestawów lub zidentyfikowane jako pełne zaufanie do) wszystkie typy są przezroczyste i wszystkie elementy członkowskie są bezpieczne-krytyczne.</span><span class="sxs-lookup"><span data-stu-id="12845-146">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="12845-147">Wszystkie typy i elementy członkowskie są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="12845-147">All types and members are transparent.</span></span>|<span data-ttu-id="12845-148">Wszystkie typy i elementy członkowskie są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="12845-148">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="12845-149">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="12845-149">Not applicable.</span></span>|<span data-ttu-id="12845-150">Wszystkie typy i elementy członkowskie są krytyczne dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="12845-150">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="12845-151">Cały kod, który jest wprowadzany przez typy w tym zestawie jest krytyczny; wszystkie inne kody są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="12845-151">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="12845-152">W przypadku zastąpienia metody wirtualnej lub abstrakcyjnej lub zaimplementowania metody `SecurityCritical` interfejsu `SecuritySafeCritical`należy jawnie opisać metodę jako lub .</span><span class="sxs-lookup"><span data-stu-id="12845-152">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="12845-153">Domyślnie wszystkie ustawienia kodu są przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="12845-153">All code defaults to transparent.</span></span> <span data-ttu-id="12845-154">Jednak poszczególne typy i elementy członkowskie mogą mieć inne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="12845-154">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="12845-155">Typ i adnotacja członkowska</span><span class="sxs-lookup"><span data-stu-id="12845-155">Type and Member Annotation</span></span>

<span data-ttu-id="12845-156">Atrybuty zabezpieczeń, które są stosowane do typu również stosuje się do elementów członkowskich, które są wprowadzane przez typ.</span><span class="sxs-lookup"><span data-stu-id="12845-156">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="12845-157">Jednak nie mają one zastosowania do wirtualnych lub abstrakcyjnych zastąpienia implementacji klasy podstawowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="12845-157">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="12845-158">Następujące reguły mają zastosowanie do używania atrybutów na poziomie typu i elementu członkowskiego:</span><span class="sxs-lookup"><span data-stu-id="12845-158">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="12845-159">`SecurityCritical`: Typ lub element członkowski jest krytyczny i może być wywoływany tylko przez kod pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="12845-159">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="12845-160">Metody, które są wprowadzane w typie krytycznym zabezpieczeń są krytyczne.</span><span class="sxs-lookup"><span data-stu-id="12845-160">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="12845-161">Metody wirtualne i abstrakcyjne, które są wprowadzane w klasach podstawowych lub interfejsach i zastępowane lub implementowane w klasie krytycznej zabezpieczeń są domyślnie przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="12845-161">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="12845-162">Muszą one być identyfikowane jako jeden `SecuritySafeCritical` lub `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="12845-162">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="12845-163">`SecuritySafeCritical`: Typ lub element członkowski jest krytyczny dla bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="12845-163">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="12845-164">Jednak typ lub element członkowski może być wywoływany z przezroczystego (częściowo zaufanego) kodu i jest tak samo zdolny, jak każdy inny kod krytyczny.</span><span class="sxs-lookup"><span data-stu-id="12845-164">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="12845-165">Kod musi być poddany inspekcji pod kątem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="12845-165">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="12845-166">Zastępowanie wzorów</span><span class="sxs-lookup"><span data-stu-id="12845-166">Override Patterns</span></span>

<span data-ttu-id="12845-167">W poniższej tabeli przedstawiono zastąpienia metody dozwolone dla przezroczystości poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="12845-167">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="12845-168">Podstawowy element członkowski wirtualny/interfejs</span><span class="sxs-lookup"><span data-stu-id="12845-168">Base virtual/interface member</span></span>|<span data-ttu-id="12845-169">Zastępowanie/interfejs</span><span class="sxs-lookup"><span data-stu-id="12845-169">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="12845-170">Zasady dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="12845-170">Inheritance Rules</span></span>

<span data-ttu-id="12845-171">W tej sekcji do programu `Transparent`przypisano `Critical`następującą kolejność i `SafeCritical` kod oparty na dostępie i możliwościach:</span><span class="sxs-lookup"><span data-stu-id="12845-171">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="12845-172">Reguły typów: przechodząc od lewej do prawej, dostęp staje się bardziej restrykcyjny.</span><span class="sxs-lookup"><span data-stu-id="12845-172">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="12845-173">Typy pochodne muszą być co najmniej tak restrykcyjne jak typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="12845-173">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="12845-174">Reguły dla metod: Metody pochodne nie można zmienić dostępność z metody podstawowej.</span><span class="sxs-lookup"><span data-stu-id="12845-174">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="12845-175">W przypadku zachowania domyślnego wszystkie metody pochodne, które nie są oś tym adnotacjami, są `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="12845-175">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="12845-176">Pochodne typów krytycznych powodują wyjątek, jeśli zastąpiona metoda nie jest jawnie opisywana jako `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="12845-176">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="12845-177">W poniższej tabeli przedstawiono wzorce dziedziczenia dozwolonego typu.</span><span class="sxs-lookup"><span data-stu-id="12845-177">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="12845-178">Klasa podstawowa</span><span class="sxs-lookup"><span data-stu-id="12845-178">Base class</span></span>|<span data-ttu-id="12845-179">Klasa pochodna może być</span><span class="sxs-lookup"><span data-stu-id="12845-179">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="12845-180">W poniższej tabeli przedstawiono wzorce dziedziczenia niedozwolonych typów.</span><span class="sxs-lookup"><span data-stu-id="12845-180">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="12845-181">Klasa podstawowa</span><span class="sxs-lookup"><span data-stu-id="12845-181">Base class</span></span>|<span data-ttu-id="12845-182">Klasa pochodna nie może być</span><span class="sxs-lookup"><span data-stu-id="12845-182">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="12845-183">W poniższej tabeli przedstawiono wzorce dziedziczenia dozwolonej metody.</span><span class="sxs-lookup"><span data-stu-id="12845-183">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="12845-184">Metoda podstawowa</span><span class="sxs-lookup"><span data-stu-id="12845-184">Base method</span></span>|<span data-ttu-id="12845-185">Metoda pochodna może być</span><span class="sxs-lookup"><span data-stu-id="12845-185">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="12845-186">W poniższej tabeli przedstawiono wzorce dziedziczenia niedozwolonych metod.</span><span class="sxs-lookup"><span data-stu-id="12845-186">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="12845-187">Metoda podstawowa</span><span class="sxs-lookup"><span data-stu-id="12845-187">Base method</span></span>|<span data-ttu-id="12845-188">Metoda pochodna nie może być</span><span class="sxs-lookup"><span data-stu-id="12845-188">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="12845-189">Te reguły dziedziczenia mają zastosowanie do typów poziomu 2 i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="12845-189">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="12845-190">Typy w zestawach poziomu 1 mogą dziedziczyć z typów i elementów członkowskich poziomu 2 o krytycznym znaczeniu dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="12845-190">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="12845-191">W związku z tym poziom 2 typów i członków musi mieć oddzielne żądania dziedziczenia dla dziedzicców poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="12845-191">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="12845-192">Dodatkowe informacje i zasady</span><span class="sxs-lookup"><span data-stu-id="12845-192">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="12845-193">Obsługa LinkDemand</span><span class="sxs-lookup"><span data-stu-id="12845-193">LinkDemand Support</span></span>

<span data-ttu-id="12845-194">Model przezroczystości poziomu 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> zastępuje <xref:System.Security.SecurityCriticalAttribute> ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="12845-194">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="12845-195">W starszym kodzie (poziom <xref:System.Security.Permissions.SecurityAction.LinkDemand> 1) a jest <xref:System.Security.Permissions.SecurityAction.Demand>automatycznie traktowany jako .</span><span class="sxs-lookup"><span data-stu-id="12845-195">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="12845-196">Odbicie</span><span class="sxs-lookup"><span data-stu-id="12845-196">Reflection</span></span>

<span data-ttu-id="12845-197">Wywoływanie metody krytycznej lub odczytywanie pola krytycznego wyzwala zapotrzebowanie na pełne zaufanie (tak, jakby wywoływano metodę prywatną lub pole).</span><span class="sxs-lookup"><span data-stu-id="12845-197">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="12845-198">W związku z tym kod pełnego zaufania można wywołać metodę krytyczną, podczas gdy kod częściowego zaufania nie może.</span><span class="sxs-lookup"><span data-stu-id="12845-198">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="12845-199">Następujące właściwości zostały dodane do <xref:System.Reflection> obszaru nazw, aby określić, czy `SecurityCritical` `SecuritySafeCritical`typ, `SecurityTransparent` <xref:System.Type.IsSecurityCritical%2A>metoda <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>lub <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>pole jest , , lub : , i .</span><span class="sxs-lookup"><span data-stu-id="12845-199">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="12845-200">Użyj tych właściwości, aby określić przezroczystość za pomocą odbicia zamiast sprawdzania obecności atrybutu.</span><span class="sxs-lookup"><span data-stu-id="12845-200">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="12845-201">Reguły przejrzystości są złożone, a sprawdzanie atrybutu może nie być wystarczające.</span><span class="sxs-lookup"><span data-stu-id="12845-201">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="12845-202">Metoda `SafeCritical` zwraca `true` dla <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>obu `SafeCritical` i , ponieważ jest rzeczywiście krytyczne (ma takie same możliwości jak kod krytyczny, ale może być wywoływana z przezroczystego kodu).</span><span class="sxs-lookup"><span data-stu-id="12845-202">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="12845-203">Metody dynamiczne dziedziczą przezroczystość modułów, do których są dołączone; nie dziedziczą przezroczystości typu (jeśli są dołączone do typu).</span><span class="sxs-lookup"><span data-stu-id="12845-203">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="12845-204">Pomiń weryfikację w trybie całkowitego zaufania</span><span class="sxs-lookup"><span data-stu-id="12845-204">Skip Verification in Full Trust</span></span>

<span data-ttu-id="12845-205">Weryfikację w pełni zaufanych zestawów <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> przezroczystych `true` można <xref:System.Security.SecurityRulesAttribute> pominąć, ustawiając właściwość w atrybucie:</span><span class="sxs-lookup"><span data-stu-id="12845-205">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="12845-206">Właściwość <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> `false` jest domyślnie, więc właściwość `true` musi być ustawiona na pominąć weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="12845-206">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="12845-207">Należy to zrobić tylko w celach optymalizacyjnych.</span><span class="sxs-lookup"><span data-stu-id="12845-207">This should be done for optimization purposes only.</span></span> <span data-ttu-id="12845-208">Należy upewnić się, że przezroczysty kod w `transparent` zestawie można zweryfikować za pomocą opcji w [narzędziu PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="12845-208">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12845-209">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12845-209">See also</span></span>

- [<span data-ttu-id="12845-210">Kod przezroczysty zabezpieczeń, poziom 1</span><span class="sxs-lookup"><span data-stu-id="12845-210">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="12845-211">Zmiany zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="12845-211">Security Changes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
