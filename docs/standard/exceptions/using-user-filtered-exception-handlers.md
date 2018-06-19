---
title: Używanie obsługi wyjątków filtrowanych przez użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e72f87bd4a33491df46576629971c60af4630ce3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571894"
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
