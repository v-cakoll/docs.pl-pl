---
title: Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c231c946897772a6f02cce6eb2d3c4936b72a35e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716042"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia

Po utworzeniu procesu systemu operacyjnego, system operacyjny wprowadza wątku w celu wykonania kodu w tym procesie, w tym wszelkie oryginalną domenę aplikacji. Od tego momentu można tworzyć i zniszczone bez żadnych wątków systemu operacyjnego, niekoniecznie są utworzone lub zniszczone domen aplikacji. Jeśli wykonywany kod jest zarządzany kod, a następnie <xref:System.Threading.Thread> obiekt wykonywany wątek w bieżącej domenie aplikacji można uzyskać przez pobranie statycznej <xref:System.Threading.Thread.CurrentThread%2A> właściwości typu <xref:System.Threading.Thread>. W tym temacie opisano tworzenie wątków i omówiono alternatywy przekazywania danych do procedury wątku.  
  
## <a name="creating-a-thread"></a>Tworzenie wątku

 Tworzenie nowego <xref:System.Threading.Thread> obiektu tworzy nowy wątek. <xref:System.Threading.Thread> Klasa ma konstruktory, które przyjmują <xref:System.Threading.ThreadStart> delegować lub <xref:System.Threading.ParameterizedThreadStart> delegować; delegat opakowuje metodę, która jest wywoływana przez nowy wątek, gdy wywołujesz <xref:System.Threading.Thread.Start%2A> metody. Wywoływanie <xref:System.Threading.Thread.Start%2A> więcej niż jeden raz powoduje, że <xref:System.Threading.ThreadStateException> zostanie wygenerowany.  
  
 <xref:System.Threading.Thread.Start%2A> Metoda zwraca natychmiast, często przed faktycznie został uruchomiony nowy wątek. Możesz użyć <xref:System.Threading.Thread.ThreadState%2A> i <xref:System.Threading.Thread.IsAlive%2A> właściwości, aby określić stan wątku w danym momencie, ale te właściwości nie mogą być używane do synchronizowania działania wątków.  
  
> [!NOTE]
> Po uruchomieniu wątek nie jest konieczne do przechowywania odwołań do <xref:System.Threading.Thread> obiektu. Wątek w dalszym ciągu wykonania do czasu zakończenia procedury wątku.  
  
 Poniższy przykład kodu tworzy dwa nowe wątki wywołanie wystąpienia i metody statyczne na inny obiekt.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>Przekazywanie danych do wątków

 W .NET Framework w wersji 2.0 <xref:System.Threading.ParameterizedThreadStart> delegata zapewnia łatwy sposób przekazać obiekt zawierający dane do wątku, po wywołaniu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenie metody. Zobacz <xref:System.Threading.ParameterizedThreadStart> dla przykładu kodu.  
  
 Za pomocą <xref:System.Threading.ParameterizedThreadStart> delegat nie jest bezpieczny sposób przekazywania danych, ponieważ <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenie metody akceptuje dowolny obiekt. Alternatywą jest hermetyzacji procedury wątku i dane w klasie pomocy i użyj <xref:System.Threading.ThreadStart> delegata do wykonania procedury wątku. Poniższy przykład pokazuje tej techniki:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ani <xref:System.Threading.ThreadStart> ani <xref:System.Threading.ParameterizedThreadStart> pełnomocnik ma wartość zwracaną, ponieważ nie istnieje żadne miejsce do zwracania danych z wywołania asynchronicznego. Do pobierania wyników metoda wątku, można użyć metody wywołania zwrotnego, jak pokazano w następnej sekcji.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Pobieranie danych z wątków, z metodami wywołania zwrotnego

 W poniższym przykładzie pokazano metodę wywołania zwrotnego, która pobiera dane z wątku. Konstruktor dla klasy, która zawiera dane, a także metoda wątku akceptuje także obiekt delegowany reprezentujący metodę wywołania zwrotnego; przed zakończeniem metoda wątek wywołuje delegata wywołania zwrotnego.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [Wątkowość](index.md)
- [Używanie wątków i wątkowości](using-threads-and-threading.md)
