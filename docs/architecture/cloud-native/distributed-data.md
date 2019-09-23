---
title: Rozproszone dane
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Rozproszone dane dla natywnych aplikacji w chmurze
ms.date: 06/30/2019
ms.openlocfilehash: 92086c52b02360e90461aea9ad23a2068224e187
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183134"
---
# <a name="distributed-data-for-cloud-native-apps"></a><span data-ttu-id="fbefd-103">Rozproszone dane dla aplikacji natywnych w chmurze</span><span class="sxs-lookup"><span data-stu-id="fbefd-103">Distributed data for cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="fbefd-104">Podczas konstruowania systemu natywnego w chmurze, który składa się z wielu niezależnych mikrousług, w zależności od tego, jak sądzisz o zmianach w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="fbefd-104">When constructing a cloud-native system that consists of many independent microservices, the way you think about data storage changes.</span></span>

<span data-ttu-id="fbefd-105">Tradycyjne aplikacje monolityczne preferują scentralizowany magazyn danych przedstawiony na rysunku 5-1.</span><span class="sxs-lookup"><span data-stu-id="fbefd-105">Traditional monolithic applications favor a centralized data store shown in Figure 5-1.</span></span> 

![Pojedyncza monolityczna baza danych](./media/single-monolithic-database.png)

<span data-ttu-id="fbefd-107">**Rysunek 5-1**.</span><span class="sxs-lookup"><span data-stu-id="fbefd-107">**Figure 5-1**.</span></span> <span data-ttu-id="fbefd-108">Pojedyncza monolityczna baza danych</span><span class="sxs-lookup"><span data-stu-id="fbefd-108">Single monolithic database</span></span>

<span data-ttu-id="fbefd-109">Zwróć uwagę na powyższym rysunku, w jaki sposób wszystkie składniki aplikacji używają pojedynczej relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fbefd-109">Note in the previous figure how all of the application components consume a single relational database.</span></span>

<span data-ttu-id="fbefd-110">Ta metoda ma wiele zalet.</span><span class="sxs-lookup"><span data-stu-id="fbefd-110">There are many benefits to this approach.</span></span> <span data-ttu-id="fbefd-111">Wykonywanie zapytań dotyczących rozmieszczenia danych w wielu tabelach jest proste i jest to proste w zaimplementowanie [transakcji kwaśnych](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) , które zapewniają spójność danych.</span><span class="sxs-lookup"><span data-stu-id="fbefd-111">It's straightforward to query data spread across  multiple tables, and it's straightforward to implement [ACID transactions](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) that ensure data consistency.</span></span> <span data-ttu-id="fbefd-112">Zawsze możesz mieć *natychmiastową spójność*: wszystkie aktualizacje danych lub żadne z nich nie są używane.</span><span class="sxs-lookup"><span data-stu-id="fbefd-112">You always end up with *immediate consistency*: either all your data updates or none of it does.</span></span>

<span data-ttu-id="fbefd-113">Systemy natywne w chmurze preferują architekturę danych pokazaną na rysunku 5-2, w której każda mikrousługa jest właścicielem i hermetyzuje własne dane.</span><span class="sxs-lookup"><span data-stu-id="fbefd-113">Cloud-native systems favor a data architecture shown in Figure 5-2 in which each microservice owns and encapsulates its own data.</span></span>

![Wiele baz danych w mikrousługach](./media/data-across-microservices.png)

<span data-ttu-id="fbefd-115">**Rysunek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="fbefd-115">**Figure 5-2**.</span></span> <span data-ttu-id="fbefd-116">Wiele baz danych w mikrousługach</span><span class="sxs-lookup"><span data-stu-id="fbefd-116">Multiple databases across microservices</span></span>

<span data-ttu-id="fbefd-117">Zwróć uwagę na to, jak na poprzedniej ilustracji każda mikrousługa posiada i hermetyzuje magazyn danych IT i udostępnia tylko dane na świecie zewnętrznym ze swojego publicznego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="fbefd-117">Note how in the previous figure each microservice owns and encapsulates it data store and only exposes data to the outside world from its public API.</span></span>
 
<span data-ttu-id="fbefd-118">Ten model umożliwia samodzielne rozdzielenie każdej mikrousług bez konieczności koordynowania zmian schematu danych z innymi mikrousługami.</span><span class="sxs-lookup"><span data-stu-id="fbefd-118">This model enables each microservice to evolve independently without having to coordinate data schema changes with other microservices.</span></span> <span data-ttu-id="fbefd-119">Każda mikrousługa jest bezpłatna do wdrożenia magazynu danych (relacyjnej bazy danych, bazy danych dokumentów, magazynu klucz-wartość), który najlepiej odpowiada potrzebom.</span><span class="sxs-lookup"><span data-stu-id="fbefd-119">Each microservice is free to implement the data store (relational database, document database, key-value store) type that best matches its needs.</span></span> <span data-ttu-id="fbefd-120">W czasie wykonywania każda mikrousługa może odpowiednio skalować swoje dane.</span><span class="sxs-lookup"><span data-stu-id="fbefd-120">At runtime, each microservice can scale its data accordingly.</span></span> <span data-ttu-id="fbefd-121">Jest to pokazane na rysunku 5-3:</span><span class="sxs-lookup"><span data-stu-id="fbefd-121">This is shown in Figure 5-3:</span></span>

![Trwałość danych Polyglot](./media/polyglot-data-persistence.png)

<span data-ttu-id="fbefd-123">**Rysunek 5-3**.</span><span class="sxs-lookup"><span data-stu-id="fbefd-123">**Figure 5-3**.</span></span> <span data-ttu-id="fbefd-124">Trwałość danych Polyglot</span><span class="sxs-lookup"><span data-stu-id="fbefd-124">Polyglot data persistence</span></span>

<span data-ttu-id="fbefd-125">Zwróć uwagę na to, jak na poprzedniej ilustracji, w jaki sposób katalog produktów i mikrousługi spisu przyjmują relacyjne bazy danych, mikrousługa do porządkowania, baza danych dokumentów NoSql oraz mikrousługa koszyka zakupów, który jest zewnętrznym magazynem wartości.</span><span class="sxs-lookup"><span data-stu-id="fbefd-125">Note how in the previous figure the product catalog and inventory microservices adopt relational databases, the ordering microservice, a NoSql document database, and the shopping cart microservice, which is an external key-value store.</span></span> <span data-ttu-id="fbefd-126">Relacyjne bazy danych pozostają istotne dla mikrousług z danymi złożonymi, jednak bazy danych NoSQL uzyskały znaczną popularność, zapewniając możliwość adaptacji, szybkie wyszukiwanie i wysoką dostępność.</span><span class="sxs-lookup"><span data-stu-id="fbefd-126">While relational databases remain relevant for microservices with complex data, NoSQL databases have gained considerable popularity, providing adaptability, fast lookup, and high availability.</span></span> <span data-ttu-id="fbefd-127">Ich charakter bez schematu pozwala deweloperom poruszać się od architektury klas danych z określonym typem i ORMs, co sprawia, że zmiany są kosztowne i czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="fbefd-127">Their schemaless nature allows developers to move away from an architecture of typed data classes and ORMs that make change expensive and time-consuming.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fbefd-128">[Poprzedni](service-mesh-communication-infrastructure.md)
>[Następny](data-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="fbefd-128">[Previous](service-mesh-communication-infrastructure.md)
[Next](data-patterns.md)</span></span>
