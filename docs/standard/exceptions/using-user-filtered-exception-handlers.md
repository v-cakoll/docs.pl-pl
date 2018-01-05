---
title: "Używanie obsługi wyjątków filtrowanych przez użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1f5eb735262ee7ef69e200b1249c7b1c4a1e2ac2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="using-user-filtered-exception-handlers"></a>Używanie obsługi wyjątków filtrowanych przez użytkownika
Visual Basic obsługuje obecnie wyjątki filtrowane przez użytkownika. Programy obsługi wyjątków filtrowanych przez użytkownika wychwycić i obsłużyć wyjątków na podstawie wymagań zdefiniowanych dla wyjątku. Użyj tych programów obsługi **Catch** instrukcji z **podczas** — słowo kluczowe.  
  
 Ta technika jest przydatna, gdy obiekt określonego wyjątku odpowiada wiele błędów. W takim przypadku obiekt zwykle ma właściwość, która zawiera kod błędu skojarzony z powodu błędu. Aby wybrać tylko określony błąd mają być obsługiwane w tym służy właściwości kodu błędu w wyrażeniu **Catch** klauzuli.  
  
 Przedstawiono w poniższym przykładzie w języku Visual Basic **wystąpienia Catch** instrukcji.  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 Wyrażenie klauzuli filtrowane przez użytkownika nie jest ograniczona w dowolny sposób. Jeśli wystąpi wyjątek podczas wykonywania wyrażenia filtrowane przez użytkownika, ten wyjątek jest odrzucany i wyrażenie filtru jest uznawany za obliczenia ma wartość false. W takim przypadku środowisko uruchomieniowe języka wspólnego kontynuuje wyszukiwanie programu obsługi dla bieżącego wyjątku.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Łączenie określonego wyjątku i klauzule filtrowane przez użytkownika  
 Instrukcji catch może zawierać zarówno określony wyjątek, jak i klauzule filtrowane przez użytkownika. Środowisko uruchomieniowe testów najpierw określony wyjątek. Jeśli określony wyjątek zakończy się powodzeniem, środowisko uruchomieniowe wykonuje filtr użytkowników. Ogólne filtru może zawierać odwołanie do zmiennej zadeklarowanej w filtrze klasy. Należy pamiętać, kolejność klauzul dwóch filtru nie można cofnąć.  
  
 W poniższym przykładzie w języku Visual Basic zawiera określony wyjątek `ClassLoadException` w **Catch** instrukcji, a także za pomocą klauzuli filtrowane przez użytkownika **podczas** — słowo kluczowe.  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a>Zobacz też
[Wyjątki](index.md)
