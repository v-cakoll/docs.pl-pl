---
title: Funkcje Canonical
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 8949735ba4712b721460335b4579f0a268c91aea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251272"
---
# <a name="canonical-functions"></a>Funkcje Canonical
W tej sekcji omówiono funkcje kanoniczne, które są obsługiwane przez wszystkich dostawców danych, i mogą być używane przez wszystkie technologie zapytań. Nie można rozszerzyć funkcji kanonicznych przez dostawcę.  
  
 Te funkcje kanoniczne zostaną przetłumaczone na odpowiednie funkcje źródła danych dla dostawcy. Pozwala to na wywołania funkcji wyrażone w typowym formacie między źródłami danych.  
  
 Ponieważ te funkcje kanoniczne są niezależne od źródeł danych, argument i zwracane typy funkcji kanonicznych są zdefiniowane w kategoriach typów w modelu koncepcyjnym. Jednak niektóre źródła danych mogą nie obsługiwać wszystkich typów w modelu koncepcyjnym.  
  
 Jeśli w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytaniu są używane funkcje kanoniczne, odpowiednia funkcja zostanie wywołana w źródle danych.  
  
 Wszystkie funkcje kanoniczne mają zarówno zachowanie danych wejściowych, jak i jawne określone warunki błędu. Dostawcy sklepu powinni przestrzegać tego zachowania, ale [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nie wymuszają tego zachowania.  
  
 W przypadku scenariuszy LINQ zapytania dotyczące programu [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] obejmują mapowanie metod CLR do metod w podstawowym źródle danych. Metody CLR mapują na funkcje kanoniczne, dzięki czemu określony zestaw metod będzie poprawnie mapowany, niezależnie od źródła danych.  
  
## <a name="canonical-functions-namespace"></a>Przestrzeń nazw funkcji kanonicznych  
 Przestrzeń nazw dla funkcji kanonicznej <xref:System.Data.Metadata.Edm>to. <xref:System.Data.Metadata.Edm> Przestrzeń nazw jest automatycznie dołączana do wszystkich zapytań. Jeśli jednak zostanie zaimportowana inna przestrzeń nazw, która zawiera funkcję o takiej samej nazwie jak funkcja kanoniczna ( <xref:System.Data.Metadata.Edm> w przestrzeni nazw), należy określić przestrzeń nazw.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje agregujące Canonical](aggregate-canonical-functions.md)  
 Omawia agregacje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcji w postaci kanonicznej.  
  
 [Funkcje matematyczne Canonical](math-canonical-functions.md)  
 Omawia funkcje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] matematyczne w postaci kanonicznej.  
  
 [Funkcje ciągów Canonical](string-canonical-functions.md)  
 Omawia funkcje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ciągów kanonicznych.  
  
 [Funkcji daty i godziny Canonical](date-and-time-canonical-functions.md)  
 Omawia funkcje kanoniczne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] daty i godziny.  
  
 [Funkcje bitowe Canonical](bitwise-canonical-functions.md)  
 Omawia bitowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje kanoniczne.  
  
 [Funkcje przestrzenne](spatial-functions.md)  
 Omawia funkcje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przestrzenne w postaci kanonicznej.  
  
 [Inne funkcje Canonical](other-canonical-functions.md)  
 Omawia funkcje niesklasyfikowane jako bitowe, daty/godziny, String, Math lub Aggregate.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Model koncepcyjny Canonical do mapowania funkcji serwera SQL](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [Funkcje zdefiniowane przez użytkownika](user-defined-functions-entity-sql.md)
