---
title: "Tworzenie grup zagnieżdżonych"
description: "Jak tworzenie grup zagnieżdżonych."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
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
