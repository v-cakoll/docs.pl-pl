---
title: Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API
description: 'Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | BRIEF: wzmianka stałych zasad projektowania warstwy aplikacji.'
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639506"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="fa447-103">Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API</span><span class="sxs-lookup"><span data-stu-id="fa447-103">Design the microservice application layer and Web API</span></span>

## <a name="use-solid-principles-and-dependency-injection"></a><span data-ttu-id="fa447-104">Użyj stałych zasad i wstrzykiwanie zależności</span><span class="sxs-lookup"><span data-stu-id="fa447-104">Use SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="fa447-105">STAŁE zasady są krytyczne technik, które ma być używany w dowolnej aplikacji nowoczesnych i o kluczowym znaczeniu, takich jak opracowywanie mikrousług przy użyciu wzorców DDD.</span><span class="sxs-lookup"><span data-stu-id="fa447-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="fa447-106">STAŁE jest skrótem tej grupy pięciu podstawowych zasad:</span><span class="sxs-lookup"><span data-stu-id="fa447-106">SOLID is an acronym that groups five fundamental principles:</span></span>

- <span data-ttu-id="fa447-107">Zasady pojedynczej odpowiedzialności</span><span class="sxs-lookup"><span data-stu-id="fa447-107">Single Responsibility principle</span></span>

- <span data-ttu-id="fa447-108">Zasada otwarty/zamknięty</span><span class="sxs-lookup"><span data-stu-id="fa447-108">Open/closed principle</span></span>

- <span data-ttu-id="fa447-109">Zasada podstawienia Liskov</span><span class="sxs-lookup"><span data-stu-id="fa447-109">Liskov substitution principle</span></span>

- <span data-ttu-id="fa447-110">Zasady podziału na interfejsie</span><span class="sxs-lookup"><span data-stu-id="fa447-110">Interface Segregation principle</span></span>

- <span data-ttu-id="fa447-111">Zasada odwrócenie zależności</span><span class="sxs-lookup"><span data-stu-id="fa447-111">Dependency Inversion principle</span></span>

<span data-ttu-id="fa447-112">Więcej na temat sposobu projektowania aplikacji lub mikrousług wewnętrznego warstwy oraz oddzielenie zależności między nimi jest pełny.</span><span class="sxs-lookup"><span data-stu-id="fa447-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="fa447-113">Nie jest powiązany z domeną, ale projekt techniczny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fa447-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="fa447-114">Ostateczne zasady, zasady odwrócenie zależności, można rozdzielić warstwy infrastruktury od reszty warstw, co pozwala lepiej wdrożenia rozdzielonego warstw DDD.</span><span class="sxs-lookup"><span data-stu-id="fa447-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="fa447-115">Wstrzykiwanie zależności (DI) jest jednym ze sposobów, aby zaimplementować zasady odwrócenie zależności.</span><span class="sxs-lookup"><span data-stu-id="fa447-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="fa447-116">Jest to technika do osiągnięcia luźne powiązanie między obiektami i ich zależności.</span><span class="sxs-lookup"><span data-stu-id="fa447-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="fa447-117">Zamiast bezpośrednio wystąpienia współpracowników lub przy użyciu odwołań statycznych, (które przy użyciu nowego...), obiekty, które klasy potrzebuje, aby wykonać działania są udostępniane (lub "wstrzykuje") klasy.</span><span class="sxs-lookup"><span data-stu-id="fa447-117">Rather than directly instantiating collaborators, or using static references (that is, using new…), the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="fa447-118">W większości przypadków klasy uzna ich zależności za pomocą ich konstruktora, umożliwiając im postępuj zgodnie z zasadą jawne zależności.</span><span class="sxs-lookup"><span data-stu-id="fa447-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="fa447-119">Wstrzykiwanie zależności opiera się zwykle w określonych kontenerach Inwersja kontroli (IoC).</span><span class="sxs-lookup"><span data-stu-id="fa447-119">Dependency Injection is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="fa447-120">Platforma ASP.NET Core udostępnia prostego, wbudowanego kontenera IoC, ale można również użyć kontenera IoC Ulubione, takich jak Autofac lub Ninject.</span><span class="sxs-lookup"><span data-stu-id="fa447-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="fa447-121">Postępując zgodnie z zasadami stałych, klas będą zwykle naturalnie za małe, dobrze uwarunkowaną i łatwo przetestowane.</span><span class="sxs-lookup"><span data-stu-id="fa447-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="fa447-122">Ale jak należy znać, jeśli zbyt wiele zależności są są wprowadzane w Twoich zajęciach?</span><span class="sxs-lookup"><span data-stu-id="fa447-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="fa447-123">Jeśli używasz DI za pośrednictwem konstruktora będzie łatwe do wykrycia, patrząc tylko na liczbę parametrów dla konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fa447-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="fa447-124">Jeśli istnieje zbyt wiele zależności, zwykle jest to znak ( [kodu zapachu](https://deviq.com/code-smells/)) próbuje wykonać zbyt dużo klasy i prawdopodobnie narusza zasadę pojedynczej odpowiedzialności.</span><span class="sxs-lookup"><span data-stu-id="fa447-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="fa447-125">Zajęłoby innego przewodnika, aby omówić stałe.</span><span class="sxs-lookup"><span data-stu-id="fa447-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="fa447-126">W związku z tym ten przewodnik wymaga posiadania minimalnej znajomości tych tematów.</span><span class="sxs-lookup"><span data-stu-id="fa447-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="fa447-127">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fa447-127">Additional resources</span></span>

- <span data-ttu-id="fa447-128">**SOLID: Obiektowo podstawowych zasad** \\</span><span class="sxs-lookup"><span data-stu-id="fa447-128">**SOLID: Fundamental OOP Principles** \\</span></span>
  <https://deviq.com/solid/>

- <span data-ttu-id="fa447-129">**Inwersja kontroli kontenerów i wzorzec wstrzykiwanie zależności** \\</span><span class="sxs-lookup"><span data-stu-id="fa447-129">**Inversion of Control Containers and the Dependency Injection pattern** \\</span></span>
  <https://martinfowler.com/articles/injection.html>

- <span data-ttu-id="fa447-130">**Steve Smith. Nowością jest pośredniczącego** \\</span><span class="sxs-lookup"><span data-stu-id="fa447-130">**Steve Smith. New is Glue** \\</span></span>
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> <span data-ttu-id="fa447-131">[Poprzednie](nosql-database-persistence-infrastructure.md)
> [dalej](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="fa447-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
