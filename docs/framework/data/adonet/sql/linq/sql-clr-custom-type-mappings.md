---
title: Mapowanie niestandardowego typu SQL CLR
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: 8901998533ec14e733ea072dd1a69b465e596328
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781088"
---
# <a name="sql-clr-custom-type-mappings"></a>Mapowanie niestandardowego typu SQL CLR
Mapowanie typu między SQL Server i środowiska uruchomieniowego języka wspólnego (CLR) jest automatycznie określane przy użyciu narzędzia wiersza polecenia SQLMetal Object Relational Designer (Projektant O/R).  
  
 Gdy nie jest wykonywane żadne dostosowane mapowanie, te narzędzia przypisują domyślne mapowania typów zgodnie z opisem w [mapowaniu typu SQL-CLR](sql-clr-type-mapping.md). Jeśli chcesz pisać mapowania inaczej niż te wartości domyślne, musisz wykonać pewne dostosowania mapowań typów.  
  
 W przypadku dostosowywania mapowań typów Zalecanym podejściem jest wprowadzenie zmian w pliku DBML pośrednim. Następnie dostosowany plik DBML powinien być używany podczas tworzenia kodu i mapowania plików za pomocą projektanta SQLMetal lub O/R.  
  
 Po utworzeniu wystąpienia <xref:System.Data.Linq.DataContext> obiektu z plików <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> kodu i mapowania Metoda tworzy bazę danych w oparciu o określone mapowania typu. Jeśli w mapowaniu nie określono `type` żadnych atrybutów CLR, zostaną użyte domyślne mapowania typu.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>Dostosowywanie za pomocą projektanta SQLMetal lub O/R  
 Za pomocą narzędzia SQLMetal i projektanta O/R można automatycznie utworzyć model obiektów, który zawiera informacje o mapowaniu typu wewnątrz lub na zewnątrz pliku kodu. Ponieważ te pliki są zastępowane przez projektanta SQLMetal lub O/R, za każdym razem, gdy utworzysz mapowania, Zalecanym podejściem do określenia mapowań typów niestandardowych jest dostosowanie pliku DBML.  
  
 Aby dostosować mapowania typów za pomocą projektanta SQLMetal lub O/R, najpierw wygeneruj plik DBML. Następnie przed wygenerowaniem pliku kodu lub pliku mapowania zmodyfikuj plik DBML, aby zidentyfikować żądane mapowania typu. W przypadku SQLMetal należy ręcznie zmienić `Type` atrybuty i `DbType` w pliku DBML, aby umożliwić dostosowanie mapowania typu. Za pomocą projektanta O/R można wprowadzać zmiany w projektancie. Aby uzyskać więcej informacji o korzystaniu z projektanta O/R, zobacz [narzędzia LINQ to SQL w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
> Niektóre mapowania typów mogą spowodować przepełnienie lub wyjątki utraty danych podczas tłumaczenia do bazy danych lub z niej. Uważnie Przejrzyj macierz zachowania w czasie wykonywania mapowania typów w [mapowaniu typu SQL-CLR](sql-clr-type-mapping.md) przed wprowadzeniem jakichkolwiek dostosowań.  
  
 Aby dostosowanie mapowania typu zostało rozpoznane przez projektanta SQLMetal lub O/R, należy się upewnić, że te narzędzia są dostarczane ze ścieżką do niestandardowego pliku DBML podczas generowania pliku kodu lub zewnętrznego pliku mapowania. Chociaż nie jest to wymagane do dostosowywania mapowania typów, zaleca się, aby zawsze oddzielić informacje o mapowaniu typu z pliku kodu i wygenerować dodatkowy plik mapowania typu zewnętrznego. Wykonanie tej czynności pozostawi pewnej elastyczności, nie wymagając, aby plik kodu został ponownie skompilowany.  
  
## <a name="incorporating-database-changes"></a>Uwzględnianie zmian w bazie danych  
 Gdy baza danych ulegnie zmianie, należy zaktualizować plik DBML w celu odzwierciedlenia tych zmian. Jednym ze sposobów jest automatyczne utworzenie nowego pliku DBML, a następnie ponowne przeprowadzenie dostosowań mapowania typu. Alternatywnie można porównać różnice między nowym plikiem DBML i dostosowanym plikiem DBML i ręcznie zaktualizować niestandardowy plik DBML w celu odzwierciedlenia zmian w bazie danych.  
  
## <a name="see-also"></a>Zobacz także

- [Mapowania typów środowiska SQL-CLR](sql-clr-type-mapping.md)
- [Generowanie kodu w składniku LINQ to SQL](code-generation-in-linq-to-sql.md)
