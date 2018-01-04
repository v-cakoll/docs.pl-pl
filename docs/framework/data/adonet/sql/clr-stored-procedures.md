---
title: "Procedury składowane CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dfed0124c33c90427c9b888f5aa7bb191aea0400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clr-stored-procedures"></a>Procedury składowane CLR
Procedury składowane są procedury, których nie można używać w wyrażeniach skalarne. Mogą zwracać wyniki tabelaryczne i komunikaty do klienta, wywołania języka definicji danych (DDL) i instrukcji języka manipulacji danych oraz zwraca parametry wyjściowe.  
  
> [!NOTE]
>  Microsoft Visual Basic nie obsługuje parametrów wyjściowych w taki sam sposób, który wykonuje Microsoft Visual C#. Należy określić parametr jest przekazywany za pomocą odwołania i stosowanie \<Out() > atrybut do reprezentowania parametru wyjściowego, co przedstawiono poniżej:  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.  
  
 **SQL Server — książki Online**  
  
1.  [Procedury składowane CLR](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
