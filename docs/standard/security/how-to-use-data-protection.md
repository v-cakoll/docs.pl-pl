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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b043c5a2173cff9eb82497f6d4ee8b7c0aa3f14c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180205"
---
# <a name="how-to-use-data-protection"></a>Porady: stosowanie ochrony danych
.NET Framework zapewnia dostęp do ochrony danych interfejsu API (DPAPI), co pozwala na szyfrowanie danych, korzystając z informacji z bieżącego konta użytkownika lub komputera.  Korzystając z interfejsu DPAPI złagodzić się trudne problem jawnie generowania i przechowywania klucza kryptograficznego.  
  
 Użyj <xref:System.Security.Cryptography.ProtectedMemory> klasy w celu zaszyfrowania tablicę bajtów w pamięci.  Ta funkcja jest dostępna w systemie Microsoft Windows XP i nowszych systemach operacyjnych.  Można określić pamięci zaszyfrowane przez bieżący proces odszyfrować je mogą tylko przez wszystkie procesy lub z tym samym kontekście użytkownika bieżącego procesu.  Zobacz <xref:System.Security.Cryptography.MemoryProtectionScope> wyliczenie, aby uzyskać szczegółowy opis <xref:System.Security.Cryptography.ProtectedMemory> opcje.  
  
 Użyj <xref:System.Security.Cryptography.ProtectedData> klasy w celu zaszyfrowania kopiowania tablicy bajtów. Ta funkcja jest dostępna w systemie Microsoft Windows 2000 i nowszych systemach operacyjnych.  Można określić, czy dane są szyfrowane przy użyciu bieżącego konta użytkownika odszyfrować je mogą tylko tego samego konta użytkownika, lub można określić, że dane są szyfrowane przy użyciu bieżącego konta użytkownika można odszyfrować przez dowolne konto na komputerze.  Zobacz <xref:System.Security.Cryptography.DataProtectionScope> wyliczenie, aby uzyskać szczegółowy opis <xref:System.Security.Cryptography.ProtectedData> opcje.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Aby szyfrować dane w pamięci przy użyciu ochrony danych  
  
1.  Wywołaj statyczną <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> metody podczas przekazując tablicę bajtów do szyfrowania, entropii i zakresu ochrony pamięci.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Aby odszyfrować dane w pamięci przy użyciu ochrony danych  
  
1.  Wywołaj statyczną <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> metody podczas przekazywania tablica bajtów do odszyfrowania i zakresu ochrony pamięci.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Do szyfrowania danych do pliku lub strumienia za pomocą ochrony danych  
  
1.  Utwórz losowe entropii.  
  
2.  Wywołaj statyczną <xref:System.Security.Cryptography.ProtectedData.Protect%2A> metody podczas przekazując tablicę bajtów do szyfrowania, entropii i zakresu ochrony danych.  
  
3.  Zaszyfrowane dane należy zapisać do pliku lub strumienia.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Aby odszyfrować dane z pliku lub strumienia za pomocą ochrony danych  
  
1.  Przeczytaj zaszyfrowane dane z pliku lub strumienia.  
  
2.  Wywołaj statyczną <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> metody podczas przekazywania tablica bajtów do odszyfrowania i zakresu ochrony danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje dwa rodzaje szyfrowania i odszyfrowywania.  Po pierwsze w przykładzie kodu szyfruje i odszyfrowuje w pamięci tablica bajtów.  Następnie w przykładzie kodu szyfruje kopiowania tablicy bajtów, zapisuje w pliku, służy do ładowania danych z kopii pliku, a następnie odszyfrowuje dane.  W przykładzie wyświetlono oryginalne dane, zaszyfrowane dane i odszyfrowane dane.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Odwołanie do `System.Security.dll`.  
  
-   Obejmują <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, i <xref:System.Text> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.ProtectedMemory>  
- <xref:System.Security.Cryptography.ProtectedData>
