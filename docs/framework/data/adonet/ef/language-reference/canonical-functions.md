---
title: Canonical funkcji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: da48efc110669c170fc409e22cb8402f471b22e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="canonical-functions"></a>Canonical funkcji
W tej sekcji omówiono kanonicznej funkcji, które są obsługiwane przez wszystkich dostawców danych i mogą być używane przez wszystkie technologie wykonywanie zapytania. Canonical funkcji nie może zostać rozszerzony przez dostawcę.  
  
 Te funkcje canonical będzie translacji odpowiedniej funkcji źródła danych dla dostawcy. Dzięki temu wywołania funkcji wyrażony w postaci typowych między źródłami danych.  
  
 Ponieważ te funkcje canonical są niezależne od źródeł danych, argumentów i zwracane typy funkcji kanonicznej są definiowane pod względem typów w modelu koncepcyjnym. Jednak niektóre źródła danych mogą nie obsługiwać wszystkie typy w modelu koncepcyjnym.  
  
 Gdy kanonicznej funkcji są używane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania, odpowiednią funkcję zostanie wywołana w źródle danych.  
  
 Wszystkie funkcje canonical mają zarówno zachowanie dane wejściowe na wartość null, jak i warunki błędów jawnie określony. Dostawców magazynu muszą być zgodne z tego zachowania, ale [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nie wymusza to zachowanie.  
  
 W przypadku scenariuszy LINQ zapytania względem [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] obejmują metody CLR mapowania do metod w źródle danych. Mapy metody CLR kanonicznej funkcji, dzięki czemu określonego zestawu metod poprawnie przypisze, niezależnie od tego źródła danych.  
  
## <a name="canonical-functions-namespace"></a>Canonical funkcje Namespace  
 Przestrzeń nazw dla funkcji kanonicznej jest <xref:System.Data.Metadata.Edm>. <xref:System.Data.Metadata.Edm> Przestrzeni nazw jest automatycznie uwzględniany we wszystkich zapytań. Jednak jeśli innej przestrzeni nazw jest importowany zawierający funkcję z taką samą nazwę jak kanonicznej funkcji (w <xref:System.Data.Metadata.Edm> przestrzeni nazw), należy określić przestrzeń nazw.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje agregujące Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 W tym artykule omówiono agregacji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.  
  
 [Funkcje matematyczne Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 W tym artykule omówiono matematyczne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.  
  
 [Funkcje ciągów Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 W tym artykule omówiono ciąg [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.  
  
 [Funkcji daty i godziny Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 W tym artykule omówiono Data i godzina [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.  
  
 [Funkcje bitowe Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 W tym artykule omówiono bitowo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.  
  
 [Funkcje przestrzenne](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 W tym artykule omówiono przestrzennym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.  
  
 [Inne funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 W tym artykule omówiono funkcje nie są sklasyfikowane jako bitowe, daty/godziny, ciąg, matematyczne lub agregacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Model koncepcyjny Canonical do mapowania funkcji serwera SQL](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [Funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
