---
title: 'Porady: stosowanie ochrony danych'
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
ms.openlocfilehash: 0efd677f11189b28b8efc184c04b30a047ab942b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706035"
---
# <a name="how-to-use-data-protection"></a>Porady: stosowanie ochrony danych
.NET Framework zapewnia dostęp do interfejsu API ochrony danych (DPAPI), który umożliwia szyfrowanie danych przy użyciu informacji z bieżącego konta użytkownika lub komputera.  Korzystając z interfejsu DPAPI, można złagodzić trudne problemy związane z jawnym generowaniem i przechowywaniem klucza kryptograficznego.  
  
 Użyj klasy <xref:System.Security.Cryptography.ProtectedMemory>, aby zaszyfrować tablicę bajtów w pamięci.  Ta funkcja jest dostępna w systemie Microsoft Windows XP i nowszych systemach operacyjnych.  Można określić, że pamięć zaszyfrowana przez bieżący proces może zostać odszyfrowana tylko przez bieżący proces, przez wszystkie procesy lub z tego samego kontekstu użytkownika.  Aby uzyskać szczegółowy opis opcji <xref:System.Security.Cryptography.ProtectedMemory>, zobacz Wyliczenie <xref:System.Security.Cryptography.MemoryProtectionScope>.  
  
 Użyj klasy <xref:System.Security.Cryptography.ProtectedData>, aby zaszyfrować kopię tablicy bajtów. Ta funkcja jest dostępna w systemie Microsoft Windows 2000 i nowszych systemach operacyjnych.  Możesz określić, że dane zaszyfrowane przez bieżące konto użytkownika mogą zostać odszyfrowane tylko przez to samo konto użytkownika, lub możesz określić, że dane zaszyfrowane przez bieżące konto użytkownika mogą zostać odszyfrowane za pomocą dowolnego konta na komputerze.  Aby uzyskać szczegółowy opis opcji <xref:System.Security.Cryptography.ProtectedData>, zobacz Wyliczenie <xref:System.Security.Cryptography.DataProtectionScope>.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Aby zaszyfrować dane znajdujące się w pamięci przy użyciu ochrony danych  
  
1. Wywołaj metodę static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> podczas przekazywania tablicy bajtów do zaszyfrowania, entropii i zakresu ochrony pamięci.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Aby odszyfrować dane w pamięci przy użyciu ochrony danych  
  
1. Wywołaj metodę static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> podczas przekazywania tablicy bajtów do odszyfrowania i zakresu ochrony pamięci.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Aby zaszyfrować dane do pliku lub strumienia przy użyciu ochrony danych  
  
1. Utwórz entropię losową.  
  
2. Wywołaj metodę static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> podczas przekazywania tablicy bajtów do zaszyfrowania, entropii i zakresu ochrony danych.  
  
3. Zapisz dane zaszyfrowane do pliku lub strumienia.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Aby odszyfrować dane z pliku lub strumienia przy użyciu ochrony danych  
  
1. Odczytaj zaszyfrowane dane z pliku lub strumienia.  
  
2. Wywołaj metodę static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> podczas przekazywania tablicy bajtów do odszyfrowania i zakresu ochrony danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje dwie formy szyfrowania i odszyfrowywania.  Najpierw kod szyfruje, a następnie odszyfrowuje tablicę bajtów w pamięci.  W przykładzie kod szyfruje kopię tablicy bajtowej, zapisuje ją w pliku, ładuje dane z powrotem z pliku, a następnie odszyfrowuje dane.  Przykład wyświetla oryginalne dane, zaszyfrowane dane i odszyfrowane dane.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Dołącz odwołanie do `System.Security.dll`.  
  
- Uwzględnij przestrzeń nazw <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>i <xref:System.Text>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
