---
title: "Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia"
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
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia
Po utworzeniu procesu systemu operacyjnego, systemu operacyjnego injects wątku wykonania kodu w tego procesu, w tym wszelkie oryginalnego domeny aplikacji. Od tego momentu można tworzyć i zniszczone bez żadnych wątków systemu operacyjnego zawsze tworzona lub zniszczony domen aplikacji. Jeśli kod wykonywany jest zarządzany kod, a następnie <xref:System.Threading.Thread> obiekt wątku wykonywania w bieżącej domenie aplikacji można uzyskać, pobierając statycznych <xref:System.Threading.Thread.CurrentThread%2A> właściwości typu <xref:System.Threading.Thread>. W tym temacie opisano tworzenie wątków i omówiono alternatyw przekazywania danych do procedury wątku.  
  
## <a name="creating-a-thread"></a>Tworzenie wątku  
 Tworzenie nowego <xref:System.Threading.Thread> obiektu tworzy nowego wątku zarządzanego. <xref:System.Threading.Thread> Klasa ma konstruktorów przyjmujących <xref:System.Threading.ThreadStart> delegować lub <xref:System.Threading.ParameterizedThreadStart> delegata; delegat opakowuje wywoływanej przez nowego wątku po wywołaniu metody <xref:System.Threading.Thread.Start%2A> metody. Wywoływanie <xref:System.Threading.Thread.Start%2A> więcej niż raz spowoduje, że <xref:System.Threading.ThreadStateException> zostanie wygenerowany.  
  
 <xref:System.Threading.Thread.Start%2A> Metoda zwraca natychmiast, często przed nowego wątku rzeczywiście została uruchomiona. Można użyć <xref:System.Threading.Thread.ThreadState%2A> i <xref:System.Threading.Thread.IsAlive%2A> właściwości, aby określić stan wątku w danym momencie, ale te właściwości nie mogą być używane do synchronizacji działania wątków.  
  
> [!NOTE]
>  Po uruchomieniu wątku nie jest konieczne do zachowania odwołanie do <xref:System.Threading.Thread> obiektu. Wątek w dalszym ciągu wykonania do czasu zakończenia procedury wątku.  
  
 Poniższy przykład kodu tworzy dwa nowe wątki wywołanie wystąpienia i metod statycznych na inny obiekt.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a>Przekazywanie danych do wątków i pobierania danych z wątków  
 W programie .NET Framework w wersji 2.0 <xref:System.Threading.ParameterizedThreadStart> delegowanie umożliwia łatwe do przekazania obiekt zawierający dane do wątku po wywołaniu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenie metody. Zobacz <xref:System.Threading.ParameterizedThreadStart> dla przykładowego kodu.  
  
 Przy użyciu <xref:System.Threading.ParameterizedThreadStart> delegat nie jest bezpieczny sposób przekazywania danych, ponieważ <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenie metody akceptuje dowolny obiekt. Alternatywą jest Hermetyzowanie procedury wątku i danych w klasie pomocy i użyj <xref:System.Threading.ThreadStart> delegata do wykonywania procedury wątku. Ta technika przedstawiono w przykładach dwóch kodu, które należy wykonać.  
  
 Oba te obiekty delegowane ma wartość zwracaną, ponieważ nie istnieje żadne miejsce do zwrócić dane z wywołanie asynchroniczne. Można pobrać wyników metody wątku, używając metody wywołania zwrotnego, jak pokazano w drugim przykładzie kodu.  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a>Pobieranie danych z metody wywołania zwrotnego  
 W poniższym przykładzie pokazano metodę wywołania zwrotnego, która pobiera dane z wątku. Konstruktor klasy, która zawiera dane, a także metoda wątku również akceptuje delegata reprezentującego metodę wywołania zwrotnego; przed zakończeniem metody wątku wywołuje delegata wywołania zwrotnego.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)
