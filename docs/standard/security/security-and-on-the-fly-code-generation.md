---
title: "Zabezpieczenia i generowanie kodu na bieżąco"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c6bb895979fb44616349505a07591f9ced9fedac
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpieczenia i generowanie kodu na bieżąco
Działanie niektórych bibliotek, generowanie kodu i uruchomienie jej do wykonania niektórych operacji do obiektu wywołującego. Podstawowy problem jest generowanie kodu w imieniu mniejszym zaufania kodu i uruchomić je na wyższe zaufania. Problem worsens podczas wywołującego może mieć wpływ na generowanie kodu, dlatego należy upewnić się, że generowane jest tylko kod, który należy wziąć pod uwagę bezpieczne.  
  
 Musisz wiedzieć, dokładnie jaki kod jest generowany przez cały czas. Oznacza to, że muszą mieć ścisłej kontroli na wartości, które można uzyskać od użytkownika, którymi są ujęte w cudzysłów ciągi (które należy zastosować ucieczkę, nie mogą zawierać elementy nieoczekiwany kod), identyfikatorów (które powinny być sprawdzane, aby sprawdzić, czy są one prawidłowe identyfikatory) lub innych elementów. Identyfikatory może być niebezpieczne, ponieważ może być modyfikowany skompilowanym zestawie, dzięki czemu jego identyfikatory zawierać dziwne znaki, które będą prawdopodobnie Podziel je (mimo że jest to rzadko luki w zabezpieczeniach).  
  
 Zaleca się, że generowanie kodu przy użyciu odbicia emisji, który często pomaga uniknąć wiele z tych problemów.  
  
 Podczas kompilowania kodu rozważ, czy istnieje inny sposób złośliwych programów można go zmodyfikować. Czy istnieje krótkim przedziale czasu, w którym złośliwego kodu, można zmienić kod źródłowy na dysku przed kompilator odczytuje go lub przed kod ładuje plik dll? Jeśli tak, należy chronić katalog zawierający pliki, za pomocą listy kontroli dostępu w systemie plików, zależnie od potrzeb.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
