---
title: Parametry połączenia w ADO.NET
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: b4e057cab4c562fc51893631c35d66409e1c3731
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617046"
---
# <a name="connection-strings-in-adonet"></a>Parametry połączenia w ADO.NET
.NET Framework 2.0 wprowadzono nowe możliwości do pracy z parametrów połączenia, łącznie z wprowadzeniem nowych słów kluczowych do klasy konstruktora parametrów połączenia, które ułatwiają tworzenie ciągów prawidłowego połączenia w czasie wykonywania.  
  
 Parametry połączenia zawierają informacje inicjowania, który jest przekazywany jako parametr od dostawcy danych do źródła danych. Składnia jest zależna od dostawcy danych, a ciąg połączenia jest analizowany podczas próby otwarcia połączenia. Błędy składniowe generowania wyjątków czasu wykonywania, ale inne błędy występują tylko wtedy, gdy źródło danych otrzymuje informacje o połączeniu. Po zweryfikowaniu źródła danych dotyczy opcje określone w parametrach połączenia i otwarcie połączenia.  
  
 Format ciągu połączenia jest rozdzielaną średnikami listę par klucz/wartość do parametru:  
  
 `keyword1=value; keyword2=value;`  
  
 Słowa kluczowe nie jest uwzględniana wielkość liter i spacje między pary klucz/wartość są ignorowane. Jednakże wartości mogą być uwzględniana wielkość liter, w zależności od źródła danych. Wszelkie wartości zawierające je średnikiem, znaki cudzysłowu pojedynczego lub podwójnego cudzysłowu muszą być ujęte w podwójny cudzysłów.  
  
 Składnia ciągu prawidłowe połączenie jest zależna od dostawcy i został przekształcony w ciągu lat, za pomocą starszych interfejsów API, takich jak ODBC. .NET Framework Data Provider for SQL Server (SqlClient) zawiera wiele elementów z starsza składnia i jest zazwyczaj bardziej elastyczne, przy użyciu typowej składni ciągu połączenia. Są często równie prawidłowe synonimy dla elementów składnia ciągu połączenia, ale niektóre składni oraz błędy pisowni może powodować problemy. Na przykład "`Integrated Security=true`" jest prawidłowy, natomiast "`IntegratedSecurity=true`" powoduje wystąpienie błędu. Ponadto parametry połączenia, tworzony w czasie wykonywania z danych wejściowych użytkownika niezweryfikowanych mogą powodować atakami polegającymi na iniekcji ciągu, bezpiecznemu zabezpieczeń w źródle danych.  
  
 Aby rozwiązać te problemy, ADO.NET w wersji 2.0 wprowadzono nowe Konstruktorzy parametrów połączeń dla każdego dostawcy danych .NET Framework. Słowa kluczowe są widoczne jako właściwości, umożliwiając składnia ciągu połączenia zostać uwierzytelnionym przed przesłaniem do źródła danych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 Pokazuje sposób użycia `ConnectionStringBuilder` klas do utworzenia prawidłowego połączenia ciągów w czasie wykonywania.  
  
 [Parametry połączenia i pliki konfiguracji](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 Pokazuje, jak przechowywać i pobierać parametry połączenia w plikach konfiguracji.  
  
 [Składnia parametrów połączenia](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 W tym artykule opisano jak skonfigurować parametry połączenia specyficzne dla dostawcy na potrzeby `SqlClient`, `OracleClient`, `OleDb`, i `Odbc`.  
  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 Pokazuje technik ochrony informacje używane do połączenia ze źródłem danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawiązywanie połączenia ze źródłem danych](/cpp/data/odbc/connecting-to-a-data-source)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
