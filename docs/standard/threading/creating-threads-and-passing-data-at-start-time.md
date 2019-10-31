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
ms.openlocfilehash: a628cbb4c9ec8e1c9ccd9fd73e72a82ecf2b2836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138102"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia

Podczas tworzenia procesu systemu operacyjnego system operacyjny wprowadza wątek w celu wykonania kodu w tym procesie, w tym wszystkich oryginalnych domen aplikacji. Od tego momentu domeny aplikacji mogą być tworzone i niszczone bez konieczności tworzenia lub zniszczenia wątków systemu operacyjnego. Jeśli wykonywany kod jest kodem zarządzanym, można uzyskać <xref:System.Threading.Thread> obiekt dla wątku wykonywanego w bieżącej domenie aplikacji, pobierając statyczną Właściwość <xref:System.Threading.Thread.CurrentThread%2A> typu <xref:System.Threading.Thread>. W tym temacie opisano tworzenie wątku i omówiono alternatywy przekazywania danych do procedury wątku.  
  
## <a name="creating-a-thread"></a>Tworzenie wątku

 Utworzenie nowego obiektu <xref:System.Threading.Thread> powoduje utworzenie nowego wątku zarządzanego. Klasa <xref:System.Threading.Thread> ma konstruktory, które pobierają <xref:System.Threading.ThreadStart> delegata lub delegata <xref:System.Threading.ParameterizedThreadStart>; delegat otacza metodę, która jest wywoływana przez nowy wątek po wywołaniu metody <xref:System.Threading.Thread.Start%2A>. Wywołanie <xref:System.Threading.Thread.Start%2A> więcej niż raz powoduje, że <xref:System.Threading.ThreadStateException> być zgłaszane.  
  
 Metoda <xref:System.Threading.Thread.Start%2A> zwraca natychmiast, często przed rozpoczęciem nowego wątku. Możesz użyć właściwości <xref:System.Threading.Thread.ThreadState%2A> i <xref:System.Threading.Thread.IsAlive%2A> do określenia stanu wątku w dowolnym momencie, ale te właściwości nie powinny być używane do synchronizowania działań wątków.  
  
> [!NOTE]
> Po uruchomieniu wątku nie jest konieczne zachowywanie odwołania do obiektu <xref:System.Threading.Thread>. Wątek będzie wykonywany do momentu zakończenia procedury wątku.  
  
 Poniższy przykład kodu tworzy dwa nowe wątki do wywoływania wystąpień i metod statycznych dla innego obiektu.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>Przekazywanie danych do wątków

 W .NET Framework w wersji 2,0, delegat <xref:System.Threading.ParameterizedThreadStart> zapewnia łatwy sposób przekazywania obiektu zawierającego dane do wątku po wywołaniu metody <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenia. Zobacz <xref:System.Threading.ParameterizedThreadStart> dla przykładowego kodu.  
  
 Użycie delegata <xref:System.Threading.ParameterizedThreadStart> nie jest bezpiecznym typem sposobu przekazywania danych, ponieważ Przeciążenie metody <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> akceptuje każdy obiekt. Alternatywą jest hermetyzacja procedury wątku i danych w klasie pomocnika i użycie delegata <xref:System.Threading.ThreadStart> w celu wykonania procedury wątku. Poniższy przykład ilustruje tę technikę:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ani <xref:System.Threading.ThreadStart> ani delegat <xref:System.Threading.ParameterizedThreadStart> ma wartość zwracaną, ponieważ nie ma miejsca do zwrócenia danych z wywołania asynchronicznego. Aby pobrać wyniki metody wątku, można użyć metody wywołania zwrotnego, jak pokazano w następnej sekcji.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Pobieranie danych z wątków z metodami wywołania zwrotnego

 Poniższy przykład demonstruje metodę wywołania zwrotnego, która pobiera dane z wątku. Konstruktor klasy, która zawiera dane i metoda wątku, również akceptuje delegata reprezentujący metodę wywołania zwrotnego; przed zakończeniem metody wątku wywołuje delegata wywołania zwrotnego.  
  
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
