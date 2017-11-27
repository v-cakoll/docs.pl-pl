---
title: "Ogólne konwencje nazewnictwa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dde3adbb7640978829dea4b977ed14eec38a9077
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="general-naming-conventions"></a><span data-ttu-id="a9876-102">Ogólne konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="a9876-102">General Naming Conventions</span></span>
<span data-ttu-id="a9876-103">W tej sekcji opisano ogólne konwencji nazewnictwa odnoszą się do wyboru word wskazówki na temat używania skrótów i akronimów i zalecenia dotyczące należy unikać nazw specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="a9876-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>  
  
## <a name="word-choice"></a><span data-ttu-id="a9876-104">Wybór programu Word</span><span class="sxs-lookup"><span data-stu-id="a9876-104">Word Choice</span></span>  
 <span data-ttu-id="a9876-105">**CZY ✓** wybrać łatwo odczytać identyfikatora nazwy.</span><span class="sxs-lookup"><span data-stu-id="a9876-105">**✓ DO** choose easily readable identifier names.</span></span>  
  
 <span data-ttu-id="a9876-106">Na przykład właściwość o nazwie `HorizontalAlignment` jest angielski czytelność niż `AlignmentHorizontal`.</span><span class="sxs-lookup"><span data-stu-id="a9876-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>  
  
 <span data-ttu-id="a9876-107">**CZY ✓** Preferuj czytelności za pośrednictwem skrócenia.</span><span class="sxs-lookup"><span data-stu-id="a9876-107">**✓ DO** favor readability over brevity.</span></span>  
  
 <span data-ttu-id="a9876-108">Nazwa właściwości `CanScrollHorizontally` jest lepszym rozwiązaniem niż `ScrollableX` (zasłoniętej odwołania do osi x).</span><span class="sxs-lookup"><span data-stu-id="a9876-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>  
  
 <span data-ttu-id="a9876-109">**X nie** użyj podkreślenia, łączniki lub innych znaków innych niż alfanumeryczne.</span><span class="sxs-lookup"><span data-stu-id="a9876-109">**X DO NOT** use underscores, hyphens, or any other nonalphanumeric characters.</span></span>  
  
 <span data-ttu-id="a9876-110">**X nie** Użyj notacji Węgierskiej.</span><span class="sxs-lookup"><span data-stu-id="a9876-110">**X DO NOT** use Hungarian notation.</span></span>  
  
 <span data-ttu-id="a9876-111">**X należy UNIKAĆ** przy użyciu identyfikatorów, które powodują konflikt z słów kluczowych z powszechnie używane języki programowania.</span><span class="sxs-lookup"><span data-stu-id="a9876-111">**X AVOID** using identifiers that conflict with keywords of widely used programming languages.</span></span>  
  
 <span data-ttu-id="a9876-112">Zgodnie z zasady 4 wspólnej specyfikacji języka (CLS) wszystkie języki zgodne podać mechanizm umożliwiający dostęp do nazwanego elementy, które korzystają ze słowem kluczowym tego języka jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="a9876-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="a9876-113">C#, na przykład używa znaku jako mechanizmu ucieczki w tym przypadku @.</span><span class="sxs-lookup"><span data-stu-id="a9876-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="a9876-114">Jednak nadal jest dobrym rozwiązaniem, aby uniknąć typowe słowa kluczowe, ponieważ jest znacznie trudniejsze do metody za pomocą sekwencji unikowej niż jeden bez niego.</span><span class="sxs-lookup"><span data-stu-id="a9876-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>  
  
## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="a9876-115">Za pomocą skrótów i akronimów</span><span class="sxs-lookup"><span data-stu-id="a9876-115">Using Abbreviations and Acronyms</span></span>  
 <span data-ttu-id="a9876-116">**X nie** Użyj skrótów lub skrótów jako część nazwy identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="a9876-116">**X DO NOT** use abbreviations or contractions as part of identifier names.</span></span>  
  
 <span data-ttu-id="a9876-117">Na przykład użyć `GetWindow` zamiast `GetWin`.</span><span class="sxs-lookup"><span data-stu-id="a9876-117">For example, use `GetWindow` rather than `GetWin`.</span></span>  
  
 <span data-ttu-id="a9876-118">**X nie** używać żadnych skrótów, które nie są powszechnie zaakceptowany, a nawet wtedy, gdy są one, tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="a9876-118">**X DO NOT** use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>  
  
## <a name="avoiding-language-specific-names"></a><span data-ttu-id="a9876-119">Unikanie specyficzny dla języka nazw</span><span class="sxs-lookup"><span data-stu-id="a9876-119">Avoiding Language-Specific Names</span></span>  
 <span data-ttu-id="a9876-120">**CZY ✓** użycie nazwy semantycznie interesujące zamiast słowa kluczowe specyficzne dla języka dla nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="a9876-120">**✓ DO** use semantically interesting names rather than language-specific keywords for type names.</span></span>  
  
 <span data-ttu-id="a9876-121">Na przykład `GetLength` jest nazwą lepszą niż `GetInt`.</span><span class="sxs-lookup"><span data-stu-id="a9876-121">For example, `GetLength` is a better name than `GetInt`.</span></span>  
  
 <span data-ttu-id="a9876-122">**CZY ✓** Użyj nazwy ogólnej typu CLR, a nie nazwę specyficzne dla języka w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego poza jego typu.</span><span class="sxs-lookup"><span data-stu-id="a9876-122">**✓ DO** use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>  
  
 <span data-ttu-id="a9876-123">Na przykład metoda konwertowania na <xref:System.Int64> powinno być nazwanym `ToInt64`, a nie `ToLong` (ponieważ <xref:System.Int64> jest nazwą CLR dla języka C# — określonego aliasu `long`).</span><span class="sxs-lookup"><span data-stu-id="a9876-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="a9876-124">W poniższej tabeli przedstawiono kilka typów danych podstawowych za pomocą nazwy typu CLR (a także odpowiedniej nazwy typu dla C#, Visual Basic i C++).</span><span class="sxs-lookup"><span data-stu-id="a9876-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>  
  
|<span data-ttu-id="a9876-125">C#</span><span class="sxs-lookup"><span data-stu-id="a9876-125">C#</span></span>|<span data-ttu-id="a9876-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9876-126">Visual Basic</span></span>|<span data-ttu-id="a9876-127">C++</span><span class="sxs-lookup"><span data-stu-id="a9876-127">C++</span></span>|<span data-ttu-id="a9876-128">CLR</span><span class="sxs-lookup"><span data-stu-id="a9876-128">CLR</span></span>|  
|---------|------------------|-----------|---------|  
|<span data-ttu-id="a9876-129">**sbyte —**</span><span class="sxs-lookup"><span data-stu-id="a9876-129">**sbyte**</span></span>|<span data-ttu-id="a9876-130">**Sbyte —**</span><span class="sxs-lookup"><span data-stu-id="a9876-130">**SByte**</span></span>|<span data-ttu-id="a9876-131">**char**</span><span class="sxs-lookup"><span data-stu-id="a9876-131">**char**</span></span>|<span data-ttu-id="a9876-132">**Sbyte —**</span><span class="sxs-lookup"><span data-stu-id="a9876-132">**SByte**</span></span>|  
|<span data-ttu-id="a9876-133">**bajtów**</span><span class="sxs-lookup"><span data-stu-id="a9876-133">**byte**</span></span>|<span data-ttu-id="a9876-134">**Bajtów**</span><span class="sxs-lookup"><span data-stu-id="a9876-134">**Byte**</span></span>|<span data-ttu-id="a9876-135">**char bez znaku**</span><span class="sxs-lookup"><span data-stu-id="a9876-135">**unsigned char**</span></span>|<span data-ttu-id="a9876-136">**Bajtów**</span><span class="sxs-lookup"><span data-stu-id="a9876-136">**Byte**</span></span>|  
|<span data-ttu-id="a9876-137">**krótki**</span><span class="sxs-lookup"><span data-stu-id="a9876-137">**short**</span></span>|<span data-ttu-id="a9876-138">**Krótki**</span><span class="sxs-lookup"><span data-stu-id="a9876-138">**Short**</span></span>|<span data-ttu-id="a9876-139">**krótki**</span><span class="sxs-lookup"><span data-stu-id="a9876-139">**short**</span></span>|<span data-ttu-id="a9876-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="a9876-140">**Int16**</span></span>|  
|<span data-ttu-id="a9876-141">**ushort**</span><span class="sxs-lookup"><span data-stu-id="a9876-141">**ushort**</span></span>|<span data-ttu-id="a9876-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="a9876-142">**UInt16**</span></span>|<span data-ttu-id="a9876-143">**short bez znaku**</span><span class="sxs-lookup"><span data-stu-id="a9876-143">**unsigned short**</span></span>|<span data-ttu-id="a9876-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="a9876-144">**UInt16**</span></span>|  
|<span data-ttu-id="a9876-145">**int**</span><span class="sxs-lookup"><span data-stu-id="a9876-145">**int**</span></span>|<span data-ttu-id="a9876-146">**Liczba całkowita**</span><span class="sxs-lookup"><span data-stu-id="a9876-146">**Integer**</span></span>|<span data-ttu-id="a9876-147">**int**</span><span class="sxs-lookup"><span data-stu-id="a9876-147">**int**</span></span>|<span data-ttu-id="a9876-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="a9876-148">**Int32**</span></span>|  
|<span data-ttu-id="a9876-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="a9876-149">**uint**</span></span>|<span data-ttu-id="a9876-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="a9876-150">**UInt32**</span></span>|<span data-ttu-id="a9876-151">**unsigned int**</span><span class="sxs-lookup"><span data-stu-id="a9876-151">**unsigned int**</span></span>|<span data-ttu-id="a9876-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="a9876-152">**UInt32**</span></span>|  
|<span data-ttu-id="a9876-153">**długa**</span><span class="sxs-lookup"><span data-stu-id="a9876-153">**long**</span></span>|<span data-ttu-id="a9876-154">**Długa**</span><span class="sxs-lookup"><span data-stu-id="a9876-154">**Long**</span></span>|<span data-ttu-id="a9876-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="a9876-155">**__int64**</span></span>|<span data-ttu-id="a9876-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="a9876-156">**Int64**</span></span>|  
|<span data-ttu-id="a9876-157">**ulong**</span><span class="sxs-lookup"><span data-stu-id="a9876-157">**ulong**</span></span>|<span data-ttu-id="a9876-158">**UInt64 —**</span><span class="sxs-lookup"><span data-stu-id="a9876-158">**UInt64**</span></span>|<span data-ttu-id="a9876-159">**__int64 bez znaku**</span><span class="sxs-lookup"><span data-stu-id="a9876-159">**unsigned __int64**</span></span>|<span data-ttu-id="a9876-160">**UInt64 —**</span><span class="sxs-lookup"><span data-stu-id="a9876-160">**UInt64**</span></span>|  
|<span data-ttu-id="a9876-161">**float**</span><span class="sxs-lookup"><span data-stu-id="a9876-161">**float**</span></span>|<span data-ttu-id="a9876-162">**Pojedynczy**</span><span class="sxs-lookup"><span data-stu-id="a9876-162">**Single**</span></span>|<span data-ttu-id="a9876-163">**float**</span><span class="sxs-lookup"><span data-stu-id="a9876-163">**float**</span></span>|<span data-ttu-id="a9876-164">**Pojedynczy**</span><span class="sxs-lookup"><span data-stu-id="a9876-164">**Single**</span></span>|  
|<span data-ttu-id="a9876-165">**podwójne**</span><span class="sxs-lookup"><span data-stu-id="a9876-165">**double**</span></span>|<span data-ttu-id="a9876-166">**O podwójnej precyzji**</span><span class="sxs-lookup"><span data-stu-id="a9876-166">**Double**</span></span>|<span data-ttu-id="a9876-167">**podwójne**</span><span class="sxs-lookup"><span data-stu-id="a9876-167">**double**</span></span>|<span data-ttu-id="a9876-168">**O podwójnej precyzji**</span><span class="sxs-lookup"><span data-stu-id="a9876-168">**Double**</span></span>|  
|<span data-ttu-id="a9876-169">**wartość logiczna**</span><span class="sxs-lookup"><span data-stu-id="a9876-169">**bool**</span></span>|<span data-ttu-id="a9876-170">**Wartość logiczna**</span><span class="sxs-lookup"><span data-stu-id="a9876-170">**Boolean**</span></span>|<span data-ttu-id="a9876-171">**wartość logiczna**</span><span class="sxs-lookup"><span data-stu-id="a9876-171">**bool**</span></span>|<span data-ttu-id="a9876-172">**Wartość logiczna**</span><span class="sxs-lookup"><span data-stu-id="a9876-172">**Boolean**</span></span>|  
|<span data-ttu-id="a9876-173">**char**</span><span class="sxs-lookup"><span data-stu-id="a9876-173">**char**</span></span>|<span data-ttu-id="a9876-174">**Char**</span><span class="sxs-lookup"><span data-stu-id="a9876-174">**Char**</span></span>|<span data-ttu-id="a9876-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="a9876-175">**wchar_t**</span></span>|<span data-ttu-id="a9876-176">**Char**</span><span class="sxs-lookup"><span data-stu-id="a9876-176">**Char**</span></span>|  
|<span data-ttu-id="a9876-177">**ciąg**</span><span class="sxs-lookup"><span data-stu-id="a9876-177">**string**</span></span>|<span data-ttu-id="a9876-178">**Ciąg**</span><span class="sxs-lookup"><span data-stu-id="a9876-178">**String**</span></span>|<span data-ttu-id="a9876-179">**Ciąg**</span><span class="sxs-lookup"><span data-stu-id="a9876-179">**String**</span></span>|<span data-ttu-id="a9876-180">**Ciąg**</span><span class="sxs-lookup"><span data-stu-id="a9876-180">**String**</span></span>|  
|<span data-ttu-id="a9876-181">**obiekt**</span><span class="sxs-lookup"><span data-stu-id="a9876-181">**object**</span></span>|<span data-ttu-id="a9876-182">**Obiekt**</span><span class="sxs-lookup"><span data-stu-id="a9876-182">**Object**</span></span>|<span data-ttu-id="a9876-183">**Obiekt**</span><span class="sxs-lookup"><span data-stu-id="a9876-183">**Object**</span></span>|<span data-ttu-id="a9876-184">**Obiekt**</span><span class="sxs-lookup"><span data-stu-id="a9876-184">**Object**</span></span>|  
  
 <span data-ttu-id="a9876-185">**CZY ✓** Użyj nazwą pospolitą, takiego jak `value` lub `item`, zamiast powtarzające się nazwa typu w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego i typ parametru nie jest ważna.</span><span class="sxs-lookup"><span data-stu-id="a9876-185">**✓ DO**  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>  
  
## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="a9876-186">Nazwy nowych wersji istniejących interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a9876-186">Naming New Versions of Existing APIs</span></span>  
 <span data-ttu-id="a9876-187">**CZY ✓** Użyj nazwy podobne do starego interfejsu API, podczas tworzenia nowych wersji istniejących interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="a9876-187">**✓ DO** use a name similar to the old API when creating new versions of an existing API.</span></span>  
  
 <span data-ttu-id="a9876-188">Pozwala to Wyróżnij relacji między interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="a9876-188">This helps to highlight the relationship between the APIs.</span></span>  
  
 <span data-ttu-id="a9876-189">**CZY ✓** preferowane jest dodanie sufiksu zamiast prefiksu wskazać nową wersję istniejącego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="a9876-189">**✓ DO** prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>  
  
 <span data-ttu-id="a9876-190">Ułatwi to Pomoc odnajdywania, przeglądając dokumentację, lub za pomocą funkcji Intellisense.</span><span class="sxs-lookup"><span data-stu-id="a9876-190">This will assist discovery when browsing documentation, or using Intellisense.</span></span> <span data-ttu-id="a9876-191">Stara wersja interfejsu API zostaną zorganizowane bliski nowych interfejsów API, ponieważ większość przeglądarek i Intellisense Pokaż identyfikatorów w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="a9876-191">The old version of the API will be organized close to the new APIs, because most browsers and Intellisense show identifiers in alphabetical order.</span></span>  
  
 <span data-ttu-id="a9876-192">**ROZWAŻ ✓** przy użyciu całkowicie nowe, ale łatwy do rozpoznania identyfikator, zamiast dodawania sufiks lub prefiks.</span><span class="sxs-lookup"><span data-stu-id="a9876-192">**✓ CONSIDER** using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>  
  
 <span data-ttu-id="a9876-193">**CZY ✓** sufiks numeryczny do wskazania użyć nową wersję istniejącego interfejsu API, szczególnie jeśli istniejącej nazwy interfejsu API jest tylko nazwę, która ma sens (tj., jeśli jest standardem branżowym) i dodawania żadnych zrozumiały sufiks (lub zmiana nazwy) nie jest aplikacji Opcja ropriate.</span><span class="sxs-lookup"><span data-stu-id="a9876-193">**✓ DO** use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>  
  
 <span data-ttu-id="a9876-194">**X nie** "Ex" (lub podobny) sufiks identyfikatora odróżniający go od wcześniejszej wersji tego samego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="a9876-194">**X DO NOT** use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>  
  
 <span data-ttu-id="a9876-195">**CZY ✓** Użyj sufiksu "64", wprowadzając wersje interfejsów API, które działają na 64-bitowa liczba całkowita (długich liczb całkowitych) zamiast 32-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="a9876-195">**✓ DO** use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="a9876-196">Należy o zastosowaniu takiego podejścia, gdy istnieje istniejących API 32-bitowy; nie robi to całkowicie nowe interfejsy API w wersji 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="a9876-196">You only need to take this approach when the existing 32-bit API exists; don’t do it for brand new APIs with only a 64-bit version.</span></span>  
  
 <span data-ttu-id="a9876-197">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="a9876-197">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a9876-198">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="a9876-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9876-199">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9876-199">See Also</span></span>  
 [<span data-ttu-id="a9876-200">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="a9876-200">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="a9876-201">Zasady nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="a9876-201">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
