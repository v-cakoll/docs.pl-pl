---
title: Projekt wyliczeń
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: efdfcda95a67941f0fde5f7a96467af7dd374396
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280143"
---
# <a name="enum-design"></a><span data-ttu-id="e679d-102">Projekt wyliczeń</span><span class="sxs-lookup"><span data-stu-id="e679d-102">Enum Design</span></span>

<span data-ttu-id="e679d-103">Wyliczenia są specjalnym rodzajem typu wartości.</span><span class="sxs-lookup"><span data-stu-id="e679d-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="e679d-104">Istnieją dwa rodzaje wyliczeń: proste wyliczenia i wyliczenia flag.</span><span class="sxs-lookup"><span data-stu-id="e679d-104">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="e679d-105">Proste wyliczenia reprezentują małe zamknięte zestawy wyborów.</span><span class="sxs-lookup"><span data-stu-id="e679d-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="e679d-106">Typowym przykładem prostego wyliczenia jest zestaw kolorów.</span><span class="sxs-lookup"><span data-stu-id="e679d-106">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="e679d-107">Typy wyliczeniowe flag są przeznaczone do obsługi operacji bitowych na wartościach wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="e679d-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="e679d-108">Typowym przykładem wyliczenia flag jest lista opcji.</span><span class="sxs-lookup"><span data-stu-id="e679d-108">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="e679d-109">✔️ Użyj wyliczenia, aby silnie typu parametry, właściwości i zwracane wartości reprezentujące zestawy wartości.</span><span class="sxs-lookup"><span data-stu-id="e679d-109">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="e679d-110">✔️ za pomocą wyliczenia zamiast stałych statycznych.</span><span class="sxs-lookup"><span data-stu-id="e679d-110">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="e679d-111">❌NIE należy używać wyliczenia dla zestawów otwartych (takich jak wersja systemu operacyjnego, nazwiska znajomych itp.).</span><span class="sxs-lookup"><span data-stu-id="e679d-111">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="e679d-112">❌Nie dostarczaj zarezerwowanych wartości wyliczenia, które są przeznaczone do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e679d-112">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="e679d-113">Zawsze możesz po prostu dodać wartości do istniejącego wyliczenia na późniejszym etapie.</span><span class="sxs-lookup"><span data-stu-id="e679d-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="e679d-114">Aby uzyskać więcej informacji na temat dodawania wartości do typów wyliczeniowych, zobacz [Dodawanie wartości do wyliczeń](#add_value) .</span><span class="sxs-lookup"><span data-stu-id="e679d-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="e679d-115">Wartości zarezerwowane powodują zanieczyszczenie zestawu rzeczywistych wartości i umożliwiają osiągnięcie błędów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e679d-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="e679d-116">❌UNIKAj publicznego ujawniania wyliczeń tylko z jedną wartością.</span><span class="sxs-lookup"><span data-stu-id="e679d-116">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="e679d-117">Typowym sposobem zapewnienia przyszłej rozszerzalności interfejsów API języka C jest dodanie zarezerwowanych parametrów do sygnatur metod.</span><span class="sxs-lookup"><span data-stu-id="e679d-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="e679d-118">Takie zastrzeżone parametry można wyrazić jako wyliczenia z pojedynczą wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="e679d-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="e679d-119">Nie należy tego robić w zarządzanych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="e679d-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="e679d-120">Przeciążanie metod pozwala dodawać parametry w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="e679d-120">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="e679d-121">❌Nie uwzględniaj wartości wskaźnikowych w wyliczeniach.</span><span class="sxs-lookup"><span data-stu-id="e679d-121">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="e679d-122">Chociaż są czasami pomocne dla deweloperów platformy, wartości wskaźnikowe są mylące dla użytkowników struktury.</span><span class="sxs-lookup"><span data-stu-id="e679d-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="e679d-123">Są one używane do śledzenia stanu wyliczenia, a nie jako jedna z wartości z zestawu reprezentowanego przez wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="e679d-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="e679d-124">✔️ zapewnić wartość zero dla prostych typów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="e679d-124">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="e679d-125">Rozważ wywołanie wartości podobnej do "none".</span><span class="sxs-lookup"><span data-stu-id="e679d-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="e679d-126">Jeśli taka wartość nie jest odpowiednia dla danego wyliczenia, najbardziej typowa wartość domyślna dla wyliczenia powinna mieć przypisaną podstawową wartość równą zero.</span><span class="sxs-lookup"><span data-stu-id="e679d-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="e679d-127">✔️ ROZWAŻYĆ użycie <xref:System.Int32> (wartość domyślna w większości języków programowania) jako typ podstawowy wyliczenia, chyba że spełniony jest którykolwiek z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="e679d-127">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="e679d-128">Wyliczenie jest wyliczeniem flag i ma więcej niż 32 flag lub oczekuje więcej w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e679d-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="e679d-129">Typ podstawowy musi być inny niż <xref:System.Int32> w celu łatwiejszego współdziałania z niezarządzanym kodem, który oczekuje różnych rodzajów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="e679d-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="e679d-130">Mniejszy typ podstawowy spowoduje znaczne oszczędności w miejscu.</span><span class="sxs-lookup"><span data-stu-id="e679d-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="e679d-131">Jeśli spodziewasz się, że Wyliczenie ma być używane głównie jako argument dla przepływu sterowania, rozmiar powoduje niewielkie różnice.</span><span class="sxs-lookup"><span data-stu-id="e679d-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="e679d-132">Oszczędność rozmiaru może być istotna, jeśli:</span><span class="sxs-lookup"><span data-stu-id="e679d-132">The size savings might be significant if:</span></span>

  - <span data-ttu-id="e679d-133">Oczekuje się, że Wyliczenie ma być używane jako pole w bardzo często skonkretyzowanyj strukturze lub klasie.</span><span class="sxs-lookup"><span data-stu-id="e679d-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="e679d-134">Oczekujesz, że użytkownicy będą tworzyć duże tablice lub kolekcje wystąpień wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="e679d-134">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="e679d-135">Oczekuje się, że wiele wystąpień wyliczenia ma być serializowana.</span><span class="sxs-lookup"><span data-stu-id="e679d-135">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="e679d-136">W przypadku użycia w pamięci należy pamiętać, że obiekty zarządzane są zawsze `DWORD` wyrównane, dlatego w celu zapewnienia różnicy należy użyć wielu wyliczeń lub innych małych struktur w celu spakowania mniejszego wyliczenia z, ponieważ całkowity rozmiar wystąpienia zawsze będzie zaokrąglany do `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="e679d-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="e679d-137">✔️ DO flagi nazwy wyliczenia z rzeczownikami w liczbie mnogiej lub rzeczownikami i prostymi wyliczeniami z pojedynczą rzeczownikami lub oznaczeniami rzeczowników.</span><span class="sxs-lookup"><span data-stu-id="e679d-137">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="e679d-138">❌NIE należy bezpośrednio przełączać <xref:System.Enum?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e679d-138">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="e679d-139"><xref:System.Enum?displayProperty=nameWithType>jest specjalnym typem używanym przez środowisko CLR do tworzenia wyliczeń zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e679d-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="e679d-140">Większość języków programowania udostępnia element programistyczny, który zapewnia dostęp do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e679d-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="e679d-141">Na przykład w języku C# `enum` słowo kluczowe jest używane do definiowania wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e679d-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="e679d-142">Projektowanie typów wyliczeniowych flag</span><span class="sxs-lookup"><span data-stu-id="e679d-142">Designing Flag Enums</span></span>

<span data-ttu-id="e679d-143">✔️ zastosować <xref:System.FlagsAttribute?displayProperty=nameWithType> do flag wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="e679d-143">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="e679d-144">Nie stosuj tego atrybutu do prostych typów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="e679d-144">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="e679d-145">✔️ Użyj uprawnień dwóch dla wartości wyliczenia flag, aby można je było swobodnie łączyć przy użyciu operacji bitowej lub.</span><span class="sxs-lookup"><span data-stu-id="e679d-145">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="e679d-146">✔️ ROZWAŻYĆ dostarczenie specjalnych wartości wyliczenia dla często używanych kombinacji flag.</span><span class="sxs-lookup"><span data-stu-id="e679d-146">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="e679d-147">Operacje bitowe są zaawansowaną koncepcją i nie powinny być wymagane w przypadku prostych zadań.</span><span class="sxs-lookup"><span data-stu-id="e679d-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="e679d-148"><xref:System.IO.FileAccess.ReadWrite>to przykład specjalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="e679d-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="e679d-149">❌UNIKAj tworzenia wyliczeń flag, w których niektóre kombinacje wartości są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e679d-149">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="e679d-150">❌UNIKAj używania wartości wyliczeniowych flag zero, chyba że wartość reprezentuje "wszystkie flagi są wyczyszczone" i jest odpowiednio określona, zgodnie z opisem w następnej wytycznej.</span><span class="sxs-lookup"><span data-stu-id="e679d-150">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="e679d-151">✔️ NALEŻY nazwać wartość zerową dla wyliczeń flag `None` .</span><span class="sxs-lookup"><span data-stu-id="e679d-151">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="e679d-152">W przypadku wyliczenia flag wartość musi zawsze oznaczać, że wszystkie flagi są wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="e679d-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="e679d-153">Dodawanie wartości do typów wyliczeniowych</span><span class="sxs-lookup"><span data-stu-id="e679d-153">Adding Value to Enums</span></span>

<span data-ttu-id="e679d-154">Bardzo typowym sposobem jest odnajdowanie, że należy dodać wartości do wyliczenia po jego już wysłaniu.</span><span class="sxs-lookup"><span data-stu-id="e679d-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="e679d-155">Występuje potencjalny problem ze zgodnością aplikacji w przypadku zwrócenia nowo dodanej wartości z istniejącego interfejsu API, ponieważ źle zapisywane aplikacje mogą nieprawidłowo obsłużyć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e679d-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="e679d-156">✔️ ROZWAŻYĆ dodanie wartości do typów wyliczeniowych, pomimo małych zagrożeń zgodności.</span><span class="sxs-lookup"><span data-stu-id="e679d-156">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="e679d-157">Jeśli masz prawdziwe dane dotyczące niezgodności aplikacji spowodowanych przez dodatki do wyliczenia, rozważ dodanie nowego interfejsu API, który zwraca nowe i stare wartości, i Zastąp stary interfejs API, który powinien nadal zwracać tylko stare wartości.</span><span class="sxs-lookup"><span data-stu-id="e679d-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="e679d-158">Dzięki temu istniejące aplikacje będą nadal zgodne.</span><span class="sxs-lookup"><span data-stu-id="e679d-158">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="e679d-159">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="e679d-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="e679d-160">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="e679d-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e679d-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e679d-161">See also</span></span>

- [<span data-ttu-id="e679d-162">Wskazówki dotyczące projektowania typów</span><span class="sxs-lookup"><span data-stu-id="e679d-162">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="e679d-163">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="e679d-163">Framework Design Guidelines</span></span>](index.md)
