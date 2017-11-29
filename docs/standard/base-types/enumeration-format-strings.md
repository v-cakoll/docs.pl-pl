---
title: "Wyliczanie ciągów formatujących"
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
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0992d8591711073f9094c29fad980a8e652e686
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="enumeration-format-strings"></a>Wyliczanie ciągów formatujących
Można użyć <xref:System.Enum.ToString%2A?displayProperty=nameWithType> metodę, aby utworzyć nowy obiekt ciągu reprezentujący liczbowe, szesnastkowo lub wartość ciągu dla elementu członkowskiego wyliczenia. Ta metoda przyjmuje jeden wyliczenie formatowania ciągi, aby określić wartości, które mają być zwracane.  
  
 W poniższej tabeli wymieniono wyliczenie formatowanie ciągów i wartości, które zwracają. Te specyfikatory formatu nie jest rozróżniana.  
  
| Ciąg formatu | Wynik |  
| ------------- | ------ |  
| G lub g | Wyświetla wpis wyliczenie jako wartość typu ciąg, jeśli to możliwe, a w przeciwnym razie wyświetlana jest wartość całkowitą bieżącego wystąpienia. Jeśli zdefiniowano wyliczenia z **flagi** ustawiony atrybut, ciąg wartości każdy nieprawidłowy wpis są połączone ze sobą, oddzielonych przecinkami. Jeśli **flagi** atrybut nie jest ustawiony, nieprawidłową wartość jest wyświetlana jako wpis liczbowych. Poniższy przykład przedstawia specyfikator formatu G.<br><br>[!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)] |  
| F lub f | Wyświetla wyliczenie hasło w postaci wartości ciągu, jeśli to możliwe. Jeśli wartość, które mogą być całkowicie wyświetlane jako suma wpisów w wyliczeniu (nawet jeśli **flagi** atrybut nie jest obecny), wartości ciągu każdego wpisu prawidłowe są łączone, oddzielonych przecinkami. Jeśli wartość nie może całkowicie określana na podstawie pozycji wyliczenia, wartość jest formatowana jako wartość całkowita. Poniższy przykład przedstawia specyfikator formatu F.<br><br>[!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)] |  
| D lub d | Wyświetla wpis wyliczenie jako wartość całkowitą w możliwie najkrótszym reprezentacji możliwe. Poniższy przykład przedstawia specyfikator formatu D.<br><br>[!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)] |  
| X lub x | Wyświetla wpis wyliczenie jako wartość szesnastkową. Wartość jest reprezentowany z zerami w razie potrzeby do zapewnienia, że wartość minimalna ośmiu cyfr długości. Poniższy przykład przedstawia specyfikator formatu X.<br /><br /> [!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)] |  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano wyliczenie o nazwie `Colors` składający się z trzech wpisów: `Red`, `Blue`, i `Green`.  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 Po zdefiniowaniu wyliczenia wystąpienia mogą być deklarowane w następujący sposób.  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 `Color.ToString(System.String)` Metody następnie może służyć do wyświetlania wartości wyliczenia na różne sposoby, w zależności od specyfikator formatu przekazany do niego.  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Formatowanie tekstu](../../../docs/standard/base-types/formatting-types.md)
