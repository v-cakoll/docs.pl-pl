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
ms.openlocfilehash: ffb1081c80c31353ad38080ae16ef9f8a74b5481
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44046778"
---
# <a name="security-and-on-the-fly-code-generation"></a>Zabezpieczenia i generowanie kodu na bieżąco
Niektóre biblioteki działają przez generowanie kodu i uruchomiania go do wykonania niektórych operacji do obiektu wywołującego. Podstawowy problem jest generowanie kodu w imieniu mniejszym zaufanemu kodowi i uruchamiając go na wyższe zaufania. Problem worsens, gdy obiekt wywołujący może mieć wpływ na generowanie kodu, więc należy upewnić się, którym generowany jest tylko kodu, które uważasz za bezpieczne.  
  
 Musisz wiedzieć, dokładnie, jaki kod jest generowany przez cały czas. Oznacza to, że muszą mieć ścisłą kontrolą od żadnych wartości, które można uzyskać od użytkownika, są to ciągi ujęty w cudzysłów, (które powinny być wyjściowym, więc nie mogą zawierać elementy nieoczekiwany kod), identyfikatory, (które powinny być sprawdzane w celu sprawdzenia, czy są prawidłowe identyfikatory) lub cokolwiek innego. Identyfikatory może być niebezpieczne, ponieważ skompilowanego zestawu można zmodyfikować tak, aby jego identyfikatory zawierać otrzymano nieoczekiwany znaki, które prawdopodobnie będą tę kwestię nieco (chociaż rzadko jest to luka w zabezpieczeniach).  
  
 Zalecane jest, że generowanie kodu za pomocą odbicia emisji, co często pozwala uniknąć wielu z tych problemów.  
  
 Podczas kompilowania kodu, należy rozważyć, czy jest jakiś sposób złośliwy program, można zmodyfikować go. Czy istnieje niewielki przedział czasu, przez który złośliwy kod może zmienić kod źródłowy na dysku, zanim kompilator odczyta go lub przed kod ładuje plik dll? Jeśli tak, należy włączyć ochronę do katalogu zawierającego te pliki za pomocą listy kontroli dostępu w systemie plików, zgodnie z potrzebami.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
