---
title: Konstruowanie typów (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 53aa7fcc82a476c8b8bd87b059e08bee6741c0d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605841"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="f26c6-102">Konstruowanie typów (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="f26c6-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f26c6-103">zawiera trzy rodzaje konstruktorów: wiersz konstruktorów, typu nazwanego konstruktorów i konstruktorów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f26c6-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="f26c6-104">Konstruktory wiersza</span><span class="sxs-lookup"><span data-stu-id="f26c6-104">Row Constructors</span></span>  
 <span data-ttu-id="f26c6-105">Użyj wiersza konstruktorów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do konstruowania anonimowe, strukturalnie wpisane rekordy z co najmniej jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="f26c6-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="f26c6-106">Typ wyniku w Konstruktorze wierszy jest typu wiersza, w których typy pól odpowiadają typy wartości używane do konstruowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="f26c6-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="f26c6-107">Na przykład poniższe wyrażenie tworzy wartość typu `Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="f26c6-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="f26c6-108">Jeśli nie podasz alias wyrażenia w Konstruktorze wierszy, platformy Entity Framework podejmie próbę go wygeneruje.</span><span class="sxs-lookup"><span data-stu-id="f26c6-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="f26c6-109">Aby uzyskać więcej informacji, zobacz sekcję "Zasady aliasowania" w [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f26c6-109">For more information, see the "Aliasing Rules" section in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="f26c6-110">Następujące reguły stosuje się do wyrażenia aliasów w Konstruktorze wierszy:</span><span class="sxs-lookup"><span data-stu-id="f26c6-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="f26c6-111">Wyrażenia w Konstruktorze row nie może odwoływać się do innych aliasów w tej samej konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f26c6-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="f26c6-112">Dwóch wyrażeń w tym samym Konstruktor row nie może mieć takiego samego aliasu.</span><span class="sxs-lookup"><span data-stu-id="f26c6-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="f26c6-113">Aby uzyskać więcej informacji na temat konstruktory wiersz zobacz [wiersza](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f26c6-113">For more information about row constructors, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="f26c6-114">Konstruktory kolekcji</span><span class="sxs-lookup"><span data-stu-id="f26c6-114">Collection Constructors</span></span>  
 <span data-ttu-id="f26c6-115">Możesz użyć kolekcji konstruktorów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do utworzenia wystąpienia zestawu wielokrotnego z listy wartości.</span><span class="sxs-lookup"><span data-stu-id="f26c6-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="f26c6-116">Wszystkie wartości w Konstruktorze musi być typu wzajemnie zgodne `T`, i Konstruktor tworzy kolekcję typu `Multiset<T>`.</span><span class="sxs-lookup"><span data-stu-id="f26c6-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="f26c6-117">Na przykład poniższe wyrażenie tworzy kolekcję liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="f26c6-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="f26c6-118">Pusty zestaw wielokrotny konstruktory nie są dozwolone, ponieważ nie można określić typ elementów.</span><span class="sxs-lookup"><span data-stu-id="f26c6-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="f26c6-119">Poniżej jest nieprawidłowa:</span><span class="sxs-lookup"><span data-stu-id="f26c6-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="f26c6-120">Aby uzyskać więcej informacji, zobacz [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f26c6-120">For more information, see [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="f26c6-121">Typ nazwany, konstruktory (NamedType inicjatory)</span><span class="sxs-lookup"><span data-stu-id="f26c6-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f26c6-122">Umożliwia konstruktorów typu (inicjatory), aby tworzyć wystąpienia nazwane typy złożone i typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="f26c6-122">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="f26c6-123">Na przykład poniższe wyrażenie tworzy wystąpienie `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="f26c6-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="f26c6-124">Poniższe wyrażenie tworzy wystąpienie typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="f26c6-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="f26c6-125">Poniższe wyrażenie tworzy wystąpienie zagnieżdżonego typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="f26c6-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="f26c6-126">Poniższe wyrażenie tworzy wystąpienie jednostki przy użyciu zagnieżdżonych typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="f26c6-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="f26c6-127">Poniższy przykład pokazuje, jak zainicjować właściwość typu złożonego do wartości null.</span><span class="sxs-lookup"><span data-stu-id="f26c6-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="f26c6-128">Argumenty konstruktora są rozpatrywane w tej samej kolejności, jak deklaracja atrybuty typu.</span><span class="sxs-lookup"><span data-stu-id="f26c6-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="f26c6-129">Aby uzyskać więcej informacji, zobacz [konstruktora typu o nazwie](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f26c6-129">For more information, see [Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f26c6-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f26c6-130">See also</span></span>

- [<span data-ttu-id="f26c6-131">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f26c6-131">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="f26c6-132">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f26c6-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="f26c6-133">System typów</span><span class="sxs-lookup"><span data-stu-id="f26c6-133">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
