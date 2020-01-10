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
ms.openlocfilehash: 64ddcc6a379e5719eb734eede13e576a707696fe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705889"
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpieczenia i generowanie kodu na bieżąco
Niektóre biblioteki działają przez generowanie kodu i uruchamianie go w celu wykonania niektórych operacji dla obiektu wywołującego. Podstawowy problem polega na wygenerowaniu kodu w imieniu kodu o niższym zaufaniu i uruchomieniu go na wyższym poziomie zaufania. Problem pogorszy się, gdy obiekt wywołujący może wpływać na generowanie kodu, dlatego należy się upewnić, że generowany jest tylko kod, który jest uważany za bezpieczny.  
  
 Musisz dokładnie poznać kod, który jest generowany przez cały czas. Oznacza to, że musisz mieć ścisłe kontrolki dla wszystkich wartości, które otrzymujesz od użytkownika, czy są to ciągi ujęte w cudzysłów (które powinny zostać zmienione, aby nie zawierały nieoczekiwanych elementów kodu), identyfikatory (które należy sprawdzić, aby sprawdzić, czy są one prawidłowe identyfikatory) lub inne. Identyfikatory mogą być niebezpieczne, ponieważ skompilowany zestaw można zmodyfikować tak, aby jego identyfikatory zawierały nietypowe znaki, które prawdopodobnie spowodują jego przerwanie (chociaż jest to rzadko występująca Luka w zabezpieczeniach).  
  
 Zaleca się generowanie kodu przy użyciu emisji odbicia, co często pomaga uniknąć wielu z tych problemów.  
  
 Podczas kompilowania kodu należy rozważyć, czy istnieje pewien sposób, w jaki złośliwy program mógłby go zmodyfikować. Czy istnieje niewielkie okno czasu, w którym złośliwy kod może zmienić kod źródłowy na dysku, zanim kompilator go odczyta lub zanim kod załaduje plik dll? W takim przypadku należy chronić katalog zawierający te pliki przy użyciu listy Access Control w systemie plików, zgodnie z potrzebami.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
