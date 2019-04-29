---
title: Funkcje Canonical
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 380c1dbcf86d8bbb844c2b226697d72d00c3e81a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606091"
---
# <a name="canonical-functions"></a>Funkcje Canonical
W tej sekcji omówiono funkcje canonical, które są obsługiwane przez wszystkich dostawców danych i może być używany przez wszystkie technologie zapytań. Nie można rozszerzyć funkcje Canonical przez dostawcę.  
  
 Te funkcje canonical będzie tłumaczona na odpowiednie funkcje źródła danych dla dostawcy. Dzięki temu wywołania funkcji wyrażony w postaci typowych źródeł danych.  
  
 Ponieważ te funkcje canonical są niezależne od źródeł danych, argumentów i typy kanonicznej funkcji są definiowane pod względem typów w modelu koncepcyjnym. Jednak niektóre źródła danych mogą nie obsługiwać wszystkich typów w modelu koncepcyjnym.  
  
 Gdy funkcje canonical są używane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania, odpowiednią funkcję zostanie wywołana w źródle danych.  
  
 Wszystkie funkcje canonical mają zachowanie danych wejściowych o wartości null i warunki błędów, które zostały jawnie określone. Dostawców Store powinny być zgodne z tego zachowania, ale [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nie wymusza to zachowanie.  
  
 W przypadku scenariuszy LINQ zapytania względem [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] obejmują metody CLR mapowania do metod w źródle danych. Mapę metodach CLR, aby funkcje canonical tak, aby zestaw konkretnych metod poprawnie zmapuje, niezależnie od tego źródła danych.  
  
## <a name="canonical-functions-namespace"></a>Namespace funkcje Canonical  
 Przestrzeń nazw dla kanonicznej funkcji jest <xref:System.Data.Metadata.Edm>. <xref:System.Data.Metadata.Edm> Przestrzeni nazw jest automatycznie uwzględniany we wszystkich zapytań. Jednak jeśli innej przestrzeni nazw jest importowany zawierający funkcję z taką samą nazwę jak kanonicznej funkcji (w <xref:System.Data.Metadata.Edm> przestrzeni nazw), należy określić przestrzeń nazw.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje agregujące Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 W tym artykule omówiono agregacji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical.  
  
 [Funkcje matematyczne Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 W tym artykule omówiono matematyczne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical.  
  
 [Funkcje ciągów Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 W tym artykule omówiono ciągu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical.  
  
 [Funkcji daty i godziny Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 W tym artykule omówiono daty i godziny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical.  
  
 [Funkcje bitowe Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 W tym artykule omówiono bitowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical.  
  
 [Funkcje przestrzenne](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 W tym artykule omówiono przestrzenne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical.  
  
 [Inne funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 W tym artykule omówiono funkcje nie sklasyfikowane jako bitowe, daty/godziny, ciąg, matematyczne lub agregacji.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Model koncepcyjny Canonical do mapowania funkcji serwera SQL](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [Funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
