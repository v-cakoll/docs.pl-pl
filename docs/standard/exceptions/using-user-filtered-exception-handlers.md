---
title: Używanie obsługi wyjątków filtrowanych przez użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708456"
---
# <a name="using-user-filtered-exception-handlers"></a>Używanie obsługi wyjątków filtrowanych przez użytkownika

Obecnie program Visual Basic obsługuje wyjątki filtrowane przez użytkownika. Programy obsługi wyjątków filtrowane przez użytkownika przechwycają i obsługują wyjątki na podstawie wymagań zdefiniowanych dla wyjątku. Te programy obsługi używać **Catch** instrukcji z **When** słowa kluczowego.  
  
 Ta technika jest przydatna, gdy obiekt określonego wyjątku odpowiada wielu błędom. W takim przypadku obiekt zazwyczaj ma właściwość, która zawiera kod błędu określonego skojarzonego z błędem. Można użyć właściwości kodu błędu w wyrażeniu, aby wybrać tylko określony błąd, który ma być obsługiwany w tej **catch** klauzuli.  
  
 Poniższy przykład języka Visual Basic ilustruje **Catch/When** instrukcji.  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 Wyrażenie klauzuli filtrowane przez użytkownika nie jest w żaden sposób ograniczone. Jeśli wystąpi wyjątek podczas wykonywania wyrażenia filtrowanego przez użytkownika, ten wyjątek jest odrzucany, a wyrażenie filtru jest uważane za ocenione jako false. W takim przypadku czas uruchomieniowy języka wspólnego kontynuuje wyszukiwanie obsługi dla bieżącego wyjątku.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Łączenie wyjątku specyficznego i klauzul filtrowanych przez użytkowników  
 Catch Instrukcji może zawierać zarówno określonego wyjątku i klauzulfiltrowane przez użytkownika. W czasie wykonywania testów określonego wyjątku pierwszy. Jeśli określony wyjątek powiedzie się, środowisko uruchomieniowe wykonuje filtr użytkownika. Filtr ogólny może zawierać odwołanie do zmiennej zadeklarowanej w filtrze klasy. Należy zauważyć, że kolejność dwóch klauzul filtru nie można odwrócić.  
  
 W poniższym przykładzie języka `ClassLoadException` Visual Basic przedstawiono określony wyjątek w **Catch** instrukcji, a także klauzuli filtrowane przez użytkownika przy użyciu **When** słowa kluczowego.  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)
