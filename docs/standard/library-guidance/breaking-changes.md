---
title: Istotne zmiany i biblioteki .NET
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących nawigowania po zmianach podczas tworzenia bibliotek .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6881b8737d9dd3fa7fa71f099fa1dc97b747033d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104658"
---
# <a name="breaking-changes"></a><span data-ttu-id="4540f-103">Fundamentalne zmiany</span><span class="sxs-lookup"><span data-stu-id="4540f-103">Breaking changes</span></span>

<span data-ttu-id="4540f-104">Ważne jest, aby w bibliotece .NET znaleźć równowagę między stabilnością dla istniejących użytkowników i innowacji w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="4540f-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="4540f-105">Autorzy biblioteki mają do refaktoryzacji i reprezentacji kodu do momentu idealnego, ale przerwanie istniejących użytkowników ma negatywny wpływ, szczególnie w przypadku bibliotek niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="4540f-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="4540f-106">Typy projektów i istotne zmiany</span><span class="sxs-lookup"><span data-stu-id="4540f-106">Project types and breaking changes</span></span>

<span data-ttu-id="4540f-107">Sposób, w jaki biblioteka jest używana przez społeczność programu .NET, zmienia wpływ na istotne zmiany w deweloperach użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="4540f-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

- <span data-ttu-id="4540f-108">**Biblioteki niskie i średnie na poziomie** , takie jak Serializator, analizator składni HTML, mapowanie relacyjne obiektów bazy danych lub platforma internetowa, są najbardziej narażone na podstawie istotnych zmian.</span><span class="sxs-lookup"><span data-stu-id="4540f-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="4540f-109">Pakiety bloków konstrukcyjnych są używane przez deweloperów użytkowników końcowych do kompilowania aplikacji i innych bibliotek jako zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="4540f-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="4540f-110">Na przykład tworzysz aplikację i używam klienta typu open source do wywoływania usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4540f-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="4540f-111">Nieprzerwana Aktualizacja zależności użytej przez klienta nie jest coś, co można naprawić.</span><span class="sxs-lookup"><span data-stu-id="4540f-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="4540f-112">Jest to klient open-source, który musi zostać zmieniony i nie ma kontroli nad nim.</span><span class="sxs-lookup"><span data-stu-id="4540f-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="4540f-113">Musisz znaleźć zgodne wersje bibliotek lub przesłać poprawkę do biblioteki klienta i poczekać na nową wersję.</span><span class="sxs-lookup"><span data-stu-id="4540f-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="4540f-114">W przypadku najgorszego przypadku należy użyć dwóch bibliotek, które są zależne od wzajemnie niezgodnych wersji trzeciej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4540f-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

- <span data-ttu-id="4540f-115">**Biblioteki wysokiego poziomu** , takie jak zestaw formantów interfejsu użytkownika, są mniej wrażliwe na istotne zmiany.</span><span class="sxs-lookup"><span data-stu-id="4540f-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="4540f-116">Biblioteki wysokiego poziomu są bezpośrednio przywoływane w aplikacji użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="4540f-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="4540f-117">Jeśli wystąpią istotne zmiany, deweloper może zdecydować się na zaktualizowanie do najnowszej wersji lub zmodyfikować swoją aplikację, aby działała ze zmianą.</span><span class="sxs-lookup"><span data-stu-id="4540f-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="4540f-118">**✔️ należy** zastanowić się, jak zostanie użyta Biblioteka.</span><span class="sxs-lookup"><span data-stu-id="4540f-118">**✔️ DO** think about how your library will be used.</span></span> <span data-ttu-id="4540f-119">Jakie skutki spowodują uszkodzenie zmian w aplikacjach i bibliotekach, które go używają?</span><span class="sxs-lookup"><span data-stu-id="4540f-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="4540f-120">**✔️** zminimalizować zmiany podczas tworzenia biblioteki .NET niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="4540f-120">**✔️ DO** minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="4540f-121">**✔️ rozważyć** opublikowanie poważnego ponownego zapisania biblioteki jako nowego pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="4540f-121">**✔️ CONSIDER** publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="4540f-122">Typy istotnych zmian</span><span class="sxs-lookup"><span data-stu-id="4540f-122">Types of breaking changes</span></span>

<span data-ttu-id="4540f-123">Istotne zmiany mieszczą się w różnych kategoriach i nie wpływają na nie.</span><span class="sxs-lookup"><span data-stu-id="4540f-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="4540f-124">Zmiana podziału źródła</span><span class="sxs-lookup"><span data-stu-id="4540f-124">Source breaking change</span></span>

<span data-ttu-id="4540f-125">Zmiana powodująca uszkodzenie źródłowa nie ma wpływu na wykonanie programu, ale spowoduje błędy kompilacji przy następnym ponownym skompilowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4540f-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="4540f-126">Na przykład nowe Przeciążenie może utworzyć niejednoznaczność wywołań metod, które były niejednoznaczne wcześniej, lub parametr o zmienionej nazwie spowoduje przerwanie wywołań, które używają nazwanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="4540f-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="4540f-127">Ze względu na to, że istotne zmiany w źródle są tylko szkodliwe, gdy deweloperzy ponownie skompilują swoje aplikacje, jest to najmniej zakłócona zmiana.</span><span class="sxs-lookup"><span data-stu-id="4540f-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="4540f-128">Deweloperzy mogą łatwo naprawić swój własny uszkodzony kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="4540f-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="4540f-129">Zmiana powodująca przerwanie działania</span><span class="sxs-lookup"><span data-stu-id="4540f-129">Behavior breaking change</span></span>

<span data-ttu-id="4540f-130">Zmiany zachowania są najczęściej spotykanym typem zmiany: prawie każda zmiana w zachowaniu może spowodować uszkodzenie kogoś.</span><span class="sxs-lookup"><span data-stu-id="4540f-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="4540f-131">Zmiany w bibliotece, takie jak sygnatury metod, zgłoszone wyjątki lub dane wejściowe lub wyjściowe, mogą mieć negatywny wpływ na użytkowników biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4540f-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="4540f-132">Nawet poprawka usterki może zakwalifikować się jako istotna zmiana, jeśli użytkownicy skorzystali z wcześniej naruszonych zachowań.</span><span class="sxs-lookup"><span data-stu-id="4540f-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="4540f-133">Dodawanie funkcji i ulepszanie nieprawidłowych zachowań jest dobrym sposobem, ale bez poważnego, aby użytkownicy mogli je uaktualnić.</span><span class="sxs-lookup"><span data-stu-id="4540f-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="4540f-134">Jednym z rozwiązań ułatwiających deweloperom Rozwiązywanie istotnych zmian w zachowaniu zachowania jest ukrycie ich za pomocą ustawień.</span><span class="sxs-lookup"><span data-stu-id="4540f-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="4540f-135">Ustawienia umożliwiają deweloperom aktualizację do najnowszej wersji biblioteki, jednocześnie wybierając opcję rezygnacji lub zrezygnowanie z istotnych zmian.</span><span class="sxs-lookup"><span data-stu-id="4540f-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="4540f-136">Ta strategia umożliwia deweloperom zachowanie aktualności, a jednocześnie pozwala na dostosowanie kodu do swoich potrzeb.</span><span class="sxs-lookup"><span data-stu-id="4540f-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="4540f-137">Na przykład ASP.NET Core MVC ma koncepcję [wersji zgodności](/aspnet/core/mvc/compatibility-version) , która modyfikuje funkcje włączone i wyłączone `MvcOptions`.</span><span class="sxs-lookup"><span data-stu-id="4540f-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="4540f-138">**✔️ rozważyć** pozostawienie nowych funkcji domyślnie, jeśli wpływają one na istniejących użytkowników, i pozwól deweloperom na dostęp do funkcji przy użyciu ustawienia.</span><span class="sxs-lookup"><span data-stu-id="4540f-138">**✔️ CONSIDER** leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="4540f-139">Zmiana podziału binarnego</span><span class="sxs-lookup"><span data-stu-id="4540f-139">Binary breaking change</span></span>

<span data-ttu-id="4540f-140">Zmiana publicznego interfejsu API biblioteki jest spowodowana zmianą w postaci binarnej, więc zestawy skompilowane pod kątem starszych wersji biblioteki nie będą już mogły wywoływania interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="4540f-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="4540f-141">Na przykład zmiana sygnatury metody przez dodanie nowego parametru spowoduje, <xref:System.MissingMethodException>że zestawy skompilowane dla starszej wersji biblioteki w celu wygenerowania.</span><span class="sxs-lookup"><span data-stu-id="4540f-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="4540f-142">Zmiana podziału binarnego może również spowodować przerwanie **całego zestawu**.</span><span class="sxs-lookup"><span data-stu-id="4540f-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="4540f-143">Zmiana nazwy zestawu za pomocą `AssemblyName` spowoduje zmianę tożsamości zestawu, ponieważ spowoduje to dodanie, usunięcie lub zmianę klucza silnego nazewnictwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="4540f-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="4540f-144">Zmiana tożsamości zestawu spowoduje przerwanie całego skompilowanego kodu, który go używa.</span><span class="sxs-lookup"><span data-stu-id="4540f-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="4540f-145">**❌ Nie** zmieniać nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="4540f-145">**❌ DO NOT** change an assembly name.</span></span>

<span data-ttu-id="4540f-146">**❌ Nie** dodawaj, usuwaj ani nie zmieniaj silnego klucza nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="4540f-146">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="4540f-147">**✔️ rozważyć** użycie abstrakcyjnych klas podstawowych zamiast interfejsów.</span><span class="sxs-lookup"><span data-stu-id="4540f-147">**✔️ CONSIDER** using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="4540f-148">Dodanie niczego do interfejsu spowoduje niepowodzenie istniejących typów, które implementują go.</span><span class="sxs-lookup"><span data-stu-id="4540f-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="4540f-149">Abstrakcyjna klasa bazowa umożliwia dodanie domyślnej implementacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="4540f-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="4540f-150">**✔️ Rozważ** umieszczenie <xref:System.ObsoleteAttribute> typów i członków, które zamierzasz usunąć.</span><span class="sxs-lookup"><span data-stu-id="4540f-150">**✔️ CONSIDER** placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="4540f-151">Atrybut powinien zawierać instrukcje dotyczące aktualizowania kodu, aby nie używał już przestarzałego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="4540f-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="4540f-152">Kod, który wywołuje typy i metody z <xref:System.ObsoleteAttribute> wygenerowaniem ostrzeżenia kompilacji z komunikatem dostarczonym do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4540f-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="4540f-153">Ostrzeżenia umożliwiają osobom korzystającym z przestarzałego czasu powierzchni interfejsu API na Migrowanie w celu usunięcia przestarzałego interfejsu API, który nie będzie już używany.</span><span class="sxs-lookup"><span data-stu-id="4540f-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

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

<span data-ttu-id="4540f-154">**✔️ rozważyć** utrzymywanie typów i metod <xref:System.ObsoleteAttribute> w nieokreślony sposób w przypadku bibliotek niskie i średnie.</span><span class="sxs-lookup"><span data-stu-id="4540f-154">**✔️ CONSIDER** keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="4540f-155">Usuwanie interfejsów API jest uszkodzeniem binarnym.</span><span class="sxs-lookup"><span data-stu-id="4540f-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="4540f-156">Biorąc pod uwagę przechowywanie przestarzałych typów i metod, jeśli ich utrzymanie jest niskiego kosztu i nie dodaje do biblioteki dużej liczby długów technicznych.</span><span class="sxs-lookup"><span data-stu-id="4540f-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="4540f-157">Nieusunięcie typów i metod może pomóc w uniknięciu najgorszych przypadków wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="4540f-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="4540f-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4540f-158">See also</span></span>

- [<span data-ttu-id="4540f-159">Zagadnienia dotyczące wersji i C# aktualizacji dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="4540f-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="4540f-160">Ostateczny Przewodnik po wprowadzeniu zmian w interfejsie API w programie .NET</span><span class="sxs-lookup"><span data-stu-id="4540f-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="4540f-161">CoreFX reguły zmiany reguł</span><span class="sxs-lookup"><span data-stu-id="4540f-161">CoreFX Breaking Change Rules</span></span>](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="4540f-162">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="4540f-162">Previous</span></span>](versioning.md)
