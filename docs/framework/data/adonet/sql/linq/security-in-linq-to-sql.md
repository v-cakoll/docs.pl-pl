---
title: Zabezpieczenia w składniku LINQ to SQL
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: f1ebf2f72fbfe3b27b9fbfd41f0dd65c70103620
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781185"
---
# <a name="security-in-linq-to-sql"></a>Zabezpieczenia w składniku LINQ to SQL
Zagrożenia bezpieczeństwa są zawsze obecne podczas łączenia się z bazą danych. Mimo że LINQ to SQL mogą zawierać nowe sposoby pracy z danymi w SQL Server, nie zapewnia żadnych dodatkowych mechanizmów zabezpieczeń.  
  
## <a name="access-control-and-authentication"></a>Access Control i uwierzytelnianie  
 LINQ to SQL nie ma własnego modelu użytkownika ani mechanizmów uwierzytelniania. Użyj zabezpieczeń SQL Server, aby kontrolować dostęp do bazy danych, tabel baz danych, widoków i procedur składowanych, które są mapowane na model obiektu. Przyznaj minimalny dostęp użytkownikom i wymagaj silnych haseł do uwierzytelniania użytkowników.  
  
## <a name="mapping-and-schema-information"></a>Mapowanie i informacje o schemacie  
 Mapowanie typu SQL-CLR i informacje o schemacie bazy danych w modelu obiektów lub zewnętrznym pliku mapowania są dostępne dla wszystkich z dostępem do tych plików w systemie plików. Załóżmy, że informacje o schemacie będą dostępne dla wszystkich osób, które mogą uzyskiwać dostęp do modelu obiektów lub zewnętrznego pliku mapowania. Aby zapobiec bardziej rozległemu dostępowi do informacji o schemacie, należy użyć mechanizmów zabezpieczeń plików do zabezpieczania plików źródłowych i plików mapowania.  
  
## <a name="connection-strings"></a>Parametry połączeń  
 Zawsze, gdy jest to możliwe, należy unikać używania haseł w ciągach połączenia. Nie tylko jest parametrami połączenia, które jest ryzykiem związanym z zabezpieczeniami, ale parametry połączenia mogą być również dodawane w postaci zwykłego tekstu do modelu obiektów lub zewnętrznego pliku mapowania przy użyciu narzędzia wiersza polecenia Object Relational Designer lub SQLMetal. Każda osoba mająca dostęp do modelu obiektów lub zewnętrznego pliku mapowania za pośrednictwem systemu plików może zobaczyć hasło połączenia (jeśli zostało dołączone do parametrów połączenia).  
  
 Aby zminimalizować takie ryzyko, należy używać zabezpieczeń zintegrowanych w celu nawiązania zaufanego połączenia z SQL Server. Korzystając z tej metody, nie trzeba przechowywać hasła w parametrach połączenia. Aby uzyskać więcej informacji, zobacz [SQL Server zabezpieczenia](../sql-server-security.md).  
  
 W przypadku braku zintegrowanego zabezpieczenia w parametrach połączenia będzie wymagana wartość hasła w postaci zwykłego tekstu. Najlepszym sposobem na zabezpieczenie parametrów połączenia w celu zwiększenia kolejności ryzyka jest następujące:  
  
- Używaj zintegrowanych zabezpieczeń.  
  
- Zabezpieczanie parametrów połączenia z hasłami i minimalizowanie przekazywania między ciągami połączeń.  
  
- <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> Użyj klasy zamiast parametrów połączenia, ponieważ ogranicza ona czas ekspozycji. Klasy LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> można utworzyć <xref:System.Data.SqlClient.SqlConnection>przy użyciu.  
  
- Zminimalizuj okresy istnienia i punkty dotykowe dla wszystkich parametrów połączenia.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
- [Często zadawane pytania](frequently-asked-questions.md)
