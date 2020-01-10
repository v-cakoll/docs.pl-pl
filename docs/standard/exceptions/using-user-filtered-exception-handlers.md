---
title: Używanie obsługi wyjątków filtrowanych przez użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708456"
---
# <a name="using-user-filtered-exception-handlers"></a>Używanie obsługi wyjątków filtrowanych przez użytkownika

Obecnie Visual Basic obsługuje wyjątki filtrowane przez użytkownika. Programy obsługi wyjątków filtrowane przez użytkownika przechwytują i obsługują wyjątki na podstawie wymagań zdefiniowanych dla wyjątku. Te programy obsługi używają instrukcji **catch** z słowem kluczowym **when** .  
  
 Ta technika jest przydatna, gdy określony obiekt wyjątku odnosi się do wielu błędów. W takim przypadku obiekt ma zazwyczaj właściwość, która zawiera konkretny kod błędu skojarzony z błędem. Możesz użyć właściwości kod błędu w wyrażeniu, aby wybrać tylko konkretny błąd, który chcesz obsłużyć w tej klauzuli **catch** .  
  
 Poniższy przykład Visual Basic ilustruje instrukcję **catch/when** .  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 Wyrażenie filtrowanej przez użytkownika klauzuli nie jest w żaden sposób ograniczone. Jeśli wystąpi wyjątek podczas wykonywania wyrażenia filtrowanego przez użytkownika, ten wyjątek zostanie odrzucony i wyrażenie filtru jest uważane za szacowane na wartość false. W takim przypadku środowisko uruchomieniowe języka wspólnego kontynuuje wyszukiwanie programu obsługi dla bieżącego wyjątku.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Połączenie określonego wyjątku i klauzul filtrowanych przez użytkownika  
 Instrukcja catch może zawierać zarówno określony wyjątek, jak i przefiltrowane przez użytkownika klauzule. Środowisko uruchomieniowe najpierw sprawdza konkretny wyjątek. Jeśli konkretny wyjątek się powiedzie, środowisko uruchomieniowe wykonuje filtr użytkownika. Filtr generyczny może zawierać odwołanie do zmiennej zadeklarowanej w filtrze klas. Należy zauważyć, że nie można odwrócić kolejności dwóch klauzul filtru.  
  
 Poniższy przykład Visual Basic ilustruje konkretny wyjątek `ClassLoadException` w instrukcji **catch** , a także klauzulę filtrowana przez użytkownika przy użyciu słowa kluczowego **when** .  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
