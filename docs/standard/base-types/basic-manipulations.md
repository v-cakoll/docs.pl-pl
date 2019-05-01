---
title: 'Instrukcje: Wykonywanie podstawowych działań na ciągach w .NET'
description: Zobacz przykład, który wywołuje wiele metod ciągów.
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
ms.custom: seodec18
ms.openlocfilehash: 11f8043745c631a642b437339240cbf06fc8df5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025941"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Instrukcje: Wykonywanie podstawowych działań na ciągach w .NET
W poniższym przykładzie użyto niektórych metod omówione w [podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md) tematy, aby utworzyć klasę, która wykonuje działań na ciągach w taki sposób, który można znaleźć w rzeczywistych aplikacjach. `MailToData` Klasa przechowuje nazwę i adres osoba w oddzielnych właściwości i zapewnia sposób łączenia `City`, `State`, i `Zip` pól w jeden ciąg do wyświetlania użytkownikowi. Ponadto klasa pozwala użytkownikowi wprowadzanie miejscowość, stan i kod POCZTOWY jako pojedynczy ciąg; Aplikacja automatycznie analizuje jeden ciąg i wprowadza odpowiednie informacje w odpowiednich właściwości.  
  
 Dla uproszczenia w tym przykładzie użyto aplikacji konsoli przy użyciu interfejsu wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Jeśli poprzedni kod jest wykonywany, użytkownik jest proszony o wprowadzenie swojej nazwy i adresu. Aplikacja umieszcza informacje w odpowiednie właściwości i wyświetla informacje użytkownika, tworząc jeden ciąg, który wyświetla miejscowość, stan i kod POCZTOWY.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
