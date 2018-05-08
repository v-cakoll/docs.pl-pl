---
title: Zapewnianie integralności danych za pomocą wartości skrótu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27e4abcd5e8dfe253ba8a7ea1ba5022561ed9ae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Zapewnianie integralności danych za pomocą wartości skrótu
Wartość skrótu jest wartość liczbową o stałej długości, który unikatowo identyfikuje dane. Wartości skrótu reprezentują dużych ilości danych jako dużo mniejsze wartości liczbowe, dlatego są one używane z podpisami cyfrowymi. Wartość skrótu można podpisać efektywniej niż podpisywania wyższej wartości. Wartości skrótu są także przydatne do sprawdzania integralności danych przesyłanych za pośrednictwem niezabezpieczonych kanałów. Wartość skrótu odebranych danych można porównać wartości skrótu danych jako został wysłany do określenia, czy dane zostało zmienione.  
  
 W tym temacie opisano sposób generować i weryfikować skrótu przy użyciu klasy w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="generating-a-hash"></a>Generowanie skrótów  
 Klasy zarządzane wyznaczania wartości skrótu można skrótu tablicę bajtów lub obiektu zarządzanego strumienia. W poniższym przykładzie użyto algorytmu wyznaczania wartości skrótu SHA1, aby utworzyć wartość skrótu ciągu. W przykładzie użyto <xref:System.Text.UnicodeEncoding> klasę, aby przekonwertować ciąg na tablicę bajtów, które są przechowywane w formie skrótu, za pomocą <xref:System.Security.Cryptography.SHA1Managed> klasy. Wartość skrótu jest następnie wyświetlane w konsoli.  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Ten kod wyświetli następujący ciąg do konsoli:  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>Sprawdzanie wartości skrótu  
 Dane mogą być porównywane do wartości skrótu, aby ustalić jego integralności. Zazwyczaj jest przemieszać danych w określonym czasie i wartości skrótu jest chroniona w inny sposób. W późniejszym czasie dane można ponownie mieszany i porównywana z wartością chronionych. Jeśli wartości skrótu są zgodne, dane nie zostały zmienione. Jeśli wartości nie są zgodne, danych została uszkodzona. Dla tego systemu do pracy chronionych skrót musi być szyfrowane lub ujawniana wszystkie niezaufane.  
  
 Poniższy przykład porównuje Poprzednia wartość skrótu ciągu na nową wartość skrótu. W tym przykładzie każdy bajt wartości skrótu w pętli i sprawia, że porównanie.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 Jeśli wartości skrótu dwóch zgodne, ten kod wyświetla następujące do konsoli:  
  
```  
The hash codes match.  
```  
  
 Jeśli nie są zgodne, kod wyświetla następujące informacje:  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
