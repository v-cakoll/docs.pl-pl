---
title: "Parametry połączenia w ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6737b451a0ccb42dfb83dda487e351a9fafde398
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="connection-strings-in-adonet"></a>Parametry połączenia w ADO.NET
.NET Framework 2.0 wprowadzono nowe funkcje do pracy z parametrów połączenia, w tym wprowadzenia nowych słów kluczowych do klasy konstruktora ciąg połączenia, które ułatwiają tworzenie prawidłowe połączenie ciągów w czasie wykonywania.  
  
 Parametry połączenia zawierają informacje inicjowania jest przekazywana jako parametr z dostawcy danych do źródła danych. Składnia jest zależna od dostawcy danych, a podczas próby otwarcia połączenia jest przeanalizować parametrów połączenia. Błędy składniowe wygenerować wyjątek czasu wykonywania, ale inne błędy występują tylko wtedy, gdy źródło danych otrzymuje informacje o połączeniu. Po sprawdzeniu poprawności źródła danych dotyczy opcje określone w parametrach połączenia i otwarcie połączenia.  
  
 Format ciągu połączenia jest rozdzielaną średnikami listę par klucz/wartość parametru:  
  
 `keyword1=value; keyword2=value;`  
  
 Słowa kluczowe nie jest uwzględniana wielkość liter i spacji między pary klucz wartość są ignorowane. Jednak wartości może być uwzględniana wielkość liter, w zależności od źródła danych. Wszelkie wartości zawierające średnika, pojedynczy cudzysłów lub podwójny cudzysłów musi być ujęta w znaki podwójnego cudzysłowu.  
  
 Składnia ciągu połączenia prawidłowy zależy od dostawcy i powstał całościowo wcześniejszych interfejsy API, takich jak ODBC. .NET Framework Data Provider for SQL Server (SqlClient) zawiera wiele elementów z starsze składnię i jest zazwyczaj bardziej elastyczne z typowych składnia ciągu połączenia. Są często jednakowo prawidłowe synonimy dla elementów składnia ciągu połączenia, ale niektóre składni i błędów pisowni mogą powodować problemy. Na przykład "`Integrated Security=true`" jest nieprawidłowa, podczas gdy "`IntegratedSecurity=true`" powoduje, że wystąpił błąd. Ponadto parametry połączenia zbudowane w czasie wykonywania na podstawie danych wejściowych użytkownika niezweryfikowanych może prowadzić do ataków iniekcji ciągu, zagrażające zabezpieczeń w źródle danych.  
  
 Aby rozwiązać te problemy, ADO.NET 2.0 wprowadzono nowe konstruktorów ciągu połączenia dla każdego dostawcy danych .NET Framework. Słowa kluczowe są widoczne jako właściwości włączenie składnia ciągu połączenia do sprawdzenia poprawności przed przesłaniem do źródła danych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 Pokazuje, jak używać `ConnectionStringBuilder` klasy, aby utworzyć prawidłowe połączenie ciągi w czasie wykonywania.  
  
 [Parametry połączenia i pliki konfiguracji](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 Przedstawiono sposób przechowywania i pobierania parametrów połączenia w plikach konfiguracji.  
  
 [Składnia parametrów połączenia](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 Opisuje sposób konfigurowania parametrów połączeń specyficznych dla dostawcy dla `SqlClient`, `OracleClient`, `OleDb`, i `Odbc`.  
  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 Prezentuje techniki chroniące informacje używane do połączenia ze źródłem danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawiązywanie połączenia ze źródłem danych](/cpp/data/odbc/connecting-to-a-data-source)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
