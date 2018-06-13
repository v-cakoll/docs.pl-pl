---
title: Zabezpieczenia w składniku LINQ to SQL
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: b2c7de75295722da643d64ff22bc769e0633629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364398"
---
# <a name="security-in-linq-to-sql"></a>Zabezpieczenia w składniku LINQ to SQL
Zagrożenia bezpieczeństwa są zawsze wtedy, gdy połączenie z bazą danych. Chociaż LINQ do SQL może zawierać niektóre nowe sposoby pracy z danymi w programie SQL Server, nie ma żadnych dodatkowe mechanizmy zabezpieczeń.  
  
## <a name="access-control-and-authentication"></a>Kontrola dostępu i uwierzytelniania  
 LINQ do SQL nie ma własne mechanizmy modelu lub uwierzytelniania użytkownika. Użyj zabezpieczeń serwera SQL, aby kontrolować dostęp do bazy danych, tabele bazy danych, widoków i procedur składowanych, które są mapowane do modelu obiektu. Minimalny wymagany udostępnić użytkownikom i wymagają silnego hasła do uwierzytelnienia użytkownika.  
  
## <a name="mapping-and-schema-information"></a>Mapowania i informacje o schemacie  
 SQL CLR typu bazy danych schematu informacji dotyczących mapowania i w modelu obiektów lub zewnętrznego mapowania pliku jest dostępna dla wszystkich dostęp do tych plików w systemie plików. Załóżmy, że informacje o schemacie będą dostępne dla wszystkich, kto ma dostęp do modelu obiektu lub plik mapowania zewnętrznych. Aby zapobiec szerszego dostępu do informacji o schemacie, umożliwia ochronę plików źródłowych i mapowania plików mechanizmy zabezpieczeń pliku.  
  
## <a name="connection-strings"></a>Parametry połączenia  
 Za pomocą hasła w parametrach połączenia należy unikać zawsze, gdy jest to możliwe. Nie jest ciąg połączenia w sobie stanowić ryzyko dla bezpieczeństwa tylko parametry połączenia mogą również dodać w postaci zwykłego tekstu w modelu obiektu lub plik mapowania zewnętrznych przy użyciu narzędzia Projektant obiektów relacyjnych lub SQLMetal wiersza polecenia. Każda osoba mająca dostęp do modelu obiektu lub plik mapowania zewnętrznej za pośrednictwem systemu plików można zobacz hasło połączenia (jeśli znajduje się on w parametrach połączenia).  
  
 Aby zminimalizować ryzyko, Użyj zintegrowanych zabezpieczeń, aby wprowadzić zaufanego połączenia z programem SQL Server. Przy użyciu tej metody, nie trzeba przechowywać hasła w parametrach połączenia. Aby uzyskać więcej informacji, zobacz [zabezpieczeń serwera SQL](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
 W przypadku braku zintegrowane zabezpieczenia hasła w postaci zwykłego tekstu będą potrzebne w parametrach połączenia. Najlepszy sposób, aby pomóc w zabezpieczeniu parametrów połączenia, rosnąco ryzyka, jest następujący:  
  
-   Użyj zintegrowanych zabezpieczeń.  
  
-   Zabezpieczenie parametry połączenia przy użyciu haseł i zminimalizować przekazywanie ciągi połączenia.  
  
-   Użyj <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> klasy zamiast ciągu połączenia, ponieważ ogranicza czas trwania zagrożeń. LINQ do SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> klasy można wdrożyć przy użyciu <xref:System.Data.SqlClient.SqlConnection>.  
  
-   Zminimalizować okresy istnienia i touch punkty dla wszystkich ciągów połączenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Często zadawane pytania](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
