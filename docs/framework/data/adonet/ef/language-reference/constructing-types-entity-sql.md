---
title: Konstruowanie typów (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 7113aaf1c2caa982a8ab4751928856c1271570cb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251120"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="74b29-102">Konstruowanie typów (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="74b29-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="74b29-103">zawiera trzy rodzaje konstruktorów: konstruktory wierszy, konstruktory nazwanych typów i konstruktory kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74b29-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="74b29-104">Konstruktory wierszy</span><span class="sxs-lookup"><span data-stu-id="74b29-104">Row Constructors</span></span>  
 <span data-ttu-id="74b29-105">Konstruktory wierszy w programie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] służą do konstruowania anonimowych, strukturalnie wpisanych rekordów z co najmniej jednej wartości.</span><span class="sxs-lookup"><span data-stu-id="74b29-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="74b29-106">Typ wyniku konstruktora wierszy jest typem wiersza, którego typy pól odpowiadają typom wartości używanych do konstruowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="74b29-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="74b29-107">Na przykład następujące wyrażenie konstruuje wartość typu `Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="74b29-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="74b29-108">Jeśli nie podasz aliasu dla wyrażenia w konstruktorze wierszy, Entity Framework podejmie próbę wygenerowania jednego.</span><span class="sxs-lookup"><span data-stu-id="74b29-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="74b29-109">Aby uzyskać więcej informacji, zobacz sekcję "reguły aliasów" w temacie [identyfikatory](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="74b29-109">For more information, see the "Aliasing Rules" section in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="74b29-110">W konstruktorze wierszy są stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="74b29-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="74b29-111">Wyrażenia w konstruktorze wierszy nie mogą odwoływać się do innych aliasów w tym samym konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="74b29-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="74b29-112">Dwa wyrażenia w tym samym konstruktorze wierszy nie mogą mieć tego samego aliasu.</span><span class="sxs-lookup"><span data-stu-id="74b29-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="74b29-113">Aby uzyskać więcej informacji na temat konstruktorów wierszy, zobacz [wiersz](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="74b29-113">For more information about row constructors, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="74b29-114">Konstruktory kolekcji</span><span class="sxs-lookup"><span data-stu-id="74b29-114">Collection Constructors</span></span>  
 <span data-ttu-id="74b29-115">Za pomocą konstruktorów kolekcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w programie można utworzyć wystąpienie zestawu wielokrotnego z listy wartości.</span><span class="sxs-lookup"><span data-stu-id="74b29-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="74b29-116">Wszystkie wartości w konstruktorze muszą być wzajemnie zgodnego typu `T`, a Konstruktor tworzy kolekcję typu. `Multiset<T>`</span><span class="sxs-lookup"><span data-stu-id="74b29-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="74b29-117">Na przykład następujące wyrażenie tworzy kolekcję liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="74b29-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="74b29-118">Puste konstruktory wielokrotne są niedozwolone, ponieważ nie można określić typu elementów.</span><span class="sxs-lookup"><span data-stu-id="74b29-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="74b29-119">Następujące elementy są nieprawidłowe:</span><span class="sxs-lookup"><span data-stu-id="74b29-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="74b29-120">Aby uzyskać więcej informacji, zobacz zestaw [wielokrotny](multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="74b29-120">For more information, see [MULTISET](multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="74b29-121">Konstruktory nazwanych typów (inicjatory nazwanych)</span><span class="sxs-lookup"><span data-stu-id="74b29-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="74b29-122">zezwala na konstruktory typów (inicjatory) do tworzenia wystąpień o nazwanych typach złożonych i typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="74b29-122">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="74b29-123">Na przykład następujące wyrażenie tworzy wystąpienie `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="74b29-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="74b29-124">Poniższe wyrażenie tworzy wystąpienie typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="74b29-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="74b29-125">Poniższe wyrażenie tworzy wystąpienie zagnieżdżonego typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="74b29-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="74b29-126">Poniższe wyrażenie tworzy wystąpienie jednostki z zagnieżdżonym typem złożonym.</span><span class="sxs-lookup"><span data-stu-id="74b29-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="74b29-127">Poniższy przykład pokazuje, jak zainicjować właściwość typu złożonego na wartość null.</span><span class="sxs-lookup"><span data-stu-id="74b29-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="74b29-128">Argumenty konstruktora są założono, że są w tej samej kolejności co deklaracja atrybutów typu.</span><span class="sxs-lookup"><span data-stu-id="74b29-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="74b29-129">Aby uzyskać więcej informacji, zobacz [nazwany Konstruktor typów](named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="74b29-129">For more information, see [Named Type Constructor](named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b29-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74b29-130">See also</span></span>

- [<span data-ttu-id="74b29-131">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="74b29-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="74b29-132">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="74b29-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="74b29-133">System typów</span><span class="sxs-lookup"><span data-stu-id="74b29-133">Type System</span></span>](type-system-entity-sql.md)
