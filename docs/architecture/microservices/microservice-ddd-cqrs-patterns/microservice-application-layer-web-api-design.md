---
title: Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Krótkie informacje o PEŁNYch zasadach projektowania warstwy aplikacji.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296739"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="80fed-103">Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API</span><span class="sxs-lookup"><span data-stu-id="80fed-103">Design the microservice application layer and Web API</span></span>

## <a name="use-solid-principles-and-dependency-injection"></a><span data-ttu-id="80fed-104">Korzystanie z PEŁNYch zasad i iniekcji zależności</span><span class="sxs-lookup"><span data-stu-id="80fed-104">Use SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="80fed-105">SOLIDNe zasady są technikami krytycznymi, które mają być używane w dowolnej nowoczesnej i o znaczeniu strategicznym, takich jak tworzenie mikrousług za pomocą wzorów DDD.</span><span class="sxs-lookup"><span data-stu-id="80fed-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="80fed-106">SOLID to akronim, który grupuje pięć podstawowych zasad:</span><span class="sxs-lookup"><span data-stu-id="80fed-106">SOLID is an acronym that groups five fundamental principles:</span></span>

- <span data-ttu-id="80fed-107">Reguła pojedynczego odpowiedzialności</span><span class="sxs-lookup"><span data-stu-id="80fed-107">Single Responsibility principle</span></span>

- <span data-ttu-id="80fed-108">Zasada Otwórz/zamknięty</span><span class="sxs-lookup"><span data-stu-id="80fed-108">Open/closed principle</span></span>

- <span data-ttu-id="80fed-109">Zasada podstawienia Liskov</span><span class="sxs-lookup"><span data-stu-id="80fed-109">Liskov substitution principle</span></span>

- <span data-ttu-id="80fed-110">Zasada segregowania interfejsu</span><span class="sxs-lookup"><span data-stu-id="80fed-110">Interface Segregation principle</span></span>

- <span data-ttu-id="80fed-111">Zasada niewersji zależności</span><span class="sxs-lookup"><span data-stu-id="80fed-111">Dependency Inversion principle</span></span>

<span data-ttu-id="80fed-112">W pełni zawarto więcej informacji o projektowaniu aplikacji lub mikrousług wewnętrznych warstw oraz o rozdzieleniu zależności między nimi.</span><span class="sxs-lookup"><span data-stu-id="80fed-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="80fed-113">Nie jest on powiązany z domeną, ale z projektem technicznym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80fed-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="80fed-114">Zasada końcowa, reguła niezależna od wersji, umożliwia oddzielenie warstwy infrastruktury od reszty warstw, co pozwala na lepszą rozłączoną implementację warstw DDD.</span><span class="sxs-lookup"><span data-stu-id="80fed-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="80fed-115">Iniekcja zależności (DI) jest jednym ze sposobów implementacji zasady Inversion zależności.</span><span class="sxs-lookup"><span data-stu-id="80fed-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="80fed-116">Jest to technika do osiągnięcia swobodnego sprzężenia między obiektami i ich zależnościami.</span><span class="sxs-lookup"><span data-stu-id="80fed-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="80fed-117">Zamiast bezpośrednio tworzyć wystąpienia współpracowników lub używać odwołań statycznych (to jest przy użyciu nowego...), obiekty, które są potrzebne do wykonania swoich akcji (lub "wstrzykiwane do") klasy.</span><span class="sxs-lookup"><span data-stu-id="80fed-117">Rather than directly instantiating collaborators, or using static references (that is, using new…), the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="80fed-118">Najczęściej klasy deklarują swoje zależności za pośrednictwem ich konstruktorów, umożliwiając im przestrzeganie zasad jawnych zależności.</span><span class="sxs-lookup"><span data-stu-id="80fed-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="80fed-119">Iniekcja zależności jest zwykle oparta na określonych kontenerach IoC (Inversion of Control).</span><span class="sxs-lookup"><span data-stu-id="80fed-119">Dependency Injection is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="80fed-120">ASP.NET Core udostępnia prosty wbudowany kontener IoC, ale można również użyć ulubionego kontenera IoC, takiego jak Autofac lub Ninject.</span><span class="sxs-lookup"><span data-stu-id="80fed-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="80fed-121">Dzięki zastosowaniu stałych zasad klasy mogą być w naturalny sposób bardzo małe, dobrze przygotowane i łatwe do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="80fed-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="80fed-122">Ale jak sprawdzić, czy zbyt wiele zależności jest wstrzykiwanych do klas?</span><span class="sxs-lookup"><span data-stu-id="80fed-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="80fed-123">Jeśli używasz funkcji DI przez konstruktora, będzie ona łatwo wykrywać, sprawdzając, czy tylko liczba parametrów dla konstruktora.</span><span class="sxs-lookup"><span data-stu-id="80fed-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="80fed-124">Jeśli istnieje zbyt wiele zależności, zwykle jest to znak ( [zapach kodu](https://deviq.com/code-smells/)), który Klasa próbuje wykonać zbyt wiele, i prawdopodobnie narusza zasadę pojedynczej odpowiedzialności.</span><span class="sxs-lookup"><span data-stu-id="80fed-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="80fed-125">Zajmiemy się kolejnymi szczegółami.</span><span class="sxs-lookup"><span data-stu-id="80fed-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="80fed-126">W związku z tym ten przewodnik wymaga posiadania tylko minimalnej wiedzy o tych tematach.</span><span class="sxs-lookup"><span data-stu-id="80fed-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="80fed-127">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="80fed-127">Additional resources</span></span>

- <span data-ttu-id="80fed-128">**Stałe: podstawowe zasady OOP** </span><span class="sxs-lookup"><span data-stu-id="80fed-128">**SOLID: Fundamental OOP Principles** </span></span>\
  <https://deviq.com/solid/>

- <span data-ttu-id="80fed-129">**Niewersja kontenerów sterowania i wzorzec iniekcji zależności** </span><span class="sxs-lookup"><span data-stu-id="80fed-129">**Inversion of Control Containers and the Dependency Injection pattern** </span></span>\
  <https://martinfowler.com/articles/injection.html>

- <span data-ttu-id="80fed-130">**Steve Smith. Nowy jest przyklejany** </span><span class="sxs-lookup"><span data-stu-id="80fed-130">**Steve Smith. New is Glue** </span></span>\
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> <span data-ttu-id="80fed-131">[Poprzedni](nosql-database-persistence-infrastructure.md)
> [Następny](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="80fed-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
