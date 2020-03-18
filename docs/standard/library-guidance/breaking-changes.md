---
title: Przełomowe zmiany i biblioteki .NET
description: Najlepsze zalecenia dotyczące nawigowania po zmianach podczas tworzenia bibliotek .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400422"
---
# <a name="breaking-changes"></a><span data-ttu-id="5e746-103">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="5e746-103">Breaking changes</span></span>

<span data-ttu-id="5e746-104">Ważne jest, aby biblioteka .NET znalazła równowagę między stabilnością dla istniejących użytkowników a innowacjami na przyszłość.</span><span class="sxs-lookup"><span data-stu-id="5e746-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="5e746-105">Autorzy biblioteki skłaniają się ku refaktoryzacji i ponownemu myśleniu kodu, dopóki nie będzie on doskonały, ale złamanie istniejących użytkowników ma negatywny wpływ, szczególnie w przypadku bibliotek niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="5e746-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="5e746-106">Typy projektów i zmiany dotyczące najpoławów</span><span class="sxs-lookup"><span data-stu-id="5e746-106">Project types and breaking changes</span></span>

<span data-ttu-id="5e746-107">Sposób, w jaki biblioteka jest używana przez społeczność .NET zmienia wpływ wprowadzania zmian na deweloperów użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="5e746-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

- <span data-ttu-id="5e746-108">**Biblioteki niskiego i średniego poziomu, takie** jak serializator, analizator HTML, obiekt bazy danych relacyjny maper lub struktura sieci web, są najbardziej dotknięte przez zmiany łamiące.</span><span class="sxs-lookup"><span data-stu-id="5e746-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="5e746-109">Pakiety bloków konstrukcyjnych są używane przez deweloperów użytkowników końcowych do tworzenia aplikacji i przez inne biblioteki jako zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="5e746-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="5e746-110">Na przykład budujesz aplikację i używasz klienta open source do wywołania usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="5e746-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="5e746-111">Aktualizacja podziału zależności, której używa klient, nie jest czymś, co można naprawić.</span><span class="sxs-lookup"><span data-stu-id="5e746-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="5e746-112">Jest to klient open-source, który musi zostać zmieniony i nie masz nad nim kontroli.</span><span class="sxs-lookup"><span data-stu-id="5e746-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="5e746-113">Musisz znaleźć zgodne wersje bibliotek lub przesłać poprawkę do biblioteki klienta i poczekać na nową wersję.</span><span class="sxs-lookup"><span data-stu-id="5e746-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="5e746-114">Najgorszą sytuacją jest, jeśli chcesz użyć dwóch bibliotek, które zależą od wzajemnie niezgodnych wersji trzeciej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5e746-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

- <span data-ttu-id="5e746-115">**Biblioteki wysokiego poziomu,** takie jak zestaw formantów interfejsu użytkownika, są mniej wrażliwe na przełomowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="5e746-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="5e746-116">Biblioteki wysokiego poziomu są bezpośrednio odwołuje się w aplikacji użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="5e746-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="5e746-117">Jeśli wystąpią zmiany dotyczące łamania, deweloper może zaktualizować do najnowszej wersji lub zmodyfikować swoją aplikację do pracy ze zmianą podziału.</span><span class="sxs-lookup"><span data-stu-id="5e746-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="5e746-118">✔️ zastanów się, w jaki sposób będzie używana twoja biblioteka.</span><span class="sxs-lookup"><span data-stu-id="5e746-118">✔️ DO think about how your library will be used.</span></span> <span data-ttu-id="5e746-119">Jaki wpływ będą miały zmiany krytyczne na aplikacje i biblioteki, które go używają?</span><span class="sxs-lookup"><span data-stu-id="5e746-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="5e746-120">✔️ zminimalizować zmiany podczas tworzenia biblioteki .NET niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="5e746-120">✔️ DO minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="5e746-121">✔️ ROZWAŻ opublikowanie głównych przepisać biblioteki jako nowy pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="5e746-121">✔️ CONSIDER publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="5e746-122">Rodzaje przełomowych zmian</span><span class="sxs-lookup"><span data-stu-id="5e746-122">Types of breaking changes</span></span>

<span data-ttu-id="5e746-123">Zmiany przełamywania dzielą się na różne kategorie i nie są równie ważne.</span><span class="sxs-lookup"><span data-stu-id="5e746-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="5e746-124">Zmiana podziału źródła</span><span class="sxs-lookup"><span data-stu-id="5e746-124">Source breaking change</span></span>

<span data-ttu-id="5e746-125">Zmiana podziału źródła nie wpływa na wykonanie programu, ale spowoduje błędy kompilacji przy następnym ponownym skompilowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e746-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="5e746-126">Na przykład nowe przeciążenie można utworzyć niejednoznaczności w wywołaniach metody, które były wcześniej jednoznaczne lub zmieniony parametr spowoduje przerwanie wywołujących, które używają nazwanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="5e746-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="5e746-127">Ponieważ zmiana podziału źródła jest szkodliwa tylko wtedy, gdy deweloperzy ponownie skompilować swoje aplikacje, jest to najmniej uciążliwa zmiana podziału.</span><span class="sxs-lookup"><span data-stu-id="5e746-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="5e746-128">Deweloperzy mogą łatwo naprawić swój własny uszkodzony kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="5e746-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="5e746-129">Zmiana łamania zachowań</span><span class="sxs-lookup"><span data-stu-id="5e746-129">Behavior breaking change</span></span>

<span data-ttu-id="5e746-130">Zmiany zachowania są najczęstszym typem zmiany podziału: prawie każda zmiana w zachowaniu może kogoś złamać.</span><span class="sxs-lookup"><span data-stu-id="5e746-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="5e746-131">Zmiany w bibliotece, takie jak podpisy metod, wyjątki generowane lub formaty danych wejściowych lub wyjściowych, mogą mieć negatywny wpływ na konsumentów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5e746-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="5e746-132">Nawet poprawka błędu może kwalifikować się jako przełomowa zmiana, jeśli użytkownicy polegali na wcześniej złamanym zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="5e746-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="5e746-133">Dodawanie funkcji i poprawa złych zachowań jest dobrą rzeczą, ale bez opieki może to bardzo utrudnić istniejącym użytkownikom uaktualnienie.</span><span class="sxs-lookup"><span data-stu-id="5e746-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="5e746-134">Jednym z podejść do pomagania deweloperom radzić sobie ze zmianami łamania zachowań jest ukrycie ich za ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="5e746-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="5e746-135">Ustawienia umożliwiają deweloperom aktualizację do najnowszej wersji biblioteki, jednocześnie decydując się na opcję wyrażenia zgody lub rezygnację z łamania zmian.</span><span class="sxs-lookup"><span data-stu-id="5e746-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="5e746-136">Ta strategia pozwala deweloperom być na bieżąco, pozwalając im czasowy dostosowywać kod.</span><span class="sxs-lookup"><span data-stu-id="5e746-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="5e746-137">Na przykład ASP.NET Core MVC ma pojęcie [wersji zgodności,](/aspnet/core/mvc/compatibility-version) która modyfikuje `MvcOptions`funkcje włączone i wyłączone na .</span><span class="sxs-lookup"><span data-stu-id="5e746-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="5e746-138">✔️ ROZWAŻ pozostawienie nowych funkcji domyślnie wyłączonych, jeśli mają one wpływ na istniejących użytkowników, i pozwól deweloperom wyrazić zgodę na tę funkcję z ustawieniem.</span><span class="sxs-lookup"><span data-stu-id="5e746-138">✔️ CONSIDER leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="5e746-139">Zmiana podziału binarnego</span><span class="sxs-lookup"><span data-stu-id="5e746-139">Binary breaking change</span></span>

<span data-ttu-id="5e746-140">Binarna zmiana podziału występuje po zmianie publicznego interfejsu API biblioteki, więc zestawy skompilowane ze starszymi wersjami biblioteki nie są już w stanie wywołać interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="5e746-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="5e746-141">Na przykład zmiana podpisu metody przez dodanie nowego parametru spowoduje, że zestawy skompilowane ze starszą wersją biblioteki będą wyrzucać . <xref:System.MissingMethodException></span><span class="sxs-lookup"><span data-stu-id="5e746-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="5e746-142">Zmiana podziału binarnego może również przerwać **cały zestaw**.</span><span class="sxs-lookup"><span data-stu-id="5e746-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="5e746-143">Zmiana nazwy zestawu `AssemblyName` z zmieni tożsamość zestawu, jak będzie dodawanie, usuwanie lub zmienianie zestawu silny klucz nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="5e746-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="5e746-144">Zmiana tożsamości zestawu spowoduje przerwanie całego skompilowanego kodu, który go używa.</span><span class="sxs-lookup"><span data-stu-id="5e746-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="5e746-145">❌NIE zmieniaj nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="5e746-145">❌ DO NOT change an assembly name.</span></span>

<span data-ttu-id="5e746-146">❌NIE dodawaj, NIE usuwaj ani nie zmieniaj silnego klucza nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="5e746-146">❌ DO NOT add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="5e746-147">✔️ ROZWAŻ UŻYCIE abstrakcyjnych klas podstawowych zamiast interfejsów.</span><span class="sxs-lookup"><span data-stu-id="5e746-147">✔️ CONSIDER using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="5e746-148">Dodawanie czegokolwiek do interfejsu spowoduje, że istniejące typy, które implementują go nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="5e746-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="5e746-149">Abstrakcyjna klasa podstawowa umożliwia dodanie domyślnej implementacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="5e746-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="5e746-150">✔️ ROZWAŻ <xref:System.ObsoleteAttribute> umieszczenie na typy i elementy członkowskie, które zamierzasz usunąć.</span><span class="sxs-lookup"><span data-stu-id="5e746-150">✔️ CONSIDER placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="5e746-151">Atrybut powinien mieć instrukcje dotyczące aktualizowania kodu, aby nie używać przestarzałego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="5e746-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="5e746-152">Kod, który wywołuje typy <xref:System.ObsoleteAttribute> i metody z wygeneruje ostrzeżenie kompilacji z komunikatem dostarczonym do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5e746-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="5e746-153">Ostrzeżenia dają ludziom, którzy używają przestarzałego czasu powierzchni interfejsu API do migracji, tak aby po usunięciu przestarzałego interfejsu API większość z niego nie używa.</span><span class="sxs-lookup"><span data-stu-id="5e746-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

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

<span data-ttu-id="5e746-154">✔️ NALEŻY ROZWAŻYĆ prowadzenie <xref:System.ObsoleteAttribute> typów i metod z inczasanie w bibliotekach niskiego i średniego poziomu.</span><span class="sxs-lookup"><span data-stu-id="5e746-154">✔️ CONSIDER keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="5e746-155">Usuwanie interfejsów API jest binarną zmianą podziału.</span><span class="sxs-lookup"><span data-stu-id="5e746-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="5e746-156">Biorąc pod uwagę utrzymanie przestarzałych typów i metod, jeśli ich utrzymanie jest niski koszt i nie dodaje wiele długu technicznego do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5e746-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="5e746-157">Nie usunięcie typów i metod może pomóc uniknąć najgorszych scenariuszy wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="5e746-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e746-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e746-158">See also</span></span>

- [<span data-ttu-id="5e746-159">Zagadnienia dotyczące wersji i aktualizacji dla deweloperów języka C#</span><span class="sxs-lookup"><span data-stu-id="5e746-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="5e746-160">Ostateczny przewodnik po zmianach łamania interfejsu API w .NET</span><span class="sxs-lookup"><span data-stu-id="5e746-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="5e746-161">Reguły łamania zmian .NET</span><span class="sxs-lookup"><span data-stu-id="5e746-161">.NET breaking change rules</span></span>](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="5e746-162">Wstecz</span><span class="sxs-lookup"><span data-stu-id="5e746-162">Previous</span></span>](versioning.md)
