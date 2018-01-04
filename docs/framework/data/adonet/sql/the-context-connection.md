---
title: "Połączenie kontekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f3bb732644bf9373d847eb14b63e69a756cb3ac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="the-context-connection"></a>Połączenie kontekstu
Problem dostępu do danych wewnętrznych jest dość typowy scenariusz. Oznacza to, że mają dostęp do tego samego serwera Twoje środowisko uruchomieniowe języka wspólnego (CLR) procedury składowanej lub funkcji jest wykonywany. Jedną z opcji jest utworzenie połączenia za pomocą <xref:System.Data.SqlClient.SqlConnection>, określ ciąg połączenia, który wskazuje na serwerze lokalnym i otwarcia połączenia. Wymaga to podania poświadczeń do logowania. Połączenie jest w sesji innej bazy danych niż procedura składowana lub funkcja, może mieć różne `SET` opcje, znajduje się w osobnej transakcji, nie zobaczą tabele tymczasowe, i tak dalej. Jeśli sieci zarządzanej procedury składowanej lub funkcji kod jest wykonywany w procesie programu SQL Server, to, że ktoś połączona z tym serwerem, a instrukcja SQL, można go wywołać. Prawdopodobnie potrzebna będzie procedura składowana lub funkcja do wykonania w kontekście tego połączenia, wraz z jego transakcji `SET` opcje i tak dalej. Jest to połączenie kontekstu.  
  
 Połączenie kontekstu umożliwia wykonanie instrukcji języka Transact-SQL w kontekście tego samego kodu wywołano w pierwszej kolejności. Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.  
  
 **SQL Server — książki Online**  
  
1.  [Połączenie kontekstu](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
