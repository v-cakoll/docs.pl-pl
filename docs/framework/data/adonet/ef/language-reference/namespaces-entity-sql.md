---
title: Przestrzenie nazw (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4df0cc483e922e93a8038da02248b5fdcb2e3471
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="1952e-102">Przestrzenie nazw (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="1952e-102">Namespaces (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1952e-103">wprowadza przestrzenie nazw, aby uniknąć konfliktów nazw identyfikatorów globalnych, takich jak nazwy typu, zestawów jednostek, funkcje i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="1952e-103"> introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="1952e-104">Obsługa przestrzeni nazw w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest podobny do obsługi przestrzeni nazw w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1952e-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1952e-105">zawiera dwa rodzaje klauzuli USING: kwalifikowana przestrzeni nazw (gdy krótszą alias zostało określone dla przestrzeni nazw), a niekwalifikowanych nazw, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1952e-105"> provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="1952e-106">Zasady rozpoznawania nazw</span><span class="sxs-lookup"><span data-stu-id="1952e-106">Name Resolution Rules</span></span>  
 <span data-ttu-id="1952e-107">Jeśli identyfikator nie jest rozpoznawany w lokalnym zakresów [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje zlokalizować nazwy w zakresach globalnych (przestrzenie nazw).</span><span class="sxs-lookup"><span data-stu-id="1952e-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1952e-108">najpierw próbuje dopasować identyfikator (prefiks) z jednej z kwalifikowaną przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1952e-108"> first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="1952e-109">Jeśli istnieje dopasowanie, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje rozpoznać pozostałej części identyfikatora w określonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1952e-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="1952e-110">Jeśli nie znaleziono, zwracany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1952e-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="1952e-111">Następnie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wyszukiwanie wszystkich nazw niekwalifikowanych (określony w prologu) dla identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="1952e-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="1952e-112">Jeśli identyfikator może znajdować się w jednej przestrzeni nazw, zwracany jest tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="1952e-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="1952e-113">Jeśli więcej niż jeden obszar nazw ma dopasowania dla tego identyfikatora, zwracany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1952e-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="1952e-114">Jeśli dla identyfikatora, można zidentyfikować bez przestrzeni nazw [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przekazuje nazwę na następny zakres na zewnątrz ( <xref:System.Data.Common.DbCommand> lub <xref:System.Data.Common.DbConnection> obiektu), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1952e-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="1952e-115">Różnice z programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1952e-115">Differences from the .NET Framework</span></span>  
 <span data-ttu-id="1952e-116">W [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], można użyć częściowo kwalifikowanej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1952e-116">In the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1952e-117">Pozwala to.</span><span class="sxs-lookup"><span data-stu-id="1952e-117"> does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="1952e-118">Użycie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1952e-118">ADO.NET Usage</span></span>  
 <span data-ttu-id="1952e-119">Zapytania są wyrazić za pomocą ADO.NET <xref:System.Data.Common.DbCommand> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1952e-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="1952e-120"><xref:System.Data.Common.DbCommand>obiekty mogą być tworzone przez <xref:System.Data.Common.DbConnection> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1952e-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="1952e-121">Przestrzenie nazw można również określić jako część <xref:System.Data.Common.DbCommand> i <xref:System.Data.Common.DbConnection> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1952e-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="1952e-122">Jeśli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie można rozpoznać identyfikatora w samej kwerendzie zewnętrznych przestrzenie nazw są sondowany (na podstawie podobnymi zasadami).</span><span class="sxs-lookup"><span data-stu-id="1952e-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1952e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1952e-123">See Also</span></span>  
 [<span data-ttu-id="1952e-124">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1952e-124">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="1952e-125">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1952e-125">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
