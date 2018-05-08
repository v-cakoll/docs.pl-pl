---
title: Zabezpieczenia i generowanie kodu na bieżąco
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2cfc93e1c8d3d9e878d96de164b0d646e62c0998
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpieczenia i generowanie kodu na bieżąco
Działanie niektórych bibliotek, generowanie kodu i uruchomienie jej do wykonania niektórych operacji do obiektu wywołującego. Podstawowy problem jest generowanie kodu w imieniu mniejszym zaufania kodu i uruchomić je na wyższe zaufania. Problem worsens podczas wywołującego może mieć wpływ na generowanie kodu, dlatego należy upewnić się, że generowane jest tylko kod, który należy wziąć pod uwagę bezpieczne.  
  
 Musisz wiedzieć, dokładnie jaki kod jest generowany przez cały czas. Oznacza to, że muszą mieć ścisłej kontroli na wartości, które można uzyskać od użytkownika, którymi są ujęte w cudzysłów ciągi (które należy zastosować ucieczkę, nie mogą zawierać elementy nieoczekiwany kod), identyfikatorów (które powinny być sprawdzane, aby sprawdzić, czy są one prawidłowe identyfikatory) lub innych elementów. Identyfikatory może być niebezpieczne, ponieważ może być modyfikowany skompilowanym zestawie, dzięki czemu jego identyfikatory zawierać dziwne znaki, które będą prawdopodobnie Podziel je (mimo że jest to rzadko luki w zabezpieczeniach).  
  
 Zaleca się, że generowanie kodu przy użyciu odbicia emisji, który często pomaga uniknąć wiele z tych problemów.  
  
 Podczas kompilowania kodu rozważ, czy istnieje inny sposób złośliwych programów można go zmodyfikować. Czy istnieje krótkim przedziale czasu, w którym złośliwego kodu, można zmienić kod źródłowy na dysku przed kompilator odczytuje go lub przed kod ładuje plik dll? Jeśli tak, należy chronić katalog zawierający pliki, za pomocą listy kontroli dostępu w systemie plików, zależnie od potrzeb.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
