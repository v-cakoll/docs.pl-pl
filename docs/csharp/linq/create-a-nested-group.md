---
title: Tworzenie grup zagnieżdżonych
description: Jak tworzenie grup zagnieżdżonych.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: dd1158bfa1456342fe8967aed5e02ecebae591c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273146"
---
# <a name="create-a-nested-group"></a>Tworzenie grup zagnieżdżonych

Poniższy przykład przedstawia sposób tworzenia grup zagnieżdżonych w wyrażeniu zapytania składnika LINQ. Każdej grupy, która jest tworzone zgodnie ze skonfigurowanym poziomie roku lub klasy uczniów następnie jest podzielony na grupy na podstawie nazw poszczególnych osób.  
  
## <a name="example"></a>Przykład

 > [!NOTE]
 > Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md). 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 Należy pamiętać, że trzy zagnieżdżone `foreach` pętle są wymagane do wykonywania iteracji wewnętrzne elementy grup zagnieżdżonych.  
  
## <a name="see-also"></a>Zobacz także  
 [Wyrażenia zapytań LINQ](index.md)
