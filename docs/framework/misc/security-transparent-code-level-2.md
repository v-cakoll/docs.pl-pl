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
ms.openlocfilehash: 0f15c3bc097bc034db41c95cd168104b8435aaf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394143"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="6865b-102">Kod o przezroczystym poziomie bezpieczeństwa, poziom 2</span><span class="sxs-lookup"><span data-stu-id="6865b-102">Security-Transparent Code, Level 2</span></span>
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="6865b-103">Przezroczystość poziomu 2 została wprowadzona w systemie [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6865b-103">Level 2 transparency was introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="6865b-104">Trzy zasady tego modelu są kod o przezroczystym, bezpieczne-kod krytyczny dla zabezpieczeń i kod krytyczny dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6865b-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>  
  
-   <span data-ttu-id="6865b-105">Kod o przezroczystym, wraz z kodem, który działa jako pełne zaufanie, można wywołać innych kod o przezroczystym lub tylko kodu bezpieczny krytyczny dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6865b-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="6865b-106">Można wykonać tylko akcje dozwolone przez uprawnienia częściowej relacji zaufania domeny (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="6865b-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="6865b-107">Kod o przezroczystym nie może wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6865b-107">Transparent code cannot do the following:</span></span>  
  
    -   <span data-ttu-id="6865b-108">Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> lub podniesienie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="6865b-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>  
  
    -   <span data-ttu-id="6865b-109">Zawiera kod niezabezpieczony lub niemożliwy.</span><span class="sxs-lookup"><span data-stu-id="6865b-109">Contain unsafe or unverifiable code.</span></span>  
  
    -   <span data-ttu-id="6865b-110">Bezpośrednio wywoływać kod krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6865b-110">Directly call critical code.</span></span>  
  
    -   <span data-ttu-id="6865b-111">Wywołania kodu natywnego lub kodu z <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6865b-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>  
  
    -   <span data-ttu-id="6865b-112">Wywołanie elementu członkowskiego, który jest chroniony przez <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="6865b-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>  
  
    -   <span data-ttu-id="6865b-113">Dziedziczy z typu krytycznego.</span><span class="sxs-lookup"><span data-stu-id="6865b-113">Inherit from critical types.</span></span>  
  
     <span data-ttu-id="6865b-114">Ponadto jawne metody nie można zastąpić krytycznych metod wirtualnych lub implementować metod interfejsu krytyczne.</span><span class="sxs-lookup"><span data-stu-id="6865b-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>  
  
-   <span data-ttu-id="6865b-115">Bezpieczne krytyczne kod jest w pełni zaufany, ale jest wywołane przez kod przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="6865b-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="6865b-116">Udostępnia ona ograniczona powierzchni kodu pełnego zaufania. weryfikacji prawidłowości i zabezpieczeń się tak zdarzyć w kodzie bezpieczne krytyczne.</span><span class="sxs-lookup"><span data-stu-id="6865b-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>  
  
-   <span data-ttu-id="6865b-117">Kod krytyczny dla zabezpieczeń można wywołać żadnego kodu i jest w pełni zaufany, ale nie można wywołać przez kod przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="6865b-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>  
  
 <span data-ttu-id="6865b-118">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="6865b-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="6865b-119">Przykłady użycia i zachowania</span><span class="sxs-lookup"><span data-stu-id="6865b-119">Usage Examples and Behaviors</span></span>](#examples)  
  
-   [<span data-ttu-id="6865b-120">Zastąpienie wzorce</span><span class="sxs-lookup"><span data-stu-id="6865b-120">Override Patterns</span></span>](#override)  
  
-   [<span data-ttu-id="6865b-121">Dziedziczenie zasad</span><span class="sxs-lookup"><span data-stu-id="6865b-121">Inheritance Rules</span></span>](#inheritance)  
  
-   [<span data-ttu-id="6865b-122">Dodatkowe informacje i reguł</span><span class="sxs-lookup"><span data-stu-id="6865b-122">Additional Information and Rules</span></span>](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="6865b-123">Przykłady użycia i zachowania</span><span class="sxs-lookup"><span data-stu-id="6865b-123">Usage Examples and Behaviors</span></span>  
 <span data-ttu-id="6865b-124">Aby określić [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] reguły (przezroczystość poziomu 2), użyj następujących adnotacji dla zestawu:</span><span class="sxs-lookup"><span data-stu-id="6865b-124">To specify [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules (level 2 transparency), use the following annotation for an assembly:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 <span data-ttu-id="6865b-125">Aby zablokować do reguł .NET Framework 2.0 (poziom 1 przezroczystości), należy użyć następujących adnotacji:</span><span class="sxs-lookup"><span data-stu-id="6865b-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="6865b-126">Jeśli zestaw nie dodawać adnotacje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zasady są stosowane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6865b-126">If you do not annotate an assembly, the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules are used by default.</span></span> <span data-ttu-id="6865b-127">Jednak zalecanym najlepszym rozwiązaniem jest użycie <xref:System.Security.SecurityRulesAttribute> atrybutu zamiast w zależności od domyślnego.</span><span class="sxs-lookup"><span data-stu-id="6865b-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="6865b-128">Adnotacja całego zestawu</span><span class="sxs-lookup"><span data-stu-id="6865b-128">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="6865b-129">Korzystanie z atrybutów na poziomie zestawu mają zastosowanie następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="6865b-129">The following rules apply to the use of attributes at the assembly level:</span></span>  
  
-   <span data-ttu-id="6865b-130">Żadne atrybuty: Jeśli nie określono żadnych atrybutów, środowisko uruchomieniowe interpretuje całego kodu jako krytyczny dla zabezpieczeń, z wyjątkiem przypadków, gdy trwa krytyczny dla zabezpieczeń narusza regułę dziedziczenia (na przykład podczas implementowania przezroczysty lub zastępowania wirtualnych lub metody interfejsu ).</span><span class="sxs-lookup"><span data-stu-id="6865b-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="6865b-131">W takich przypadkach metody są bezpieczne krytyczne.</span><span class="sxs-lookup"><span data-stu-id="6865b-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="6865b-132">Określenie atrybutu nie powoduje, że środowisko uruchomieniowe języka wspólnego do określenia reguł przezroczystości dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="6865b-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>  
  
-   <span data-ttu-id="6865b-133">`SecurityTransparent`: Wszystkie kodu jest niewidoczny; cały zestaw nie ma żadnego znaczenia uprzywilejowanych lub niebezpieczna.</span><span class="sxs-lookup"><span data-stu-id="6865b-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>  
  
-   <span data-ttu-id="6865b-134">`SecurityCritical`: Kod wszystkie wprowadzone przez typy w tym zestawie jest krytyczne; inny kod jest niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="6865b-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="6865b-135">Ten scenariusz jest podobne do określania nie wszystkie atrybuty; środowisko uruchomieniowe języka wspólnego nie jednak automatycznie określić reguł przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="6865b-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="6865b-136">Na przykład jeśli zastąpić metodę wirtualne lub abstrakcyjne lub zaimplementować metodę interfejsu domyślnie, ta metoda jest niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="6865b-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="6865b-137">Należy jawnie dodawać adnotacje metodę jako `SecurityCritical` lub `SecuritySafeCritical`; w przeciwnym razie <xref:System.TypeLoadException> zostanie zgłoszony w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="6865b-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="6865b-138">Ta zasada ma zastosowanie również w przypadku zarówno klasy podstawowej i pochodnej klasy w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="6865b-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>  
  
-   <span data-ttu-id="6865b-139">`AllowPartiallyTrustedCallers` (poziom 2): wszystkie kodu, wartością domyślną będzie przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="6865b-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="6865b-140">Jednak poszczególne typy i składniki może mieć innych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6865b-140">However, individual types and members can have other attributes.</span></span>  
  
 <span data-ttu-id="6865b-141">W poniższej tabeli porównano zachowanie poziomu zestawu dla poziomu 2 z poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="6865b-141">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>  
  
|<span data-ttu-id="6865b-142">Atrybut zestawu</span><span class="sxs-lookup"><span data-stu-id="6865b-142">Assembly attribute</span></span>|<span data-ttu-id="6865b-143">Poziom 2</span><span class="sxs-lookup"><span data-stu-id="6865b-143">Level 2</span></span>|<span data-ttu-id="6865b-144">Poziom 1</span><span class="sxs-lookup"><span data-stu-id="6865b-144">Level 1</span></span>|  
|------------------------|-------------|-------------|  
|<span data-ttu-id="6865b-145">Brak atrybutu na częściowo zaufanym zestawie</span><span class="sxs-lookup"><span data-stu-id="6865b-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="6865b-146">Typy i składniki są domyślnie przezroczyste, ale może być krytyczny dla zabezpieczeń lub bezpieczny krytyczny dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6865b-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="6865b-147">Wszystkie elementy członkowskie i typy są niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="6865b-147">All types and members are transparent.</span></span>|  
|<span data-ttu-id="6865b-148">Brak atrybutu</span><span class="sxs-lookup"><span data-stu-id="6865b-148">No attribute</span></span>|<span data-ttu-id="6865b-149">Określenie atrybutu nie powoduje, że środowisko uruchomieniowe języka wspólnego do określenia reguł przezroczystości dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="6865b-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="6865b-150">Wszystkie typy i elementy członkowskie są krytyczny dla zabezpieczeń, z wyjątkiem przypadków, gdy trwa krytyczny dla zabezpieczeń narusza regułę dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="6865b-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="6865b-151">W pełni zaufanych zestawów (w globalnej pamięci podręcznej zestawów lub zidentyfikowane jako pełne zaufanie w `AppDomain`) wszystkie typy są niewidoczne i wszystkie elementy członkowskie są bezpieczny krytyczny dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6865b-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="6865b-152">Wszystkie elementy członkowskie i typy są niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="6865b-152">All types and members are transparent.</span></span>|<span data-ttu-id="6865b-153">Wszystkie elementy członkowskie i typy są niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="6865b-153">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="6865b-154">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="6865b-154">Not applicable.</span></span>|<span data-ttu-id="6865b-155">Wszystkie typy i elementy członkowskie są krytyczny dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6865b-155">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="6865b-156">Cały kod wprowadzone przez typy w tym zestawie ma kluczowe znaczenie; inny kod jest niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="6865b-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="6865b-157">Jeśli zastąpić metodę wirtualne lub abstrakcyjne lub zaimplementować metodę interfejsu, musi jawnie dodawania adnotacji do metody jako `SecurityCritical` lub `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="6865b-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="6865b-158">Wszystkie kodu, wartością domyślną będzie przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="6865b-158">All code defaults to transparent.</span></span> <span data-ttu-id="6865b-159">Jednak poszczególne typy i składniki może mieć innych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6865b-159">However, individual types and members can have other attributes.</span></span>|  
  
### <a name="type-and-member-annotation"></a><span data-ttu-id="6865b-160">Typ i adnotacja członkowska</span><span class="sxs-lookup"><span data-stu-id="6865b-160">Type and Member Annotation</span></span>  
 <span data-ttu-id="6865b-161">Atrybuty zabezpieczeń, które są stosowane do typu również zastosowanie do elementów członkowskich, które są wprowadzane według typu.</span><span class="sxs-lookup"><span data-stu-id="6865b-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="6865b-162">Jednak nie mają zastosowania do wirtualnego lub abstrakcyjny zastępuje podstawowej implementacji klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6865b-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="6865b-163">Korzystanie z atrybutów na poziomie typu i element członkowski mają zastosowanie następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="6865b-163">The following rules apply to the use of attributes at the type and member level:</span></span>  
  
-   <span data-ttu-id="6865b-164">`SecurityCritical`Typ lub element członkowski jest szczególnie ważne i może być wywoływana tylko przez kod pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="6865b-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="6865b-165">Metody, które zostały wprowadzone w typie krytyczny dla zabezpieczeń są krytyczne.</span><span class="sxs-lookup"><span data-stu-id="6865b-165">Methods that are introduced in a security-critical type are critical.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6865b-166">Wirtualny i abstrakcyjny metody, które wprowadzono w klasy podstawowej lub do interfejsów i przesłonięcia lub zaimplementowania w klasie krytyczny dla zabezpieczeń są niewidoczne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6865b-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="6865b-167">Zostaną one zidentyfikowane jako `SecuritySafeCritical` lub `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="6865b-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>  
  
-   <span data-ttu-id="6865b-168">`SecuritySafeCritical`Typ lub element członkowski jest bezpieczne krytyczne.</span><span class="sxs-lookup"><span data-stu-id="6865b-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="6865b-169">Jednak typu lub elementu członkowskiego może zostać wywołana z kod o przezroczystym (częściowo zaufanych) i może jako inne krytyczne kodu.</span><span class="sxs-lookup"><span data-stu-id="6865b-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="6865b-170">Kod musi podlegać inspekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6865b-170">The code must be audited for security.</span></span>  
  
 [<span data-ttu-id="6865b-171">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="6865b-171">Back to top</span></span>](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a><span data-ttu-id="6865b-172">Zastępowanie wzorów</span><span class="sxs-lookup"><span data-stu-id="6865b-172">Override Patterns</span></span>  
 <span data-ttu-id="6865b-173">W poniższej tabeli przedstawiono przesłonięcia metody dozwolone w przypadku przezroczystość poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="6865b-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>  
  
|<span data-ttu-id="6865b-174">Podstawowy wirtualny/elementu członkowskiego interfejsu</span><span class="sxs-lookup"><span data-stu-id="6865b-174">Base virtual/interface member</span></span>|<span data-ttu-id="6865b-175">Zastąpienie/interfejsu</span><span class="sxs-lookup"><span data-stu-id="6865b-175">Override/interface</span></span>|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [<span data-ttu-id="6865b-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="6865b-176">Back to top</span></span>](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a><span data-ttu-id="6865b-177">Zasady dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="6865b-177">Inheritance Rules</span></span>  
 <span data-ttu-id="6865b-178">W tej sekcji następującej kolejności jest przypisany do `Transparent`, `Critical`, i `SafeCritical` kodu na podstawie dostępu i możliwości:</span><span class="sxs-lookup"><span data-stu-id="6865b-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   <span data-ttu-id="6865b-179">Reguły dla typów: przechodząc od lewej do prawej, dostępu staje się bardziej restrykcyjne.</span><span class="sxs-lookup"><span data-stu-id="6865b-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="6865b-180">Typy pochodne musi być przynajmniej tak restrykcyjne jako typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="6865b-180">Derived types must be at least as restrictive as the base type.</span></span>  
  
-   <span data-ttu-id="6865b-181">Reguły dla metody: pochodnej metody nie można zmienić ułatwień dostępu z metody podstawowej.</span><span class="sxs-lookup"><span data-stu-id="6865b-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="6865b-182">Domyślne zachowanie są wszystkie metody pochodne, które nie mają adnotacje `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="6865b-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="6865b-183">Pochodne typy krytyczne spowodować wyjątek zostanie wygenerowany, jeśli przeciążonej nie ma jawnie adnotacji jako `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="6865b-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>  
  
 <span data-ttu-id="6865b-184">W poniższej tabeli przedstawiono dozwolone typu wzorce dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="6865b-184">The following table shows the allowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="6865b-185">Klasa podstawowa</span><span class="sxs-lookup"><span data-stu-id="6865b-185">Base class</span></span>|<span data-ttu-id="6865b-186">Klasa pochodna może być</span><span class="sxs-lookup"><span data-stu-id="6865b-186">Derived class can be</span></span>|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="6865b-187">W poniższej tabeli przedstawiono typu niedozwolonych wzorców dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="6865b-187">The following table shows the disallowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="6865b-188">Klasa podstawowa</span><span class="sxs-lookup"><span data-stu-id="6865b-188">Base class</span></span>|<span data-ttu-id="6865b-189">Klasa pochodna nie może być</span><span class="sxs-lookup"><span data-stu-id="6865b-189">Derived class cannot be</span></span>|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 <span data-ttu-id="6865b-190">W poniższej tabeli przedstawiono dozwolone metody wzorce dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="6865b-190">The following table shows the allowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="6865b-191">Base — metoda</span><span class="sxs-lookup"><span data-stu-id="6865b-191">Base method</span></span>|<span data-ttu-id="6865b-192">Metoda pochodna może być</span><span class="sxs-lookup"><span data-stu-id="6865b-192">Derived method can be</span></span>|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="6865b-193">W poniższej tabeli przedstawiono metodę niedozwolonych wzorców dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="6865b-193">The following table shows the disallowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="6865b-194">Base — metoda</span><span class="sxs-lookup"><span data-stu-id="6865b-194">Base method</span></span>|<span data-ttu-id="6865b-195">Metoda pochodna nie może być</span><span class="sxs-lookup"><span data-stu-id="6865b-195">Derived method cannot be</span></span>|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  <span data-ttu-id="6865b-196">Te reguły dziedziczenia stosuje się do poziomu 2 typów i członków.</span><span class="sxs-lookup"><span data-stu-id="6865b-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="6865b-197">Typów w zestawach poziom 1 może dziedziczyć typy krytyczny dla zabezpieczeń poziomu 2 i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6865b-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="6865b-198">W związku z tym poziom 2 typy i składniki musi mieć osobne inheritancedemand dla dziedziczenia poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="6865b-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>  
  
 [<span data-ttu-id="6865b-199">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="6865b-199">Back to top</span></span>](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a><span data-ttu-id="6865b-200">Dodatkowe informacje i zasady</span><span class="sxs-lookup"><span data-stu-id="6865b-200">Additional Information and Rules</span></span>  
  
### <a name="linkdemand-support"></a><span data-ttu-id="6865b-201">Obsługa LinkDemand</span><span class="sxs-lookup"><span data-stu-id="6865b-201">LinkDemand Support</span></span>  
 <span data-ttu-id="6865b-202">Zastępuje modelu przezroczystość poziomu 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> z <xref:System.Security.SecurityCriticalAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6865b-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="6865b-203">W kodzie starszych (poziom 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> jest automatycznie traktowane jako <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="6865b-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>  
  
### <a name="reflection"></a><span data-ttu-id="6865b-204">Odbicie</span><span class="sxs-lookup"><span data-stu-id="6865b-204">Reflection</span></span>  
 <span data-ttu-id="6865b-205">Wywoływanie metody krytycznych lub odczytywania pola krytyczne wyzwala zażąda pełnego zaufania (tak, jakby były wywoływania prywatnej metody lub pola).</span><span class="sxs-lookup"><span data-stu-id="6865b-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="6865b-206">Kod pełnego zaufania może wywołać metodę krytycznych, natomiast kod częściowego zaufania nie.</span><span class="sxs-lookup"><span data-stu-id="6865b-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>  
  
 <span data-ttu-id="6865b-207">Dodano następujące właściwości <xref:System.Reflection> przestrzeni nazw, aby określić, czy typ, metoda lub pole jest `SecurityCritical`, `SecuritySafeCritical`, lub `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, i <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="6865b-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="6865b-208">Użyj tych właściwości, aby określić przezroczystość przy użyciu odbicia zamiast sprawdzania pod kątem obecności atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6865b-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="6865b-209">Reguł przezroczystości są złożone i sprawdzanie dla atrybutu, nie może być wystarczające.</span><span class="sxs-lookup"><span data-stu-id="6865b-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6865b-210">A `SafeCritical` metoda zwraca `true` dla obu <xref:System.Type.IsSecurityCritical%2A> i <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, ponieważ `SafeCritical` jest w rzeczywistości krytyczne (ma takie same możliwości jak wykonywanie kodu krytycznego, ale może ona zostać wywołana z kod o przezroczystym).</span><span class="sxs-lookup"><span data-stu-id="6865b-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>  
  
 <span data-ttu-id="6865b-211">Metody dynamiczne dziedziczą przezroczystość moduły, w których są one dołączone do; nie dziedziczą przezroczystość typu (jeśli są one dołączone do typu).</span><span class="sxs-lookup"><span data-stu-id="6865b-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>  
  
### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="6865b-212">Pomiń weryfikację w trybie całkowitego zaufania</span><span class="sxs-lookup"><span data-stu-id="6865b-212">Skip Verification in Full Trust</span></span>  
 <span data-ttu-id="6865b-213">Można pominąć weryfikacji całkowicie zaufanych zestawów przezroczysty przez ustawienie <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> właściwości `true` w <xref:System.Security.SecurityRulesAttribute> atrybutu:</span><span class="sxs-lookup"><span data-stu-id="6865b-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <span data-ttu-id="6865b-214"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Właściwość jest `false` domyślnie, więc właściwości należy wybrać opcję `true` do pominięcia weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="6865b-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="6865b-215">Należy to zrobić tylko na potrzeby optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="6865b-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="6865b-216">Należy upewnić się, kod przezroczysty w zestawie jest możliwe do zweryfikowania przy użyciu `transparent` opcji [narzędzie PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6865b-217">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6865b-217">See Also</span></span>  
 [<span data-ttu-id="6865b-218">Kod o przezroczystym poziomie bezpieczeństwa, poziom 1</span><span class="sxs-lookup"><span data-stu-id="6865b-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [<span data-ttu-id="6865b-219">Zmiany zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6865b-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
