---
title: Zabezpieczenia w składniku LINQ to SQL
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: 7730419509cd0c3530813734a98f777ddf9d9f04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625682"
---
# <a name="security-in-linq-to-sql"></a>Zabezpieczenia w składniku LINQ to SQL
Zagrożenia bezpieczeństwa są zawsze wtedy, gdy połączenie z bazą danych. Mimo że LINQ to SQL mogą obejmować niektóre nowe sposoby pracy z danymi w programie SQL Server nie zapewnia dodatkowe zabezpieczenia jakichkolwiek mechanizmów środowiska użytkownika.  
  
## <a name="access-control-and-authentication"></a>Kontrola dostępu i uwierzytelniania  
 LINQ do SQL nie ma swoje własne mechanizmy uwierzytelniania lub modelu użytkownika. Korzystanie z zabezpieczeń serwera SQL do kontrolowania dostępu do bazy danych, tabele bazy danych, widoków i procedur składowanych, które są mapowane do modelu obiektu. Minimalny wymagany udostępnienia użytkownikom i wymagane silne hasła do uwierzytelniania użytkowników.  
  
## <a name="mapping-and-schema-information"></a>Mapowanie i informacji o schemacie  
 SQL-CLR typu mapowania i bazy danych informacji o schemacie w modelu obiektu lub pliku mapowania zewnętrznych jest dostępna dla wszystkich mających dostęp do tych plików w systemie plików. Przyjęto założenie, że informacje o schemacie będzie dostępny dla wszystkich, kto może uzyskiwać dostęp do modelu obiektów lub pliku mapowania zewnętrznych. Aby uniemożliwić szersze dostęp do informacji o schemacie, użyj mechanizmów zabezpieczeń pliku do zabezpieczania plików źródłowych i mapowania plików.  
  
## <a name="connection-strings"></a>Parametry połączenia  
 Za pomocą hasła w parametrach połączenia należy unikać zawsze, gdy jest to możliwe. Nie tylko parametry połączenia to zagrożenie bezpieczeństwa samodzielną, ale parametry połączenia mogą również dodawać w postaci zwykłego tekstu do modelu obiektów lub pliku mapowania zewnętrznych podczas przy użyciu wiersza polecenia narzędzia Object Relational Designer lub SQLMetal. (Jeśli jest on uwzględniony w parametrach połączenia), każda osoba mająca dostęp do modelu obiektów lub pliku mapowania zewnętrznych za pośrednictwem systemu plików można uzyskać hasło połączenia.  
  
 Aby zminimalizować ryzyko, używaj zintegrowanych zabezpieczeń umożliwiają zaufane połączenie z programem SQL Server. Za pomocą tej metody, nie masz do przechowywania hasła w parametrach połączenia. Aby uzyskać więcej informacji, zobacz [zabezpieczeń serwera SQL](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
 W przypadku braku zintegrowane zabezpieczenia hasła w postaci zwykłego tekstu, będzie potrzebna w parametrach połączenia. Najlepszym sposobem zabezpieczania parametry połączenia, rosnąco ryzyka, jest następujący:  
  
-   Użyj zintegrowanych zabezpieczeń.  
  
-   Zabezpiecz parametrów połączenia przy użyciu haseł i zminimalizować przekazywanie wokół parametry połączenia.  
  
-   Użyj <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> klasy zamiast parametrów połączenia, ponieważ ogranicza czas narażenia na zagrożenia. LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> klasy mogą być tworzone przy użyciu <xref:System.Data.SqlClient.SqlConnection>.  
  
-   Zminimalizować okresy istnienia i touch punktów dla wszystkich parametrów połączenia.  
  
## <a name="see-also"></a>Zobacz także
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Często zadawane pytania](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
