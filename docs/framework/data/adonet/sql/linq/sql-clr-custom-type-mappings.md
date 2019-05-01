---
title: Mapowanie niestandardowego typu SQL CLR
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: bc92d54cad6a977268ef3f000c684d5f195a933d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037053"
---
# <a name="sql-clr-custom-type-mappings"></a>Mapowanie niestandardowego typu SQL CLR
Typ mapowania między programu SQL Server i środowisko uruchomieniowe języka wspólnego (CLR) automatycznie jest określona, korzystając z narzędzia wiersza polecenia SQLMetal Object Relational Designer (O/R Designer).  
  
 Podczas wykonywania dostosowane mapowania tych narzędzi przypisać domyślne mapowanie typu zgodnie z opisem w [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md). Na typ mapowania inaczej niż te ustawienia domyślne, należy wykonać pewne dostosowania mapowania typów.  
  
 Podczas dostosowywania mapowania typów, zalecanym podejściem jest aby wprowadzić zmiany w pliku DBML pośrednie. Następnie dostosowanego pliku DBML powinna służyć podczas tworzenia możesz kodu i mapowania plików za pomocą SQLMetal lub O/R Designer.  
  
 Gdy tworzenia wystąpienia <xref:System.Data.Linq.DataContext> obiektu z kodu i mapowania plików <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda tworzy bazę danych w oparciu mapowania typów, które są określone. Jeśli nie ma żadnych CLR `type` atrybuty określone w mapowaniach, będą używane domyślne mapowania typu.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>Dostosowywanie za pomocą SQLMetal lub Relational Designer  
 Program SQLMetal i O/R Designer może automatycznie tworzyć model obiektu, który zawiera mapowania informacje o typie wewnątrz lub na zewnątrz pliku kodu. Ponieważ te pliki są zastępowane przez program SQLMetal lub O/R Designer, zawsze możesz ponownie utworzyć mapowania, zalecane podejście do określania mapowanie niestandardowego typu jest dostosowywanie za pomocą pliku DBML.  
  
 Aby dostosować mapowanie typu SQLMetal lub O/R Designer, należy najpierw wygenerować za pomocą pliku DBML. Przed wygenerowaniem plik kodu lub pliku mapowania, zmodyfikowanie pliku DBML, aby zidentyfikować mapowania żądanego typu. Za pomocą SQLMetal, należy ręcznie zmienić `Type` i `DbType` atrybutów w dostosowania mapowania typu za pomocą pliku DBML. Za pomocą Projektanta obiektów relacyjnych można wprowadzić zmiany w projektancie. Aby uzyskać więcej informacji na temat za pomocą Projektanta obiektów relacyjnych, zobacz [LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
>  Niektóre mapowania typu może spowodować wyjątki utraty danych lub przepełnienie podczas tłumaczenia do lub z bazy danych. Dokładnie przejrzyj macierzy zachowanie mapowanie typu wykonawcze w [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) przed wykonaniem wszelkich dostosowań.  
  
 Mapowanie typu dostosowania zostały rozpoznane przez program SQLMetal lub O/R Designer, należy upewnić się, że te narzędzia są dostarczane ze ścieżką do niestandardowego pliku DBML podczas generowania pliku kodu lub pliku mapowania zewnętrznych. Chociaż nie jest to wymagane do dostosowywania mapowania typu, zalecane jest zawsze rozdzielić dane mapowania typu z pliku kodu i wygenerować dodatkowe typ zewnętrzny plik mapowania. To spowoduje, że pewną elastyczność, nie wymagając rekompilować pliku kodu.  
  
## <a name="incorporating-database-changes"></a>Dołączanie zmian w bazie danych  
 Po zmianie bazy danych, należy zaktualizować pliku DBML, aby odzwierciedlać wprowadzone zmiany. Jednym ze sposobów, aby zrobić to automatyczne tworzenie nowego pliku DBML, a następnie ponownie wykonaj dostosowania mapowania typu. Alternatywnie możesz porównać nowego pliku DBML i dostosowanego pliku DBML i zaktualizować niestandardowego pliku DBML ręcznie, aby odzwierciedlić zmianę w bazie danych.  
  
## <a name="see-also"></a>Zobacz także

- [Mapowania typów środowiska SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
