---
title: 'Porady: stosowanie ochrony danych'
description: Dowiedz się, jak używać ochrony danych, uzyskując dostęp do interfejsu API ochrony danych (DPAPI) w środowisku .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: c7f88105727dfd33c87a815054aa317ac2052e83
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598596"
---
# <a name="how-to-use-data-protection"></a>Porady: stosowanie ochrony danych
.NET Framework zapewnia dostęp do interfejsu API ochrony danych (DPAPI), który umożliwia szyfrowanie danych przy użyciu informacji z bieżącego konta użytkownika lub komputera.  Korzystając z interfejsu DPAPI, można złagodzić trudne problemy związane z jawnym generowaniem i przechowywaniem klucza kryptograficznego.  
  
 Użyj <xref:System.Security.Cryptography.ProtectedMemory> klasy, aby zaszyfrować tablicę bajtów w pamięci.  Ta funkcja jest dostępna w systemie Microsoft Windows XP i nowszych systemach operacyjnych.  Można określić, że pamięć zaszyfrowana przez bieżący proces może zostać odszyfrowana tylko przez bieżący proces, przez wszystkie procesy lub z tego samego kontekstu użytkownika.  <xref:System.Security.Cryptography.MemoryProtectionScope>Szczegółowy opis opcji można znaleźć w wyliczeniu <xref:System.Security.Cryptography.ProtectedMemory> .  
  
 Użyj <xref:System.Security.Cryptography.ProtectedData> klasy, aby zaszyfrować kopię tablicy bajtów. Ta funkcja jest dostępna w systemie Microsoft Windows 2000 i nowszych systemach operacyjnych.  Możesz określić, że dane zaszyfrowane przez bieżące konto użytkownika mogą zostać odszyfrowane tylko przez to samo konto użytkownika, lub możesz określić, że dane zaszyfrowane przez bieżące konto użytkownika mogą zostać odszyfrowane za pomocą dowolnego konta na komputerze.  <xref:System.Security.Cryptography.DataProtectionScope>Szczegółowy opis opcji można znaleźć w wyliczeniu <xref:System.Security.Cryptography.ProtectedData> .  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Aby zaszyfrować dane znajdujące się w pamięci przy użyciu ochrony danych  
  
1. Wywołaj metodę statyczną <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> podczas przekazywania tablicy bajtów do szyfrowania, entropii i zakresu ochrony pamięci.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Aby odszyfrować dane w pamięci przy użyciu ochrony danych  
  
1. Wywołaj metodę statyczną <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> podczas przekazywania tablicy bajtów do odszyfrowania i zakresu ochrony pamięci.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Aby zaszyfrować dane do pliku lub strumienia przy użyciu ochrony danych  
  
1. Utwórz entropię losową.  
  
2. Wywołaj metodę statyczną <xref:System.Security.Cryptography.ProtectedData.Protect%2A> podczas przekazywania tablicy bajtów do szyfrowania, entropii i zakresu ochrony danych.  
  
3. Zapisz dane zaszyfrowane do pliku lub strumienia.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Aby odszyfrować dane z pliku lub strumienia przy użyciu ochrony danych  
  
1. Odczytaj zaszyfrowane dane z pliku lub strumienia.  
  
2. Wywołaj metodę statyczną <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> podczas przekazywania tablicy bajtów do odszyfrowania i zakresu ochrony danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje dwie formy szyfrowania i odszyfrowywania.  Najpierw kod szyfruje, a następnie odszyfrowuje tablicę bajtów w pamięci.  W przykładzie kod szyfruje kopię tablicy bajtowej, zapisuje ją w pliku, ładuje dane z powrotem z pliku, a następnie odszyfrowuje dane.  Przykład wyświetla oryginalne dane, zaszyfrowane dane i odszyfrowane dane.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Dołącz odwołanie do `System.Security.dll` .  
  
- Dołącz <xref:System> <xref:System.IO> <xref:System.Security.Cryptography> przestrzeń nazw,,, i <xref:System.Text> .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
