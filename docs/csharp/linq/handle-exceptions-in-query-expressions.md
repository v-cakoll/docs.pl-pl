---
title: Obsługa wyjątków w wyrażeniach zapytań
description: Sposób obsługi wyjątków w wyrażeniach zapytań.
ms.date: 12/1/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 691373fabeb3934ecc454cbc3b36a5f7bf477bee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="handle-exceptions-in-query-expressions"></a>Obsługa wyjątków w wyrażeniach zapytań

Istnieje możliwość wywołania dowolnej metody w kontekście wyrażenia zapytania. Firma Microsoft zaleca jednak uniknąć wywołaniem jakiejkolwiek jego metody w wyrażeniu zapytania, który może tworzyć efektu ubocznego, takich jak modyfikowania zawartości ze źródłem danych i zgłaszanie wyjątku. W tym przykładzie pokazano, jak można uniknąć występowanie wyjątków podczas wywołania metody w wyrażeniu zapytania bez naruszania ogólne wytyczne .NET Framework dla obsługi wyjątków. Stan te wskazówki można przechwytywać określony wyjątek, podczas zrozumienie, dlaczego będzie zostać zgłoszony w danym kontekście. Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące wyjątków](../../standard/exceptions/best-practices-for-exceptions.md).  
  
 Końcowy przykład przedstawia sposób obsługi tych przypadkach, gdy należy zgłosić wyjątek w trakcie wykonywania zapytania.  
  
## <a name="example"></a>Przykład  

 Poniższy przykład przedstawia sposób przenoszenia kodu poza wyrażenie zapytania obsługi wyjątków. Jest to możliwe tylko wtedy, gdy metoda nie zależy od żadnych zmiennych lokalnych do zapytania.  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a>Przykład 

 W niektórych przypadkach najlepsze odpowiedzi na wyjątek zgłaszany w obrębie zapytania może być natychmiastowe zatrzymanie wykonywania zapytania. Poniższy przykład przedstawia sposób obsługi wyjątków, które może zostać zgłoszone z wewnątrz treści zapytania. Przyjęto założenie, że `SomeMethodThatMightThrow` potencjalnie może spowodować wyjątek, który wymaga wykonywania zapytania, aby zatrzymać.  
  
 Należy pamiętać, że `try` umieszcza bloku `foreach` pętli i nie zapytania. Jest to spowodowane `foreach` pętli jest punktem, jaką faktycznie wykonywania zapytania. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a>Zobacz też  
 [Wyrażenia zapytań LINQ](index.md)
