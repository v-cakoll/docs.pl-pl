---
title: 'Porady: wykonywanie podstawowych działań na ciągach w programie .NET Framework'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1206648c694c9f09a600e3c70f4aa27118b2d458
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178055"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Porady: wykonywanie podstawowych działań na ciągach w .NET
W poniższym przykładzie użyto niektórych metod omówione w [podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md) tematy, aby utworzyć klasę, która wykonuje działań na ciągach w taki sposób, który można znaleźć w rzeczywistych aplikacjach. `MailToData` Klasa przechowuje nazwę i adres osoba w oddzielnych właściwości i zapewnia sposób łączenia `City`, `State`, i `Zip` pól w jeden ciąg do wyświetlania użytkownikowi. Ponadto klasa pozwala użytkownikowi wprowadzanie miejscowość, stan i kod POCZTOWY jako pojedynczy ciąg; Aplikacja automatycznie analizuje jeden ciąg i wprowadza odpowiednie informacje w odpowiednich właściwości.  
  
 Dla uproszczenia w tym przykładzie użyto aplikacji konsoli przy użyciu interfejsu wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Jeśli poprzedni kod jest wykonywany, użytkownik jest proszony o wprowadzenie swojej nazwy i adresu. Aplikacja umieszcza informacje w odpowiednie właściwości i wyświetla informacje użytkownika, tworząc jeden ciąg, który wyświetla miejscowość, stan i kod POCZTOWY.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
