---
title: Podstawowe manipulacje ciągami w .NET
description: Zobacz przykład, który wywołuje wiele metod ciągu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 87ce7a79ce18ca8f5579841ad9e52e2519d6ac73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187259"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Jak: Wykonywanie podstawowych manipulacji ciągami w .NET

W poniższym przykładzie użyto niektórych metod omówione w [podstawowych operacji ciągów](../../../docs/standard/base-types/basic-string-operations.md) tematy do konstruowania klasy, która wykonuje manipulacje ciągami w sposób, który można znaleźć w aplikacji w świecie rzeczywistym. Klasa `MailToData` przechowuje nazwę i adres osoby w oddzielnych właściwościach i `City` `State`umożliwia `Zip` połączenie , i pola w jeden ciąg do wyświetlenia dla użytkownika. Ponadto klasa umożliwia użytkownikowi wprowadzenie informacji o mieście, stanie i kodzie pocztowym jako pojedynczy ciąg; aplikacja automatycznie analizuje pojedynczy ciąg i wprowadza odpowiednie informacje do odpowiedniej właściwości.  
  
Dla uproszczenia w tym przykładzie używa aplikacji konsoli z interfejsem wiersza polecenia.  
  
## <a name="example"></a>Przykład  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
Po wykonaniu poprzedniego kodu użytkownik jest proszony o podanie nazwy i adresu. Aplikacja umieszcza informacje w odpowiednich właściwościach i wyświetla informacje z powrotem do użytkownika, tworząc pojedynczy ciąg, który wyświetla informacje o mieście, stanie i kodzie pocztowym.  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
