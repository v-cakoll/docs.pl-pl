---
title: Funkcje Canonical
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: f8ca9e2027e82db89e91287fda02d2014d53f325
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854511"
---
# <a name="canonical-functions"></a><span data-ttu-id="7051a-102">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="7051a-102">Canonical Functions</span></span>
<span data-ttu-id="7051a-103">W tej sekcji omówiono funkcje kanoniczne, które są obsługiwane przez wszystkich dostawców danych, i mogą być używane przez wszystkie technologie zapytań.</span><span class="sxs-lookup"><span data-stu-id="7051a-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="7051a-104">Nie można rozszerzyć funkcji kanonicznych przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="7051a-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="7051a-105">Te funkcje kanoniczne zostaną przetłumaczone na odpowiednie funkcje źródła danych dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="7051a-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="7051a-106">Pozwala to na wywołania funkcji wyrażone w typowym formacie między źródłami danych.</span><span class="sxs-lookup"><span data-stu-id="7051a-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="7051a-107">Ponieważ te funkcje kanoniczne są niezależne od źródeł danych, argument i zwracane typy funkcji kanonicznych są zdefiniowane w kategoriach typów w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="7051a-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="7051a-108">Jednak niektóre źródła danych mogą nie obsługiwać wszystkich typów w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="7051a-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="7051a-109">Jeśli w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytaniu są używane funkcje kanoniczne, odpowiednia funkcja zostanie wywołana w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="7051a-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="7051a-110">Wszystkie funkcje kanoniczne mają zarówno zachowanie danych wejściowych, jak i jawne określone warunki błędu.</span><span class="sxs-lookup"><span data-stu-id="7051a-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="7051a-111">Dostawcy sklepu powinni przestrzegać tego zachowania, ale Entity Framework nie wymusza tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="7051a-111">Store providers should comply with that behavior, but Entity Framework does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="7051a-112">W przypadku scenariuszy LINQ zapytania dotyczące Entity Framework obejmują mapowanie metod CLR do metod w podstawowym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="7051a-112">For LINQ scenarios, queries against the Entity Framework involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="7051a-113">Metody CLR mapują na funkcje kanoniczne, dzięki czemu określony zestaw metod będzie poprawnie mapowany, niezależnie od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7051a-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="7051a-114">Przestrzeń nazw funkcji kanonicznych</span><span class="sxs-lookup"><span data-stu-id="7051a-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="7051a-115">Przestrzeń nazw dla funkcji kanonicznej <xref:System.Data.Metadata.Edm>to.</span><span class="sxs-lookup"><span data-stu-id="7051a-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="7051a-116"><xref:System.Data.Metadata.Edm> Przestrzeń nazw jest automatycznie dołączana do wszystkich zapytań.</span><span class="sxs-lookup"><span data-stu-id="7051a-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="7051a-117">Jeśli jednak zostanie zaimportowana inna przestrzeń nazw, która zawiera funkcję o takiej samej nazwie jak funkcja kanoniczna ( <xref:System.Data.Metadata.Edm> w przestrzeni nazw), należy określić przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="7051a-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7051a-118">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7051a-118">In This Section</span></span>  
 [<span data-ttu-id="7051a-119">Funkcje agregujące Canonical</span><span class="sxs-lookup"><span data-stu-id="7051a-119">Aggregate Canonical Functions</span></span>](aggregate-canonical-functions.md)  
 <span data-ttu-id="7051a-120">Omawia agregacje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcji w postaci kanonicznej.</span><span class="sxs-lookup"><span data-stu-id="7051a-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="7051a-121">Funkcje matematyczne Canonical</span><span class="sxs-lookup"><span data-stu-id="7051a-121">Math Canonical Functions</span></span>](math-canonical-functions.md)  
 <span data-ttu-id="7051a-122">Omawia funkcje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] matematyczne w postaci kanonicznej.</span><span class="sxs-lookup"><span data-stu-id="7051a-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="7051a-123">Funkcje ciągów Canonical</span><span class="sxs-lookup"><span data-stu-id="7051a-123">String Canonical Functions</span></span>](string-canonical-functions.md)  
 <span data-ttu-id="7051a-124">Omawia funkcje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ciągów kanonicznych.</span><span class="sxs-lookup"><span data-stu-id="7051a-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="7051a-125">Funkcji daty i godziny Canonical</span><span class="sxs-lookup"><span data-stu-id="7051a-125">Date and Time Canonical Functions</span></span>](date-and-time-canonical-functions.md)  
 <span data-ttu-id="7051a-126">Omawia funkcje kanoniczne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="7051a-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="7051a-127">Funkcje bitowe Canonical</span><span class="sxs-lookup"><span data-stu-id="7051a-127">Bitwise Canonical Functions</span></span>](bitwise-canonical-functions.md)  
 <span data-ttu-id="7051a-128">Omawia bitowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje kanoniczne.</span><span class="sxs-lookup"><span data-stu-id="7051a-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="7051a-129">Funkcje przestrzenne</span><span class="sxs-lookup"><span data-stu-id="7051a-129">Spatial Functions</span></span>](spatial-functions.md)  
 <span data-ttu-id="7051a-130">Omawia funkcje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przestrzenne w postaci kanonicznej.</span><span class="sxs-lookup"><span data-stu-id="7051a-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="7051a-131">Inne funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="7051a-131">Other Canonical Functions</span></span>](other-canonical-functions.md)  
 <span data-ttu-id="7051a-132">Omawia funkcje niesklasyfikowane jako bitowe, daty/godziny, String, Math lub Aggregate.</span><span class="sxs-lookup"><span data-stu-id="7051a-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7051a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7051a-133">See also</span></span>

- [<span data-ttu-id="7051a-134">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="7051a-134">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="7051a-135">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="7051a-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="7051a-136">Model koncepcyjny Canonical do mapowania funkcji serwera SQL</span><span class="sxs-lookup"><span data-stu-id="7051a-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="7051a-137">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="7051a-137">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)
