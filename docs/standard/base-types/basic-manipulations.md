---
title: "Porady: wykonywanie podstawowych działań na ciągach w programie .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee9c00d02b7b5d1f391ce60f843c18445efd6edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Porady: wykonywanie podstawowych działań na ciągach w .NET
W poniższym przykładzie użyto niektóre metody omówione w [podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md) tematy, aby utworzyć klasę, która wykonuje na ciągach w sposób, który może zostać znaleziony w rzeczywistych aplikacjach. `MailToData` Klasy przechowuje nazwę i adres osoby w oddzielnych właściwości i umożliwia łączenie `City`, `State`, i `Zip` pól w jednym ciągu do wyświetlenia dla użytkownika. Ponadto klasa umożliwia użytkownikowi Wprowadź miejscowość, stan i kod POCZTOWY jako pojedynczy ciąg; Aplikacja automatycznie analizuje jeden ciąg i wprowadza odpowiednie informacje do odpowiadających im właściwości.  
  
 Dla uproszczenia w tym przykładzie użyto aplikacji konsoli przy użyciu interfejsu wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Jeśli poprzedni kod jest wykonywane, użytkownik jest proszony o wprowadzenie jego nazwę lub adres. Aplikacja umieszcza informacje w odpowiednich właściwości i wyświetla informacje do użytkownika, tworzenie jeden ciąg, który wyświetla miejscowość, stan i kod POCZTOWY.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
