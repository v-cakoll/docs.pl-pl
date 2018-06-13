---
title: Mapowanie niestandardowego typu SQL CLR
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: ebbbaf4b90c289d4230bada210d3031a87ac4f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359666"
---
# <a name="sql-clr-custom-type-mappings"></a>Mapowanie niestandardowego typu SQL CLR
Automatycznie określono typ mapowania między serwerem SQL i środowisko uruchomieniowe języka wspólnego (CLR), korzystając z narzędzia wiersza polecenia SQLMetal Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych).  
  
 Po wykonaniu dostosowane mapowania tych narzędzi przypisać domyślne mapowanie typu zgodnie z opisem w [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md). Na typ mapowania inaczej niż te wartości domyślne, należy wykonać pewne dostosowania mapowania typu.  
  
 W przypadku dostosowywania mapowania typów, zalecanym podejściem jest będzie wprowadzenie zmian w pliku DBML pośredniczące. Następnie dostosowanego pliku DBML powinna być używana podczas tworzenia możesz kodu i mapowania plików SQLMetal lub projektanta obiektów relacyjnych.  
  
 Po można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> obiektu z kodu i pliki mapowania <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda tworzy bazę danych oparte na mapowania typów, które zostały określone. Jeśli nie ma żadnych CLR `type` atrybuty określone w mapowaniu, będą używane domyślne mapowania typu.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>Dostosowywanie SQLMetal lub projektanta obiektów relacyjnych  
 SQLMetal i projektanta obiektów relacyjnych można automatycznie utworzyć model obiektu, który zawiera typ informacje dotyczące mapowania lub poza nim pliku kodu. Ponieważ te pliki zostaną zastąpione przez SQLMetal lub projektanta obiektów relacyjnych, zawsze możesz ponownie utworzyć mapowania, zalecane podejście do określania typu niestandardowego mapowania jest dostosować za pomocą pliku DBML.  
  
 Aby dostosować mapowania typu SQLMetal lub projektanta obiektów relacyjnych, najpierw należy wygenerować za pomocą pliku DBML. Następnie przed wygenerowaniem kodu lub pliku mapowania, należy zmodyfikować pliku DBML, aby zidentyfikować mapowania żądanego typu. Dzięki SQLMetal, trzeba ręcznie zmienić `Type` i `DbType` atrybutów w pliku DBML, aby Twoje typu dostosowania mapowania. Za pomocą Projektanta obiektów relacyjnych możesz wprowadzić zmiany w projektancie. Aby uzyskać więcej informacji na temat za pomocą Projektanta obiektów relacyjnych, zobacz [składnika LINQ to SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
>  Niektóre mapowania typów może skutkować wyjątki utrata danych lub przepełnienie podczas tłumaczenia do lub z bazy danych. Uważnie przejrzyj macierz zachowanie mapowanie typu czasu wykonywania w [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) przed wprowadzeniem jakichkolwiek dostosowań.  
  
 Mapowanie typu dostosowania rozpoznaje SQLMetal lub projektanta obiektów relacyjnych, należy upewnij się, że te narzędzia są dostarczane ze ścieżką do niestandardowego pliku DBML podczas generowania pliku kodu lub pliku mapowania zewnętrznych. Nie są wymagane do dostosowania mapowanie typu, zalecane jest zawsze oddzielnych z informacjami dotyczącymi mapowania typu z pliku kodu i Generuj plik mapowania dodatkowe typu zewnętrznego. W ten sposób spowoduje pozostawienie elastycznością nie wymaga, aby ponownie skompilowana pliku kodu.  
  
## <a name="incorporating-database-changes"></a>Dołączanie zmian w bazie danych  
 Podczas zmiany bazy danych, musisz zaktualizować pliku DBML w celu odzwierciedlenia tych zmian. Aby wykonać to do automatycznego tworzenia nowego pliku DBML, a następnie wykonaj ponownie Twoje dostosowania mapowania typu. Alternatywnie możesz porównać nowego pliku DBML i dostosowanego pliku DBML i aktualizacja Twojego niestandardowego pliku DBML ręcznie, aby odzwierciedlić zmianę w bazie danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowania typów środowiska SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
