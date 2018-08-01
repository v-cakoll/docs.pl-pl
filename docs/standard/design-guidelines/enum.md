---
title: Projekt wyliczenia
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
ms.openlocfilehash: 544f617ca3a352814504125d7a61d70db5a81566
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579252"
---
# <a name="enum-design"></a><span data-ttu-id="c1e15-102">Projekt wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c1e15-102">Enum Design</span></span>
<span data-ttu-id="c1e15-103">Wyliczenia to specjalny rodzaj typu wartości.</span><span class="sxs-lookup"><span data-stu-id="c1e15-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="c1e15-104">Istnieją dwa rodzaje wyliczenia: proste Typy wyliczeniowe i flagi wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1e15-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="c1e15-105">Proste typy wyliczeniowe reprezentują małych zestawów zamkniętego opcji.</span><span class="sxs-lookup"><span data-stu-id="c1e15-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="c1e15-106">Typowym przykładem prostego wyliczenia to zestaw kolorów.</span><span class="sxs-lookup"><span data-stu-id="c1e15-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="c1e15-107">Typy wyliczeniowe flag zostały zaprojektowane do obsługi Operacje bitowe wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1e15-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="c1e15-108">Typowym przykładem wyliczenia flag znajduje się lista opcji.</span><span class="sxs-lookup"><span data-stu-id="c1e15-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="c1e15-109">**✓ DO** silnie wpisz parametry, właściwości, za pomocą wyliczeniem i zwracać wartości, które reprezentują zestawy wartości.</span><span class="sxs-lookup"><span data-stu-id="c1e15-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="c1e15-110">**✓ DO** Preferuj przy użyciu wyliczenia zamiast stałych statycznych.</span><span class="sxs-lookup"><span data-stu-id="c1e15-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="c1e15-111">**X DO NOT** wyliczenia na użytek otwartych zestawów (takie jak wersja systemu operacyjnego, nazwy użytkownika znajomych, itp.).</span><span class="sxs-lookup"><span data-stu-id="c1e15-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="c1e15-112">**X DO NOT** Podaj zastrzeżone wyliczenia wartości, które są przeznaczone do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="c1e15-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="c1e15-113">Zawsze po prostu można dodać wartości do istniejących wyliczenia na późniejszym etapie.</span><span class="sxs-lookup"><span data-stu-id="c1e15-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="c1e15-114">Zobacz [dodawania wartości do wyliczenia](#add_value) uzyskać więcej informacji dotyczących dodawania wartości do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1e15-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="c1e15-115">Zastrzeżone wartości po prostu charakteryzują się zbiór wartości rzeczywistych i powodowało błędy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c1e15-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="c1e15-116">**X AVOID** publicznie udostępnianie wyliczenia z tylko jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="c1e15-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="c1e15-117">Jest typowym rozwiązaniem dla zapewnienia przyszłych rozszerzalności interfejsów API C aby dodać parametry zarezerwowane do sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="c1e15-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="c1e15-118">Parametry takie zastrzeżone może zostać wyrażona jako wyliczenia za pomocą pojedynczego domyślną wartość.</span><span class="sxs-lookup"><span data-stu-id="c1e15-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="c1e15-119">Nie należy to zrobić w zarządzanych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="c1e15-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="c1e15-120">Przeciążenie metody umożliwia dodawanie parametrów w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="c1e15-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="c1e15-121">**X DO NOT** zawierają wartości wskaźnikowych w wyliczeniach.</span><span class="sxs-lookup"><span data-stu-id="c1e15-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="c1e15-122">Chociaż są czasami pomaga deweloperom framework, wartości wartownika są trudne dla użytkowników platformy.</span><span class="sxs-lookup"><span data-stu-id="c1e15-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="c1e15-123">Są one używane do śledzenia stanu wyliczenia, a nie jest jedną z wartości z zestawu reprezentowany przez wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1e15-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="c1e15-124">**✓ DO** Podaj wartość zero w prosty wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1e15-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="c1e15-125">Należy wziąć pod uwagę podczas wywoływania wartości podobnie "None."</span><span class="sxs-lookup"><span data-stu-id="c1e15-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="c1e15-126">Jeśli wartość ta nie jest odpowiedni dla tego konkretnego wyliczenia, najczęściej domyślna wartość wyliczenia należy przypisać odpowiednia wartość zero.</span><span class="sxs-lookup"><span data-stu-id="c1e15-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="c1e15-127">**✓ CONSIDER** przy użyciu <xref:System.Int32> (ustawienie domyślne w większości języków programowania) jako typu bazowego typu wyliczeniowego, chyba że jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c1e15-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
-   <span data-ttu-id="c1e15-128">Wyliczenia jest wyliczenia flag, i mieć więcej niż 32 flagi lub oczekiwana jest więcej w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="c1e15-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
-   <span data-ttu-id="c1e15-129">Typ podstawowy musi być inna niż <xref:System.Int32> ułatwia współdziałanie z kodem niezarządzanym oczekiwano inny rozmiar wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1e15-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
-   <span data-ttu-id="c1e15-130">Mniejsze podstawowy typ spowoduje znaczne oszczędności miejsca.</span><span class="sxs-lookup"><span data-stu-id="c1e15-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="c1e15-131">Jeśli planujesz wyliczenia mają być używane głównie jako argument dla przepływu sterowania, rozmiar sprawia, że mała różnica.</span><span class="sxs-lookup"><span data-stu-id="c1e15-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="c1e15-132">Wielkość oszczędności mogą być istotne jeśli:</span><span class="sxs-lookup"><span data-stu-id="c1e15-132">The size savings might be significant if:</span></span>  
  
    -   <span data-ttu-id="c1e15-133">Spodziewasz się wyliczenia mają być używane jako pola na bardzo często skonkretyzowanym struktury lub klasy.</span><span class="sxs-lookup"><span data-stu-id="c1e15-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    -   <span data-ttu-id="c1e15-134">Spodziewasz się użytkownikom na tworzenie dużych tablice lub kolekcji wystąpień wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1e15-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    -   <span data-ttu-id="c1e15-135">Spodziewasz się dużej liczby wystąpień wyliczenia do serializacji.</span><span class="sxs-lookup"><span data-stu-id="c1e15-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="c1e15-136">Do użytku w pamięci, należy pamiętać, zawsze są zarządzane obiekty `DWORD`-wyrównane, więc należy skutecznie wiele typów wyliczeniowych lub inne małych struktury w wystąpieniu można spakować mniejszych wyliczenie o Aby pracować wydajniej, ponieważ rozmiar całkowitą wystąpienia jest zawsze będzie zaokrągloną w górę do `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="c1e15-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="c1e15-137">**✓ DO** nazwa wyliczenia flagi rzeczowniki w liczbie mnogiej lub fraz rzeczownik i proste wyliczenia za pomocą pojedynczej rzeczowniki ani fraz rzeczownik.</span><span class="sxs-lookup"><span data-stu-id="c1e15-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="c1e15-138">**X DO NOT** rozszerzyć <xref:System.Enum?displayProperty=nameWithType> bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="c1e15-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="c1e15-139"><xref:System.Enum?displayProperty=nameWithType> specjalny typ służy przez środowisko CLR do tworzenia wyliczenia zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c1e15-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="c1e15-140">Większość języków programowania udostępnia elementu programistycznego, która umożliwia dostęp do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c1e15-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="c1e15-141">Na przykład w języku C# `enum` — słowo kluczowe jest używane do definiowania wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1e15-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="c1e15-142">Projektowanie wyliczenia flagi</span><span class="sxs-lookup"><span data-stu-id="c1e15-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="c1e15-143">**✓ DO** zastosować <xref:System.FlagsAttribute?displayProperty=nameWithType> do wyliczenia flagi.</span><span class="sxs-lookup"><span data-stu-id="c1e15-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="c1e15-144">Nie dotyczą tego atrybutu prostego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1e15-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="c1e15-145">**✓ DO** używać potęgami liczby dwa dla wartości wyliczenia flag, dlatego można je dowolnie łączyć przy użyciu operacji bitowej OR.</span><span class="sxs-lookup"><span data-stu-id="c1e15-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="c1e15-146">**✓ CONSIDER** dostarczanie wartości wyliczenia specjalne powszechnie używane kombinacji flag.</span><span class="sxs-lookup"><span data-stu-id="c1e15-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="c1e15-147">Operacje bitowe są zaawansowane koncepcji i nie może być wymagane dla prostych zadań.</span><span class="sxs-lookup"><span data-stu-id="c1e15-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="c1e15-148"><xref:System.IO.FileAccess.ReadWrite> jest to przykład specjalna wartość.</span><span class="sxs-lookup"><span data-stu-id="c1e15-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="c1e15-149">**X AVOID** tworzenia wyliczenia flag gdzie niektórych kombinacji wartości są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="c1e15-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="c1e15-150">**X AVOID** przy użyciu flagi wyliczenia wartości zero, chyba że wartość reprezentuje "wszystkie flagi są czyszczone" i nazwie odpowiednio, zgodnie z wytycznymi dalej.</span><span class="sxs-lookup"><span data-stu-id="c1e15-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="c1e15-151">**✓ DO** nazwę zerowej wartości wyliczenia flagi `None`.</span><span class="sxs-lookup"><span data-stu-id="c1e15-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="c1e15-152">Dla wyliczenia flag wartość musi zawsze oznacza "wszystkie flagi są czyszczone."</span><span class="sxs-lookup"><span data-stu-id="c1e15-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="c1e15-153">Dodając wartość wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c1e15-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="c1e15-154">Często zdarza się, aby dowiedzieć się, że trzeba dodać do wyliczenia wartości, po już zostały dostarczone.</span><span class="sxs-lookup"><span data-stu-id="c1e15-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="c1e15-155">Brak potencjalny problem ze zgodnością aplikacji, gdy zostanie zwrócona wartość nowo dodanego przez istniejący interfejs API, ponieważ niepoprawnie napisane aplikacji nie może obsługiwać nową wartość poprawnie.</span><span class="sxs-lookup"><span data-stu-id="c1e15-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="c1e15-156">**✓ CONSIDER** dodawania wartości do wyliczenia, pomimo ryzyka małych zgodności.</span><span class="sxs-lookup"><span data-stu-id="c1e15-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="c1e15-157">Jeśli masz prawdziwe dane dotyczące problemów ze zgodnością aplikacji spowodowane przez dodatki do wyliczenia, należy dodać nowy interfejs API, który zwraca wartości nowym i starym i zastąpić starego interfejsu API, który powinno być kontynuowane zwracanie starych wartości.</span><span class="sxs-lookup"><span data-stu-id="c1e15-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="c1e15-158">Daje to pewność, że istniejące aplikacje są zgodne.</span><span class="sxs-lookup"><span data-stu-id="c1e15-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="c1e15-159">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="c1e15-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c1e15-160">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="c1e15-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e15-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1e15-161">See Also</span></span>  
 [<span data-ttu-id="c1e15-162">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="c1e15-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="c1e15-163">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="c1e15-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
