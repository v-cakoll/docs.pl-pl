---
title: Zabezpieczenia i generowanie kodu na bieżąco
description: Generowanie kodu w imieniu niemniejszego zaufania kodu, który jest uruchamiany na wyższym poziomie zaufania, stanowi zagrożenie bezpieczeństwa, zwłaszcza gdy obiekt wywołujący może wpływać na generowanie kodu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 7e5168aa9305c559cf5ea2fb197b2c23ce2a05b0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291035"
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpieczenia i generowanie kodu na bieżąco
Niektóre biblioteki działają przez generowanie kodu i uruchamianie go w celu wykonania niektórych operacji dla obiektu wywołującego. Podstawowy problem polega na wygenerowaniu kodu w imieniu kodu o niższym zaufaniu i uruchomieniu go na wyższym poziomie zaufania. Problem pogorszy się, gdy obiekt wywołujący może wpływać na generowanie kodu, dlatego należy się upewnić, że generowany jest tylko kod, który jest uważany za bezpieczny.  
  
 Musisz dokładnie poznać kod, który jest generowany przez cały czas. Oznacza to, że musisz mieć ścisłe kontrolki dla wszystkich wartości, które otrzymujesz od użytkownika, czy są to ciągi ujęte w cudzysłów (które należy zmienić, aby nie mogli zawierać nieoczekiwanych elementów kodu), identyfikatory (które powinny być sprawdzane w celu sprawdzenia, czy są prawidłowymi identyfikatorami) lub inne. Identyfikatory mogą być niebezpieczne, ponieważ skompilowany zestaw można zmodyfikować tak, aby jego identyfikatory zawierały nietypowe znaki, które prawdopodobnie spowodują jego przerwanie (chociaż jest to rzadko występująca Luka w zabezpieczeniach).  
  
 Zaleca się generowanie kodu przy użyciu emisji odbicia, co często pomaga uniknąć wielu z tych problemów.  
  
 Podczas kompilowania kodu należy rozważyć, czy istnieje pewien sposób, w jaki złośliwy program mógłby go zmodyfikować. Czy istnieje niewielkie okno czasu, w którym złośliwy kod może zmienić kod źródłowy na dysku, zanim kompilator go odczyta lub zanim kod załaduje plik dll? W takim przypadku należy chronić katalog zawierający te pliki przy użyciu listy Access Control w systemie plików, zgodnie z potrzebami.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](secure-coding-guidelines.md)
