---
title: Kod o przezroczystym poziomie bezpieczeństwa, poziom 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62c25b14fa7b3867bbdbcb2f1e08cc16ce349e72
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156081"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="e1f50-102">Kod o przezroczystym poziomie bezpieczeństwa, poziom 2</span><span class="sxs-lookup"><span data-stu-id="e1f50-102">Security-Transparent Code, Level 2</span></span>
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="e1f50-103">Poziom 2 przejrzystości został wprowadzony w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e1f50-103">Level 2 transparency was introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="e1f50-104">Trzy założenia tego modelu to kod przezroczysty, kod zabezpieczenia bezpieczny krytyczny i kod zabezpieczenia krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1f50-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>  
  
-   <span data-ttu-id="e1f50-105">Przezroczysty kod, łącznie z kodem, który działa jako pełne zaufanie, wywołując inne kodu przezroczyste lub tylko kod zabezpieczenia bezpieczny krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1f50-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="e1f50-106">Można wykonać tylko akcje dozwolone przez uprawnienie częściowej relacji zaufania domeny (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="e1f50-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="e1f50-107">Przezroczysty kod nie są możliwe następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e1f50-107">Transparent code cannot do the following:</span></span>  
  
    -   <span data-ttu-id="e1f50-108">Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> lub podniesienie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="e1f50-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>  
  
    -   <span data-ttu-id="e1f50-109">Zawiera kod niebezpieczny lub niemożliwy do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="e1f50-109">Contain unsafe or unverifiable code.</span></span>  
  
    -   <span data-ttu-id="e1f50-110">Bezpośrednio Wywołaj kod krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1f50-110">Directly call critical code.</span></span>  
  
    -   <span data-ttu-id="e1f50-111">Wywoływanie kodu macierzystego lub kodu za pomocą <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e1f50-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>  
  
    -   <span data-ttu-id="e1f50-112">Wywołaj element członkowski, który jest chroniony przez <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="e1f50-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>  
  
    -   <span data-ttu-id="e1f50-113">Dziedziczy z typów krytycznych.</span><span class="sxs-lookup"><span data-stu-id="e1f50-113">Inherit from critical types.</span></span>  
  
     <span data-ttu-id="e1f50-114">Ponadto metody przezroczyste nie mogą zastąpić krytycznych metod wirtualnych lub implementować krytycznych metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e1f50-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>  
  
-   <span data-ttu-id="e1f50-115">Kod bezpieczny krytyczny jest w pełni zaufany, ale jest wywoływany przez kod przejrzysty.</span><span class="sxs-lookup"><span data-stu-id="e1f50-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="e1f50-116">Udostępnia ona ograniczona obszar powierzchni pełnego zaufania kodu; Weryfikacja poprawności i zabezpieczeń dojść w kod bezpieczny krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1f50-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>  
  
-   <span data-ttu-id="e1f50-117">Kod zabezpieczenia krytyczny może wywołać dowolny kod i jest w pełni zaufany, ale nie może być wywoływany przez kod przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="e1f50-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>  
  
 <span data-ttu-id="e1f50-118">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="e1f50-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="e1f50-119">Przykłady użycia i zachowania</span><span class="sxs-lookup"><span data-stu-id="e1f50-119">Usage Examples and Behaviors</span></span>](#examples)  
  
-   [<span data-ttu-id="e1f50-120">Zastępowanie wzorów</span><span class="sxs-lookup"><span data-stu-id="e1f50-120">Override Patterns</span></span>](#override)  
  
-   [<span data-ttu-id="e1f50-121">Zasady dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="e1f50-121">Inheritance Rules</span></span>](#inheritance)  
  
-   [<span data-ttu-id="e1f50-122">Dodatkowe informacje i zasady</span><span class="sxs-lookup"><span data-stu-id="e1f50-122">Additional Information and Rules</span></span>](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="e1f50-123">Przykłady użycia i zachowania</span><span class="sxs-lookup"><span data-stu-id="e1f50-123">Usage Examples and Behaviors</span></span>  
 <span data-ttu-id="e1f50-124">Aby określić [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] reguł (poziom 2 przezroczystości), użyj następujących adnotacji dla zestawu:</span><span class="sxs-lookup"><span data-stu-id="e1f50-124">To specify [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules (level 2 transparency), use the following annotation for an assembly:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 <span data-ttu-id="e1f50-125">Aby zablokować do reguł .NET Framework 2.0 (poziom 1 przejrzystości), należy użyć następujących adnotacji:</span><span class="sxs-lookup"><span data-stu-id="e1f50-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="e1f50-126">Jeśli zestaw nie dodawać adnotacje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] domyślnie są używane zasady.</span><span class="sxs-lookup"><span data-stu-id="e1f50-126">If you do not annotate an assembly, the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules are used by default.</span></span> <span data-ttu-id="e1f50-127">Jednak zalecanym najlepszym rozwiązaniem jest użycie <xref:System.Security.SecurityRulesAttribute> atrybutu zamiast w zależności od tego, wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="e1f50-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="e1f50-128">Adnotacja całego zestawu</span><span class="sxs-lookup"><span data-stu-id="e1f50-128">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="e1f50-129">Następujące reguły dotyczą użytkowania atrybuty na poziomie zestawu:</span><span class="sxs-lookup"><span data-stu-id="e1f50-129">The following rules apply to the use of attributes at the assembly level:</span></span>  
  
-   <span data-ttu-id="e1f50-130">Żadne atrybuty: Jeśli nie określisz żadnych atrybutów, środowisko uruchomieniowe interpretuje cały kod jako krytyczne dla zabezpieczeń, z wyjątkiem sytuacji, w którym są krytyczne dla bezpieczeństwa narusza regułę dziedziczenia (na przykład podczas implementowania przezroczyste lub zastępowania wirtualnych lub metody interfejsu).</span><span class="sxs-lookup"><span data-stu-id="e1f50-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="e1f50-131">W takich przypadkach metody są bezpieczny krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1f50-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="e1f50-132">Określanie bez atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego ustalić zasady przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="e1f50-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>  
  
-   `SecurityTransparent`<span data-ttu-id="e1f50-133">: Cały kod jest przezroczysty; cały zespół nie będzie ono działać uprzywilejowanych lub unsafe.</span><span class="sxs-lookup"><span data-stu-id="e1f50-133">: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>  
  
-   `SecurityCritical`<span data-ttu-id="e1f50-134">: Cały kod, który został wprowadzony przez typy w tym zestawie jest krytyczna; inny kod jest przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="e1f50-134">: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="e1f50-135">Ten scenariusz jest podobne do określania nie wszelkie atrybuty; jednak automatycznie środowiska uruchomieniowego języka wspólnego nie określa zasady przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="e1f50-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="e1f50-136">Na przykład jeśli zastąpienie metody wirtualne ani abstrakcyjne lub implementuje metodę interfejsu, domyślnie tej metody jest przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="e1f50-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="e1f50-137">Należy jawnie dodać adnotacje metodę jako `SecurityCritical` lub `SecuritySafeCritical`; w przeciwnym razie <xref:System.TypeLoadException> zostanie wyrzucony w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="e1f50-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="e1f50-138">Ta zasada ma zastosowanie, gdy klasa bazowa i Klasa pochodna znajdują się w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="e1f50-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>  
  
-   `AllowPartiallyTrustedCallers` <span data-ttu-id="e1f50-139">(tylko poziom 2): Wartość domyślna to przezroczyste wszystkie kodu.</span><span class="sxs-lookup"><span data-stu-id="e1f50-139">(level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="e1f50-140">Jednak poszczególne typy i składowe mogą mieć inne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="e1f50-140">However, individual types and members can have other attributes.</span></span>  
  
 <span data-ttu-id="e1f50-141">W poniższej tabeli porównano zachowania poziomu zestawu na poziomie 2 z poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="e1f50-141">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>  
  
|<span data-ttu-id="e1f50-142">Atrybutu zestawu</span><span class="sxs-lookup"><span data-stu-id="e1f50-142">Assembly attribute</span></span>|<span data-ttu-id="e1f50-143">Poziom 2</span><span class="sxs-lookup"><span data-stu-id="e1f50-143">Level 2</span></span>|<span data-ttu-id="e1f50-144">Poziom 1</span><span class="sxs-lookup"><span data-stu-id="e1f50-144">Level 1</span></span>|  
|------------------------|-------------|-------------|  
|<span data-ttu-id="e1f50-145">Brak atrybutu w częściowo zaufanym zestawie</span><span class="sxs-lookup"><span data-stu-id="e1f50-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="e1f50-146">Typy i elementy członkowskie są domyślnie przejrzysty, ale może być krytyczne dla bezpieczeństwa lub zabezpieczenia bezpieczny krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1f50-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="e1f50-147">Wszystkie typy i elementy członkowskie są niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="e1f50-147">All types and members are transparent.</span></span>|  
|<span data-ttu-id="e1f50-148">Brak atrybutu</span><span class="sxs-lookup"><span data-stu-id="e1f50-148">No attribute</span></span>|<span data-ttu-id="e1f50-149">Określanie bez atrybutu powoduje, że środowisko uruchomieniowe języka wspólnego ustalić zasady przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="e1f50-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="e1f50-150">Wszystkie typy i elementy członkowskie są krytyczne dla bezpieczeństwa, z wyjątkiem sytuacji, w którym są krytyczne dla bezpieczeństwa narusza regułę dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e1f50-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="e1f50-151">W pełni zaufanym zestawie (w globalnej pamięci podręcznej lub zidentyfikowane jako pełne zaufanie w `AppDomain`) wszystkie typy są niewidoczne, a wszystkie elementy członkowskie są zabezpieczenia bezpieczny krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1f50-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="e1f50-152">Wszystkie typy i elementy członkowskie są niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="e1f50-152">All types and members are transparent.</span></span>|<span data-ttu-id="e1f50-153">Wszystkie typy i elementy członkowskie są niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="e1f50-153">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="e1f50-154">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e1f50-154">Not applicable.</span></span>|<span data-ttu-id="e1f50-155">Wszystkie typy i elementy członkowskie są krytyczne dla bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="e1f50-155">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="e1f50-156">Cały kod, który został wprowadzony przez typy w tym zestawie jest krytyczna; inny kod jest przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="e1f50-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="e1f50-157">Jeśli zastępują metody wirtualne ani abstrakcyjne lub implementować metody interfejsu muszą jawnie dodawania adnotacji do metody jako `SecurityCritical` lub `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="e1f50-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="e1f50-158">Wartość domyślna to przezroczyste wszystkie kodu.</span><span class="sxs-lookup"><span data-stu-id="e1f50-158">All code defaults to transparent.</span></span> <span data-ttu-id="e1f50-159">Jednak poszczególne typy i składowe mogą mieć inne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="e1f50-159">However, individual types and members can have other attributes.</span></span>|  
  
### <a name="type-and-member-annotation"></a><span data-ttu-id="e1f50-160">Typ i adnotacja członkowska</span><span class="sxs-lookup"><span data-stu-id="e1f50-160">Type and Member Annotation</span></span>  
 <span data-ttu-id="e1f50-161">Atrybuty zabezpieczeń, które są stosowane do typu, która jest również zastosowanie do elementów członkowskich, które są wprowadzone przez tego typu.</span><span class="sxs-lookup"><span data-stu-id="e1f50-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="e1f50-162">Jednak nie mają zastosowania do programu virtual lub abstract zastępuje podstawowej implementacji klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e1f50-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="e1f50-163">Następujące reguły dotyczą użytkowania atrybuty na poziomie typów i elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="e1f50-163">The following rules apply to the use of attributes at the type and member level:</span></span>  
  
-   `SecurityCritical`<span data-ttu-id="e1f50-164">: Typ lub element członkowski ma krytyczne znaczenie i może być wywoływany tylko przez kod pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="e1f50-164">: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="e1f50-165">Metody, które zostały wprowadzone w typie, zabezpieczenia krytyczny są niezwykle ważne.</span><span class="sxs-lookup"><span data-stu-id="e1f50-165">Methods that are introduced in a security-critical type are critical.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e1f50-166">Wirtualny i abstrakcyjny metody, które są wprowadzone w klasach bazowych lub interfejsów i zastąpione lub zaimplementowaniu w klasie zabezpieczenia krytyczny są niewidoczne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1f50-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="e1f50-167">Musi być identyfikowany jako `SecuritySafeCritical` lub `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="e1f50-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>  
  
-   `SecuritySafeCritical`<span data-ttu-id="e1f50-168">: Typ lub składowa jest bezpieczny krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1f50-168">: The type or member is safe-critical.</span></span> <span data-ttu-id="e1f50-169">Jednak typ lub element członkowski może zostać wywołana z przezroczystym kodzie (częściowo zaufanym) i może się tak jak każdy inny kod krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1f50-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="e1f50-170">Kod musi inspekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e1f50-170">The code must be audited for security.</span></span>  
  
 [<span data-ttu-id="e1f50-171">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="e1f50-171">Back to top</span></span>](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a><span data-ttu-id="e1f50-172">Zastępowanie wzorów</span><span class="sxs-lookup"><span data-stu-id="e1f50-172">Override Patterns</span></span>  
 <span data-ttu-id="e1f50-173">W poniższej tabeli przedstawiono zastąpienia metody, które mogą uzyskać przezroczystość poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="e1f50-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>  
  
|<span data-ttu-id="e1f50-174">Podstawowy wirtualnej składowej/składowej interfejsu</span><span class="sxs-lookup"><span data-stu-id="e1f50-174">Base virtual/interface member</span></span>|<span data-ttu-id="e1f50-175">Zastąpienie/interfejsu</span><span class="sxs-lookup"><span data-stu-id="e1f50-175">Override/interface</span></span>|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [<span data-ttu-id="e1f50-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="e1f50-176">Back to top</span></span>](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a><span data-ttu-id="e1f50-177">Zasady dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="e1f50-177">Inheritance Rules</span></span>  
 <span data-ttu-id="e1f50-178">W tej sekcji następującej kolejności jest przypisany do `Transparent`, `Critical`, i `SafeCritical` kodu na podstawie dostępu i możliwości:</span><span class="sxs-lookup"><span data-stu-id="e1f50-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   <span data-ttu-id="e1f50-179">Reguły dla typów: Przechodzenie od lewej do prawej, dostępu staje się bardziej restrykcyjne.</span><span class="sxs-lookup"><span data-stu-id="e1f50-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="e1f50-180">Typy pochodne musi być co najmniej tak restrykcyjne jako typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="e1f50-180">Derived types must be at least as restrictive as the base type.</span></span>  
  
-   <span data-ttu-id="e1f50-181">Reguły dla metod: Metody pochodnej nie można zmienić dostępności z metody podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e1f50-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="e1f50-182">Domyślne zachowanie wszystkich pochodnych metody, które nie posiadają adnotację, są `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="e1f50-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="e1f50-183">Pochodne typy krytyczne spowodować wyjątek zostanie wygenerowany, jeśli zastąpiona metoda nie jest jawnie oznaczona jako `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="e1f50-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>  
  
 <span data-ttu-id="e1f50-184">W poniższej tabeli przedstawiono dozwolone typu wzorców dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e1f50-184">The following table shows the allowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="e1f50-185">Klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="e1f50-185">Base class</span></span>|<span data-ttu-id="e1f50-186">Klasa pochodna może być</span><span class="sxs-lookup"><span data-stu-id="e1f50-186">Derived class can be</span></span>|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="e1f50-187">W poniższej tabeli przedstawiono typ niedozwolonych wzorców dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e1f50-187">The following table shows the disallowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="e1f50-188">Klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="e1f50-188">Base class</span></span>|<span data-ttu-id="e1f50-189">Klasa pochodna nie może być</span><span class="sxs-lookup"><span data-stu-id="e1f50-189">Derived class cannot be</span></span>|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 <span data-ttu-id="e1f50-190">W poniższej tabeli przedstawiono dozwolone metody wzorców dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e1f50-190">The following table shows the allowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="e1f50-191">Base — metoda</span><span class="sxs-lookup"><span data-stu-id="e1f50-191">Base method</span></span>|<span data-ttu-id="e1f50-192">Pochodna metoda może być</span><span class="sxs-lookup"><span data-stu-id="e1f50-192">Derived method can be</span></span>|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="e1f50-193">W poniższej tabeli przedstawiono metody niedozwolonych wzorców dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e1f50-193">The following table shows the disallowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="e1f50-194">Base — metoda</span><span class="sxs-lookup"><span data-stu-id="e1f50-194">Base method</span></span>|<span data-ttu-id="e1f50-195">Metoda pochodnej nie może być</span><span class="sxs-lookup"><span data-stu-id="e1f50-195">Derived method cannot be</span></span>|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  <span data-ttu-id="e1f50-196">Te reguły dziedziczenia stosuje się do poziomu 2 typów i członków.</span><span class="sxs-lookup"><span data-stu-id="e1f50-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="e1f50-197">Typów w zestawach poziomu 1 może dziedziczyć z poziomu 2 krytyczne dla bezpieczeństwa typy i elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="e1f50-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="e1f50-198">W związku z tym poziom 2 typy i elementy Członkowskie musi mieć osobne inheritancedemand dotyczące obiektów dziedziczących poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="e1f50-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>  
  
 [<span data-ttu-id="e1f50-199">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="e1f50-199">Back to top</span></span>](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a><span data-ttu-id="e1f50-200">Dodatkowe informacje i zasady</span><span class="sxs-lookup"><span data-stu-id="e1f50-200">Additional Information and Rules</span></span>  
  
### <a name="linkdemand-support"></a><span data-ttu-id="e1f50-201">Obsługa LinkDemand</span><span class="sxs-lookup"><span data-stu-id="e1f50-201">LinkDemand Support</span></span>  
 <span data-ttu-id="e1f50-202">Zastępuje poziomie 2 modelu przezroczystości <xref:System.Security.Permissions.SecurityAction.LinkDemand> z <xref:System.Security.SecurityCriticalAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e1f50-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="e1f50-203">W kodzie starszej wersji (poziom 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> jest automatycznie traktowany jako <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="e1f50-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>  
  
### <a name="reflection"></a><span data-ttu-id="e1f50-204">Odbicie</span><span class="sxs-lookup"><span data-stu-id="e1f50-204">Reflection</span></span>  
 <span data-ttu-id="e1f50-205">Wywoływanie metody krytyczne lub pola Krytyczne do czytania wyzwala żądanie, aby uzyskać pełne zaufanie (tak, jakby były wywoływanie metody prywatnej lub pola).</span><span class="sxs-lookup"><span data-stu-id="e1f50-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="e1f50-206">Pełni zaufany kod, można wywołać metody krytycznej, natomiast nie częściowo zaufanemu kodowi.</span><span class="sxs-lookup"><span data-stu-id="e1f50-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>  
  
 <span data-ttu-id="e1f50-207">Następujące właściwości zostały dodane do <xref:System.Reflection> przestrzeń nazw w celu ustalenia, czy typ, metoda lub pole jest `SecurityCritical`, `SecuritySafeCritical`, lub `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, i <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1f50-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="e1f50-208">Użyj tych właściwości, aby określić przezroczystość przy użyciu odbicia zamiast sprawdzania pod kątem obecności atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e1f50-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="e1f50-209">Zasady przezroczystości są złożone i sprawdzanie, czy atrybut może nie być wystarczające.</span><span class="sxs-lookup"><span data-stu-id="e1f50-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1f50-210">A `SafeCritical` metoda zwraca `true` dla obu <xref:System.Type.IsSecurityCritical%2A> i <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, ponieważ `SafeCritical` bezwzględnie rzeczywiście (ma takie same możliwości jak kodu krytycznego, ale może ona zostać wywołana z przezroczystego kodu).</span><span class="sxs-lookup"><span data-stu-id="e1f50-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>  
  
 <span data-ttu-id="e1f50-211">Metody dynamiczne dziedziczą przezroczystość moduły, w których są podłączone. nie dziedziczą przezroczystości typu (jeśli są one dołączone do typu).</span><span class="sxs-lookup"><span data-stu-id="e1f50-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>  
  
### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="e1f50-212">Pomiń weryfikację w trybie całkowitego zaufania</span><span class="sxs-lookup"><span data-stu-id="e1f50-212">Skip Verification in Full Trust</span></span>  
 <span data-ttu-id="e1f50-213">Możesz pominąć weryfikację dla całkowicie zaufanych zestawów przezroczyste, ustawiając <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> właściwości `true` w <xref:System.Security.SecurityRulesAttribute> atrybutu:</span><span class="sxs-lookup"><span data-stu-id="e1f50-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <span data-ttu-id="e1f50-214"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Właściwość `false` domyślnie, więc właściwość musi być równa `true` Aby pominąć weryfikację.</span><span class="sxs-lookup"><span data-stu-id="e1f50-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="e1f50-215">To powinno odbywać się wyłącznie do celów optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="e1f50-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="e1f50-216">Należy upewnić się, że przezroczysty kod w zestawie jest możliwe do zweryfikowania przy użyciu `transparent` opcji [narzędzie PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e1f50-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f50-217">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1f50-217">See also</span></span>

- [<span data-ttu-id="e1f50-218">Kod o przezroczystym poziomie bezpieczeństwa, poziom 1</span><span class="sxs-lookup"><span data-stu-id="e1f50-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [<span data-ttu-id="e1f50-219">Zmiany zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e1f50-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
