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
ms.openlocfilehash: 16770ea938973372d1d94c628c42d5d5bf10c695
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199586"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Zapewnianie integralności danych za pomocą wartości skrótu
Wartość skrótu jest wartością liczbową o stałej długości, która jednoznacznie identyfikuje dane. Wartości skrótów reprezentują dużych ilości danych jako dużo mniejsze wartości liczbowe, dzięki czemu są one używane, za pomocą podpisów cyfrowych. Wartość skrótu można podpisać efektywniej niż podpisywania większa wartość. Wartości skrótu są również przydatne w przypadku sprawdzania integralności danych przesyłanych za pośrednictwem niezabezpieczonych kanałów. Wartość skrótu odebranych danych można porównać do wartości skrótu danych jako wysłano w celu ustalenia, czy dane zostało zmienione.  
  
 W tym temacie opisano sposób generowania i sprawdzić kody skrótów przy użyciu klas w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="generating-a-hash"></a>Generowanie skrótów  
 Klasy zarządzane wyznaczania wartości skrótu można skrótu tablicę bajtów lub obiektu zarządzanego strumienia. W poniższym przykładzie użyto algorytmu wyznaczania wartości skrótu SHA1, aby utworzyć wartość skrótu ciągu. W przykładzie użyto <xref:System.Text.UnicodeEncoding> klasy w celu przekonwertowania ciągu na tablicę bajtów, które są przekazywane przy użyciu <xref:System.Security.Cryptography.SHA1Managed> klasy. Wartość skrótu jest następnie wyświetlana w konsoli.  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Ten kod wyświetli następujący ciąg do konsoli:  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>Weryfikowanie wartości skrótu  
 Dane można porównać do wartość skrótu, aby określić ich integralności. Zazwyczaj danych jest wyznaczana wartość skrótu w określonym czasie, a wartość skrótu jest chroniona w jakiś sposób. W późniejszym czasie dane można ponownie skrótu i porównywana z wartością chronionych. Jeśli wartości skrótu są zgodne, dane nie został zmieniony. Jeśli wartości nie są zgodne, zostały uszkodzone dane. Dla tego systemu do pracy chronionych skrótu musi być szyfrowane lub trzymane w tajemnicy wszystkie niezaufane.  
  
 W poniższym przykładzie porównano poprzednią wartość skrótu ciągu na nową wartość skrótu. W tym przykładzie pętli poszczególne bajty wartości skrótu i sprawia, że porównanie.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 Jeśli wartości skrótu dwóch zgodne, ten kod wyświetla następujące do konsoli:  
  
```  
The hash codes match.  
```  
  
 Jeśli nie są zgodne, ten kod wyświetla następujące informacje:  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
