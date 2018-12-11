---
title: Powodująca niezgodność zmiany i bibliotek platformy .NET
description: Zalecenia dotyczące najlepszych rozwiązań do nawigowania między przełomowych zmian podczas tworzenia bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: e0e62cda1b7475cd5d1f8bcd3558dc2fe7f6e07c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148516"
---
# <a name="breaking-changes"></a><span data-ttu-id="8d848-103">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="8d848-103">Breaking changes</span></span>

<span data-ttu-id="8d848-104">Jest ważne dla biblioteki .NET znaleźć równowagę między stabilności istniejących użytkowników i innowacji w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="8d848-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="8d848-105">Dowiedz się autorzy biblioteki kierunku refaktoryzacji i przemyślenie kod, dopóki nie jest doskonała, ale istotne istniejących użytkowników ma negatywnego wpływu, szczególnie w przypadku bibliotek niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8d848-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="8d848-106">Typy projektów i fundamentalne zmiany</span><span class="sxs-lookup"><span data-stu-id="8d848-106">Project types and breaking changes</span></span>

<span data-ttu-id="8d848-107">Jak biblioteka jest używana przez społeczność .NET zmienia efekt istotne zmiany w deweloperzy będący użytkownikami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="8d848-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

* <span data-ttu-id="8d848-108">**Niski i bibliotek średnio** podobnie jak serializator, HTML analizatora, mapowania obiektowo relacyjny bazy danych lub struktury sieci web są najczęściej wykorzystywanych przez istotne zmiany.</span><span class="sxs-lookup"><span data-stu-id="8d848-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="8d848-109">Bloków konstrukcyjnych pakiety są używane przez użytkowników końcowych deweloperom tworzenie aplikacji i innych bibliotek, jako zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="8d848-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="8d848-110">Na przykład tworzysz aplikację i za pomocą klienta typu open source do wywołania usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="8d848-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="8d848-111">Aktualizację zależności, którego klient używa na podziału nie jest coś, co można poprawić.</span><span class="sxs-lookup"><span data-stu-id="8d848-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="8d848-112">To klient typu open source, który musi zostać zmieniona, i masz żadnej kontroli nad nim.</span><span class="sxs-lookup"><span data-stu-id="8d848-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="8d848-113">Trzeba znaleźć zgodne wersje bibliotek lub przesłać poprawki do biblioteki klienta i poczekaj na nową wersję.</span><span class="sxs-lookup"><span data-stu-id="8d848-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="8d848-114">Najgorszego przypadku sytuacja jest, jeśli chcesz korzystać z dwóch bibliotek, które są zależne od wzajemnie wykluczające się niezgodne wersje trzeci biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8d848-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

* <span data-ttu-id="8d848-115">**Biblioteki wysokiego poziomu** takich jak pakiet interfejsu użytkownika kontrolki są mniej podatne na istotne zmiany.</span><span class="sxs-lookup"><span data-stu-id="8d848-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="8d848-116">Biblioteki wysokiego poziomu odwołuje się bezpośrednio w aplikacji użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="8d848-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="8d848-117">Przełomowych zmianach, deweloper może zdecydować o aktualizacji do najnowszej wersji lub mogą modyfikować ich stosowania do pracy z istotną zmianę.</span><span class="sxs-lookup"><span data-stu-id="8d848-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="8d848-118">**CZY ✔️** reakcji o tym, jak używać biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8d848-118">**✔️ DO** think about how your library will be used.</span></span> <span data-ttu-id="8d848-119">Jaki będzie wpływ będą miały przełomowe zmiany w aplikacji i bibliotek, które go używają?</span><span class="sxs-lookup"><span data-stu-id="8d848-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="8d848-120">**CZY ✔️** zminimalizować przełomowych zmianach, wdrażając bibliotekę .NET niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8d848-120">**✔️ DO** minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="8d848-121">**ROZWAŻ ✔️** publikowanie większych Napisz ponownie jako nowy pakiet NuGet biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8d848-121">**✔️ CONSIDER** publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="8d848-122">Typy zmian powodujących niezgodność</span><span class="sxs-lookup"><span data-stu-id="8d848-122">Types of breaking changes</span></span>

<span data-ttu-id="8d848-123">Powodująca niezgodność zmiany można podzielić na różne kategorie i nie są równie istotna.</span><span class="sxs-lookup"><span data-stu-id="8d848-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="8d848-124">Zmiana powodująca Niezgodność źródła</span><span class="sxs-lookup"><span data-stu-id="8d848-124">Source breaking change</span></span>

<span data-ttu-id="8d848-125">Zmiana powodująca niezgodność źródło nie ma wpływu na działanie programu, ale spowoduje, że błędy kompilacji podczas następnego aplikacji jest ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="8d848-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="8d848-126">Na przykład też nowym przeciążeniem można utworzyć niejednoznaczność w wywołaniach metod, które wcześniej znajdowały się jednoznaczna lub zmieniono nazwę parametru spowoduje przerwanie obiektów wywołujących, które używają nazwanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="8d848-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="8d848-127">Źródło zmiana powodująca niezgodność jest szkodliwe tylko w przypadku, gdy deweloperzy ponownie skompilować swoich aplikacji, dlatego jest najmniej szkodliwe istotną zmianę.</span><span class="sxs-lookup"><span data-stu-id="8d848-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="8d848-128">Deweloperzy łatwo rozwiązać swój własny kod w uszkodzona źródła.</span><span class="sxs-lookup"><span data-stu-id="8d848-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="8d848-129">Zmiana powodująca niezgodność zachowanie</span><span class="sxs-lookup"><span data-stu-id="8d848-129">Behavior breaking change</span></span>

<span data-ttu-id="8d848-130">Zmiany zachowania są najczęściej spotykanym typem istotnej zmiany: praktycznie dowolne zmiany w zachowaniu może spowodować przerwanie osoby.</span><span class="sxs-lookup"><span data-stu-id="8d848-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="8d848-131">Zmiany do biblioteki, takie jak podpisy metod wyjątki zgłaszane lub wejścia lub wyjścia formatów danych mogą wszystkie niekorzystnie wpłynąć na klientów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8d848-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="8d848-132">Nawet poprawki mogą zakwalifikować się do istotnej zmiany, jeśli użytkownicy opiera się na zachowanie wcześniej przerwane.</span><span class="sxs-lookup"><span data-stu-id="8d848-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="8d848-133">Dodawanie funkcji i poprawianie nieprawidłowych zachowań jest to przydatne, ale bez obsługi może być bardzo trudne dla istniejących użytkowników do uaktualnienia.</span><span class="sxs-lookup"><span data-stu-id="8d848-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="8d848-134">Jedno z podejść do pomagając deweloperom postępowania z zachowaniem przełomowych zmian jest je ukryć za ustawienia.</span><span class="sxs-lookup"><span data-stu-id="8d848-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="8d848-135">Ustawienia umożliwiają deweloperom aktualizację do najnowszej wersji biblioteki, w tym samym czasie, wybierając zgoda lub zrezygnować z istotne zmiany.</span><span class="sxs-lookup"><span data-stu-id="8d848-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="8d848-136">Ta strategia umożliwia deweloperom bądź na bieżąco, pozwalając na ich kod konsumencki dostosowania wraz z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="8d848-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="8d848-137">Na przykład, ASP.NET Core MVC korzysta z koncepcji [zgodność wersji](/aspnet/core/mvc/compatibility-version) funkcje włączone i wyłączone, który modyfikuje `MvcOptions`.</span><span class="sxs-lookup"><span data-stu-id="8d848-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="8d848-138">**ROZWAŻ ✔️** opuszczania nowe funkcje domyślnie, jeśli one wpływu na istniejących użytkowników i umożliwiają deweloperom Zezwól na korzystanie z funkcji z ustawieniem.</span><span class="sxs-lookup"><span data-stu-id="8d848-138">**✔️ CONSIDER** leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="8d848-139">Zmiana powodująca niezgodność binarne</span><span class="sxs-lookup"><span data-stu-id="8d848-139">Binary breaking change</span></span>

<span data-ttu-id="8d848-140">Zmiana powodująca niezgodność plik binarny się dzieje, gdy zmienisz publiczny interfejs API biblioteki, dzięki czemu zestawy skompilowane starsze wersje biblioteki nie jest już możliwe do wywołania interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="8d848-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="8d848-141">Na przykład zmiana sygnatury metody przez dodanie nowego parametru spowoduje, że zestawy skompilowane starszą wersję biblioteki throw <xref:System.MissingMethodException>.</span><span class="sxs-lookup"><span data-stu-id="8d848-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="8d848-142">Zmiana powodująca niezgodność plik binarny może to również uszkodzenie **cały zespół**.</span><span class="sxs-lookup"><span data-stu-id="8d848-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="8d848-143">Zmiana nazwy zestawu za pomocą `AssemblyName` ulegnie zmianie tożsamości zestawu, podobnie jak dodawanie, usuwanie i zmienianie silnego klucza nazw zestawu.</span><span class="sxs-lookup"><span data-stu-id="8d848-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="8d848-144">Zmiana tożsamości zestawu spowoduje przerwanie wszystkich skompilowany kod, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="8d848-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="8d848-145">**❌ NIE** Zmień nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="8d848-145">**❌ DO NOT** change an assembly name.</span></span>

<span data-ttu-id="8d848-146">**❌ NIE** dodać, usunąć lub zmienić silnego klucza nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="8d848-146">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="8d848-147">**ROZWAŻ ✔️** przy użyciu abstrakcyjnych klas bazowych, zamiast interfejsów.</span><span class="sxs-lookup"><span data-stu-id="8d848-147">**✔️ CONSIDER** using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="8d848-148">Dodawanie niczego do interfejsu spowoduje, że istniejące typy implementujące nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="8d848-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="8d848-149">Abstrakcyjna klasa bazowa umożliwia dodawanie Domyślna implementacja wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="8d848-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="8d848-150">**ROZWAŻ ✔️** umieszczenie <xref:System.ObsoleteAttribute> na typy i elementy członkowskie, które zamierzasz usunąć.</span><span class="sxs-lookup"><span data-stu-id="8d848-150">**✔️ CONSIDER** placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="8d848-151">Ten atrybut powinien mieć instrukcje dotyczące aktualizowania kodu nie są już używane przestarzałych API.</span><span class="sxs-lookup"><span data-stu-id="8d848-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="8d848-152">Kod, który wywołuje typy i metody o <xref:System.ObsoleteAttribute> zostanie wygenerowane ostrzeżenie dotyczące kompilacji za pomocą wiadomości podano do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8d848-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="8d848-153">Osoby zapewniają ostrzeżeń, które umożliwia migracji po usunięciu przestarzałe API większość nie są już przestarzałe czasu powierzchni interfejsu API przy użyciu go.</span><span class="sxs-lookup"><span data-stu-id="8d848-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

<span data-ttu-id="8d848-154">**✔️ ROZWAŻ** utrzymywanie typy i metody o <xref:System.ObsoleteAttribute> przez czas nieokreślony w bibliotekach niski i wyższych.</span><span class="sxs-lookup"><span data-stu-id="8d848-154">**✔️ CONSIDER** keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="8d848-155">Usuwanie interfejsów API jest zmiana powodująca niezgodność dane binarne.</span><span class="sxs-lookup"><span data-stu-id="8d848-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="8d848-156">Biorąc pod uwagę zachowanie przestarzałe typy i metody, jeśli ich obsługi jest niskie koszty i nie powoduje dodania dług techniczny do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8d848-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="8d848-157">Nie usuwanie typów i metod może pomóc uniknąć najgorszego przypadku scenariuszy wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="8d848-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d848-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d848-158">See also</span></span>

* [<span data-ttu-id="8d848-159">Wersja i zaktualizuj uwagi dla deweloperów języka C#</span><span class="sxs-lookup"><span data-stu-id="8d848-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
* [<span data-ttu-id="8d848-160">Ostateczny przewodnik dotyczący interfejsu API — przełomowe zmiany w .NET</span><span class="sxs-lookup"><span data-stu-id="8d848-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
* [<span data-ttu-id="8d848-161">CoreFX istotnej zmiany zasad</span><span class="sxs-lookup"><span data-stu-id="8d848-161">CoreFX Breaking Change Rules</span></span>](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="8d848-162">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="8d848-162">Previous</span></span>](versioning.md)