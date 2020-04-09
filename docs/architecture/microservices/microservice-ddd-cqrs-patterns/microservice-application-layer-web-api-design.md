---
title: Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Krótka wzmianka o zasadach SOLID do projektowania warstwy aplikacji.
ms.date: 10/08/2018
ms.openlocfilehash: 491aa7bd90910c7f6c1d0ab56edfe0ae057ca006
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988456"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="699b2-103">Projektowanie warstwy aplikacji mikrousług i interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="699b2-103">Design the microservice application layer and Web API</span></span>

## <a name="use-solid-principles-and-dependency-injection"></a><span data-ttu-id="699b2-104">Użyj zasad SOLID i iniekcji zależności</span><span class="sxs-lookup"><span data-stu-id="699b2-104">Use SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="699b2-105">Zasady SOLID są krytyczne techniki, które mają być używane w każdej nowoczesnej i krytycznej aplikacji, takich jak tworzenie mikrousługi z wzorców DDD.</span><span class="sxs-lookup"><span data-stu-id="699b2-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="699b2-106">SOLID to akronim, który grupuje pięć podstawowych zasad:</span><span class="sxs-lookup"><span data-stu-id="699b2-106">SOLID is an acronym that groups five fundamental principles:</span></span>

- <span data-ttu-id="699b2-107">Zasada jednolitej odpowiedzialności</span><span class="sxs-lookup"><span data-stu-id="699b2-107">Single Responsibility principle</span></span>

- <span data-ttu-id="699b2-108">Zasada otwarcia/zamknięcia</span><span class="sxs-lookup"><span data-stu-id="699b2-108">Open/closed principle</span></span>

- <span data-ttu-id="699b2-109">Zasada zastępowania Liskova</span><span class="sxs-lookup"><span data-stu-id="699b2-109">Liskov substitution principle</span></span>

- <span data-ttu-id="699b2-110">Zasada segregacji interfejsu</span><span class="sxs-lookup"><span data-stu-id="699b2-110">Interface Segregation principle</span></span>

- <span data-ttu-id="699b2-111">Zasada inwersji zależności</span><span class="sxs-lookup"><span data-stu-id="699b2-111">Dependency Inversion principle</span></span>

<span data-ttu-id="699b2-112">SOLID jest bardziej o tym, jak projektować warstwy wewnętrzne aplikacji lub mikrousług i o oddzielenie zależności między nimi.</span><span class="sxs-lookup"><span data-stu-id="699b2-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="699b2-113">Nie jest to związane z domeną, ale z projektem technicznym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="699b2-113">It is not related to the domain, but to the application's technical design.</span></span> <span data-ttu-id="699b2-114">Ostateczna zasada, zasada Inwersji zależności, pozwala na oddzielenie warstwy infrastruktury od pozostałych warstw, co pozwala na lepszą implementację oddzielonych warstw DDD.</span><span class="sxs-lookup"><span data-stu-id="699b2-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="699b2-115">Iniekcja zależności (DI) jest jednym ze sposobów zaimplementowania zasady inwersji zależności.</span><span class="sxs-lookup"><span data-stu-id="699b2-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="699b2-116">Jest to technika osiągnięcia luźnego sprzężenia między obiektami i ich zależnościami.</span><span class="sxs-lookup"><span data-stu-id="699b2-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="699b2-117">Zamiast bezpośrednio tworzenia wystąpienia współpracowników lub przy użyciu odwołań statycznych (czyli przy użyciu nowych ...), obiekty, które klasa potrzebuje w celu wykonania jego akcji są dostarczane do (lub "wstrzykuje się do") klasy.</span><span class="sxs-lookup"><span data-stu-id="699b2-117">Rather than directly instantiating collaborators, or using static references (that is, using new…), the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="699b2-118">Najczęściej klasy deklaruje ich zależności za pośrednictwem ich konstruktora, umożliwiając im przestrzeganie zasady jawne zależności.</span><span class="sxs-lookup"><span data-stu-id="699b2-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="699b2-119">Iniekcja zależności jest zwykle oparta na określonych kontenerach inwersji kontroli (IoC).</span><span class="sxs-lookup"><span data-stu-id="699b2-119">Dependency Injection is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="699b2-120">ASP.NET Core zapewnia prosty wbudowany kontener IoC, ale można również użyć ulubionego kontenera IoC, takiego jak Autofac lub Ninject.</span><span class="sxs-lookup"><span data-stu-id="699b2-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="699b2-121">Zgodnie z zasadami SOLID, twoje klasy będą naturalnie małe, dobrze uwzględnione i łatwo przetestowane.</span><span class="sxs-lookup"><span data-stu-id="699b2-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="699b2-122">Ale skąd wiesz, czy zbyt wiele zależności są wstrzykiwane do klas?</span><span class="sxs-lookup"><span data-stu-id="699b2-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="699b2-123">Jeśli używasz DI za pośrednictwem konstruktora, będzie łatwo wykryć, że po prostu patrząc na liczbę parametrów dla konstruktora.</span><span class="sxs-lookup"><span data-stu-id="699b2-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="699b2-124">Jeśli istnieje zbyt wiele zależności, jest to zazwyczaj znak [(zapach kodu),](https://deviq.com/code-smells/)że klasa próbuje zrobić zbyt wiele i prawdopodobnie narusza zasadę pojedynczej odpowiedzialności.</span><span class="sxs-lookup"><span data-stu-id="699b2-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="699b2-125">Zajęłoby inny przewodnik, aby pokryć SOLID w szczegółach.</span><span class="sxs-lookup"><span data-stu-id="699b2-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="699b2-126">W związku z tym ten przewodnik wymaga, aby mieć tylko minimalną wiedzę na te tematy.</span><span class="sxs-lookup"><span data-stu-id="699b2-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="699b2-127">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="699b2-127">Additional resources</span></span>

- <span data-ttu-id="699b2-128">**SOLID: Podstawowe zasady OOP** </span><span class="sxs-lookup"><span data-stu-id="699b2-128">**SOLID: Fundamental OOP Principles** </span></span>\
  <https://deviq.com/solid/>

- <span data-ttu-id="699b2-129">**Inwersja kontenerów kontrolnych i wzorzec iniekcji zależności** </span><span class="sxs-lookup"><span data-stu-id="699b2-129">**Inversion of Control Containers and the Dependency Injection pattern** </span></span>\
  <https://martinfowler.com/articles/injection.html>

- <span data-ttu-id="699b2-130">**Steve Smith. Nowy jest klej** </span><span class="sxs-lookup"><span data-stu-id="699b2-130">**Steve Smith. New is Glue** </span></span>\
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> <span data-ttu-id="699b2-131">[Poprzedni](nosql-database-persistence-infrastructure.md)
> [następny](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="699b2-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
