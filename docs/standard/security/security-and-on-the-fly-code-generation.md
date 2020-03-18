---
title: Zabezpieczenia i generowanie kodu na bieżąco
description: Generowanie kodu w imieniu kodu mniejszego zaufania, który działa przy wyższym zaufaniu, jest problemem zabezpieczeń, szczególnie wtedy, gdy obiekt wywołujący może wpływać na generowanie kodu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 34ebda27a81ca29ebb27a721b77b735a12be882e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186801"
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpieczenia i generowanie kodu na bieżąco
Niektóre biblioteki działają przez generowanie kodu i uruchamianie go w celu wykonania niektórych operacji dla obiektu wywołującego. Podstawowym problemem jest generowanie kodu w imieniu kodu mniejszego zaufania i uruchamianie go z większym zaufaniem. Problem pogarsza się, gdy obiekt wywołujący może mieć wpływ na generowanie kodu, więc należy upewnić się, że generowany jest tylko kod, który uważasz za bezpieczny.  
  
 Musisz dokładnie wiedzieć, jaki kod generujesz przez cały czas. Oznacza to, że musisz mieć ścisłe kontrole wszelkich wartości, które można uzyskać od użytkownika, czy to ciągi dołączone do cudzysłowu (które powinny być unikane, aby nie mogły zawierać nieoczekiwanych elementów kodu), identyfikatory (które powinny być sprawdzane, aby sprawdzić, czy są prawidłowe identyfikatorów) lub czegokolwiek innego. Identyfikatory mogą być niebezpieczne, ponieważ skompilowany zestaw może być modyfikowany tak, aby jego identyfikatory zawierały dziwne znaki, które prawdopodobnie go złamią (chociaż rzadko jest to luka w zabezpieczeniach).  
  
 Zaleca się generowanie kodu z emitują odbicia, co często pomaga uniknąć wielu z tych problemów.  
  
 Podczas kompilowania kodu należy rozważyć, czy istnieje jakiś sposób, w jaki złośliwy program może go zmodyfikować. Czy istnieje małe okno czasu, w którym złośliwy kod może zmienić kod źródłowy na dysku przed kompilatorem odczytuje go lub przed załadowaniem kodu pliku dll? Jeśli tak, należy chronić katalog zawierający te pliki, przy użyciu listy kontroli dostępu w systemie plików, w stosownych przypadkach.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
