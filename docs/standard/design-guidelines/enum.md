---
title: Projekt wyliczeń
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dea187b5f3911114e551d640e0bb0aa6fac1143
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891236"
---
# <a name="enum-design"></a><span data-ttu-id="ecb36-102">Projekt wyliczeń</span><span class="sxs-lookup"><span data-stu-id="ecb36-102">Enum Design</span></span>
<span data-ttu-id="ecb36-103">Typy wyliczeniowe są specjalnym rodzajem typu wartości.</span><span class="sxs-lookup"><span data-stu-id="ecb36-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="ecb36-104">Istnieją dwa rodzaje wyliczeń: prostych typów wyliczeniowych i flagi wyliczeń.</span><span class="sxs-lookup"><span data-stu-id="ecb36-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="ecb36-105">Proste typy wyliczeniowe reprezentują małych zamknięte zestawów opcji.</span><span class="sxs-lookup"><span data-stu-id="ecb36-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="ecb36-106">Typowym przykładem proste wyliczenia to zestaw kolorów.</span><span class="sxs-lookup"><span data-stu-id="ecb36-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="ecb36-107">Typy wyliczeniowe flag są przeznaczone do wsparcia Operacje bitowe wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ecb36-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="ecb36-108">Typowym przykładem wyliczenia flag jest lista opcji.</span><span class="sxs-lookup"><span data-stu-id="ecb36-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="ecb36-109">**✓ DO** silnie wpisz parametry, właściwości, za pomocą wyliczeniem i zwracać wartości, które reprezentują zestawy wartości.</span><span class="sxs-lookup"><span data-stu-id="ecb36-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="ecb36-110">**✓ DO** Preferuj przy użyciu wyliczenia zamiast stałych statycznych.</span><span class="sxs-lookup"><span data-stu-id="ecb36-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="ecb36-111">**X DO NOT** wyliczenia na użytek otwartych zestawów (takie jak wersja systemu operacyjnego, nazwy użytkownika znajomych, itp.).</span><span class="sxs-lookup"><span data-stu-id="ecb36-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="ecb36-112">**X DO NOT** Podaj zastrzeżone wyliczenia wartości, które są przeznaczone do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="ecb36-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="ecb36-113">Na późniejszym etapie można zawsze po prostu dodać wartości do istniejącego typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="ecb36-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="ecb36-114">Zobacz [dodanie wartości do wyliczenia](#add_value) Aby uzyskać więcej informacji na temat dodawania wartości do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ecb36-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="ecb36-115">Zastrzeżone wartości po prostu charakteryzują się zestaw wartości rzeczywistych i powodowało błędy użytkowników.</span><span class="sxs-lookup"><span data-stu-id="ecb36-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="ecb36-116">**X AVOID** publicznie udostępnianie wyliczenia z tylko jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="ecb36-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="ecb36-117">Powszechną praktyką zapewniających przyszłej rozszerzalności interfejsów API języka C jest dodać zastrzeżone parametry do podpisów metod.</span><span class="sxs-lookup"><span data-stu-id="ecb36-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="ecb36-118">Takie zastrzeżone parametry mogą być wyrażone jako Typy wyliczeniowe atrybutem wartość domyślną pojedynczej.</span><span class="sxs-lookup"><span data-stu-id="ecb36-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="ecb36-119">To nie należy wykonywać w zarządzanych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="ecb36-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="ecb36-120">Przeciążenie metody umożliwia dodawanie parametrów w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="ecb36-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="ecb36-121">**X DO NOT** zawierają wartości wskaźnikowych w wyliczeniach.</span><span class="sxs-lookup"><span data-stu-id="ecb36-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="ecb36-122">Chociaż czasami są przydatne dla deweloperów w ramach, wartownik wartości są mylące dla użytkowników Framework.</span><span class="sxs-lookup"><span data-stu-id="ecb36-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="ecb36-123">Są one używane do śledzenia stanu typu wyliczeniowego, a nie jest jedną z wartości z zestawu, reprezentowany przez wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="ecb36-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="ecb36-124">**✓ DO** Podaj wartość zero w prosty wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ecb36-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="ecb36-125">Należy wziąć pod uwagę podczas wywoływania wartość podobną "None".</span><span class="sxs-lookup"><span data-stu-id="ecb36-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="ecb36-126">Jeśli wartość ta nie jest właściwa dla tego konkretnego wyliczenia, najbardziej typowe domyślna wartość wyliczenia powinny przypisany podstawową wartość zero.</span><span class="sxs-lookup"><span data-stu-id="ecb36-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="ecb36-127">**✓ CONSIDER** przy użyciu <xref:System.Int32> (ustawienie domyślne w większości języków programowania) jako typu bazowego typu wyliczeniowego, chyba że jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ecb36-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
-   <span data-ttu-id="ecb36-128">Wyliczenia jest wyliczenie flag i masz więcej niż 32 flag lub chcą mieć w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="ecb36-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
-   <span data-ttu-id="ecb36-129">Typ podstawowy musi być inna niż <xref:System.Int32> dla ułatwia współdziałanie z kodem niezarządzanym Oczekiwano innego rozmiaru wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ecb36-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
-   <span data-ttu-id="ecb36-130">Mniejsze bazowego typu spowoduje znaczne oszczędności miejsca.</span><span class="sxs-lookup"><span data-stu-id="ecb36-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="ecb36-131">Jeśli oczekujesz, wyliczenia, które ma być używany przede wszystkim jako argument dla przepływu sterowania, rozmiar sprawia, że niewielkie różnice.</span><span class="sxs-lookup"><span data-stu-id="ecb36-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="ecb36-132">Oszczędności rozmiaru wynikające mogą być znaczące, jeśli:</span><span class="sxs-lookup"><span data-stu-id="ecb36-132">The size savings might be significant if:</span></span>  
  
    -   <span data-ttu-id="ecb36-133">Oczekujesz, że wyliczenie, które ma być używany jako pole w bardzo często skonkretyzowany struktury lub klasy.</span><span class="sxs-lookup"><span data-stu-id="ecb36-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    -   <span data-ttu-id="ecb36-134">Oczekujesz, że użytkownicy, aby utworzyć duże tablice i kolekcje wystąpieniami enum.</span><span class="sxs-lookup"><span data-stu-id="ecb36-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    -   <span data-ttu-id="ecb36-135">Spodziewasz się dużej liczby wystąpień typu wyliczeniowego do zserializowania.</span><span class="sxs-lookup"><span data-stu-id="ecb36-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="ecb36-136">Do użycia w pamięci należy pamiętać, że zarządzane obiekty są zawsze `DWORD`-wyrównane, więc należy skutecznie wiele typów wyliczeniowych lub innych struktur małe w wystąpieniu umieszczenie mniejszych wyliczenia z celu reagować, ponieważ rozmiar wystąpienia całkowita jest zawsze Zamierzasz zaokrąglone do `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="ecb36-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="ecb36-137">**✓ DO** nazwa wyliczenia flagi rzeczowniki w liczbie mnogiej lub fraz rzeczownik i proste wyliczenia za pomocą pojedynczej rzeczowniki ani fraz rzeczownik.</span><span class="sxs-lookup"><span data-stu-id="ecb36-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="ecb36-138">**X DO NOT** rozszerzyć <xref:System.Enum?displayProperty=nameWithType> bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ecb36-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="ecb36-139"><xref:System.Enum?displayProperty=nameWithType> jest specjalnym typem jest używana przez środowisko CLR do tworzenia wyliczenia zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ecb36-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="ecb36-140">Większość języków programowania, podaj element programowania, który umożliwia dostęp do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ecb36-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="ecb36-141">Na przykład w języku C# `enum` — słowo kluczowe jest używane do definiowania wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ecb36-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="ecb36-142">Projektowanie flagi wyliczeń</span><span class="sxs-lookup"><span data-stu-id="ecb36-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="ecb36-143">**✓ DO** zastosować <xref:System.FlagsAttribute?displayProperty=nameWithType> do wyliczenia flagi.</span><span class="sxs-lookup"><span data-stu-id="ecb36-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="ecb36-144">Nie dotyczą tego atrybutu prostych typów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="ecb36-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="ecb36-145">**✓ DO** używać potęgami liczby dwa dla wartości wyliczenia flag, dlatego można je dowolnie łączyć przy użyciu operacji bitowej OR.</span><span class="sxs-lookup"><span data-stu-id="ecb36-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="ecb36-146">**✓ CONSIDER** dostarczanie wartości wyliczenia specjalne powszechnie używane kombinacji flag.</span><span class="sxs-lookup"><span data-stu-id="ecb36-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="ecb36-147">Operacje bitowe są zaawansowane pojęcia i nie powinno być wymagane dla prostych zadań.</span><span class="sxs-lookup"><span data-stu-id="ecb36-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="ecb36-148"><xref:System.IO.FileAccess.ReadWrite> znajduje się przykład specjalna wartość.</span><span class="sxs-lookup"><span data-stu-id="ecb36-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="ecb36-149">**X AVOID** tworzenia wyliczenia flag gdzie niektórych kombinacji wartości są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="ecb36-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="ecb36-150">**X AVOID** przy użyciu flagi wyliczenia wartości zero, chyba że wartość reprezentuje "wszystkie flagi są czyszczone" i nazwie odpowiednio, zgodnie z wytycznymi dalej.</span><span class="sxs-lookup"><span data-stu-id="ecb36-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="ecb36-151">**✓ DO** nazwę zerowej wartości wyliczenia flagi `None`.</span><span class="sxs-lookup"><span data-stu-id="ecb36-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="ecb36-152">Dla wyliczenia flag wartość musi zawsze oznacza "wszystkie flagi są czyszczone."</span><span class="sxs-lookup"><span data-stu-id="ecb36-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="ecb36-153">Dodanie wartości do wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ecb36-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="ecb36-154">Jest bardzo popularne jest potrzebna dodać wartości do wyliczenia, po już został wysłany.</span><span class="sxs-lookup"><span data-stu-id="ecb36-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="ecb36-155">Istnieje potencjalny problem ze zgodnością aplikacji gdy nowo dodanych wartość jest zwracana z istniejących interfejsów API, ponieważ źle napisane aplikacje nie może obsługiwać nową wartość poprawnie.</span><span class="sxs-lookup"><span data-stu-id="ecb36-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="ecb36-156">**✓ CONSIDER** dodawania wartości do wyliczenia, pomimo ryzyka małych zgodności.</span><span class="sxs-lookup"><span data-stu-id="ecb36-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="ecb36-157">Jeśli masz rzeczywiste dane dotyczące problemów ze zgodnością aplikacji spowodowanych dodatki do wyliczenia, Rozważ dodanie nowego interfejsu API, które zwraca wartości nowym i starym i wycofana starego interfejsu API, który powinno być kontynuowane, zwracając starej wartości.</span><span class="sxs-lookup"><span data-stu-id="ecb36-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="ecb36-158">Pozwoli to zagwarantować, że istniejące aplikacje są zgodne.</span><span class="sxs-lookup"><span data-stu-id="ecb36-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="ecb36-159">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="ecb36-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ecb36-160">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="ecb36-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb36-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecb36-161">See also</span></span>

- [<span data-ttu-id="ecb36-162">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ecb36-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="ecb36-163">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ecb36-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
