---
title: Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia
description: Zapoznaj się z tematem tworzenia wątków i przekazywania danych w czasie rozpoczęcia procesu systemu operacyjnego w programie .NET.
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
ms.openlocfilehash: 811028d3c853441ff3a61d3628a44e5c65ba7059
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661917"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia

Podczas tworzenia procesu systemu operacyjnego system operacyjny wprowadza wątek w celu wykonania kodu w tym procesie, w tym wszystkich oryginalnych domen aplikacji. Od tego momentu domeny aplikacji mogą być tworzone i niszczone bez konieczności tworzenia lub zniszczenia wątków systemu operacyjnego. Jeśli wykonywany kod jest kodem zarządzanym, <xref:System.Threading.Thread> można uzyskać obiekt dla wątku wykonywanego w bieżącej domenie aplikacji, pobierając Właściwość statyczną <xref:System.Threading.Thread.CurrentThread%2A> typu <xref:System.Threading.Thread> . W tym temacie opisano tworzenie wątku i omówiono alternatywy przekazywania danych do procedury wątku.  
  
## <a name="creating-a-thread"></a>Tworzenie wątku

 Tworzenie nowego <xref:System.Threading.Thread> obiektu powoduje utworzenie nowego wątku zarządzanego. <xref:System.Threading.Thread>Klasa ma konstruktory, które przyjmują <xref:System.Threading.ThreadStart> delegata lub <xref:System.Threading.ParameterizedThreadStart> delegata; delegat otacza metodę, która jest wywoływana przez nowy wątek po wywołaniu <xref:System.Threading.Thread.Start%2A> metody. Wywoływanie <xref:System.Threading.Thread.Start%2A> więcej niż raz powoduje, że <xref:System.Threading.ThreadStateException> zostanie zgłoszony.  
  
 <xref:System.Threading.Thread.Start%2A>Metoda wraca natychmiast, często przed rozpoczęciem nowego wątku. Można użyć <xref:System.Threading.Thread.ThreadState%2A> <xref:System.Threading.Thread.IsAlive%2A> właściwości i do określenia stanu wątku w dowolnym momencie, ale te właściwości nie powinny być używane do synchronizowania działań wątków.  
  
> [!NOTE]
> Po uruchomieniu wątku nie jest konieczne zachowywanie odwołania do <xref:System.Threading.Thread> obiektu. Wątek będzie wykonywany do momentu zakończenia procedury wątku.  
  
 Poniższy przykład kodu tworzy dwa nowe wątki do wywoływania wystąpień i metod statycznych dla innego obiektu.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>Przekazywanie danych do wątków

 W .NET Framework w wersji 2,0 <xref:System.Threading.ParameterizedThreadStart> Delegat zapewnia łatwy sposób przekazywania obiektu zawierającego dane do wątku po wywołaniu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenia metody. Zobacz <xref:System.Threading.ParameterizedThreadStart> , aby zobaczyć przykład kodu.  
  
 Użycie <xref:System.Threading.ParameterizedThreadStart> delegata nie jest bezpiecznym typem sposobu przekazywania danych, ponieważ <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> Przeciążenie metody akceptuje każdy obiekt. Alternatywą jest hermetyzacja procedury wątku i danych w klasie pomocnika i użycie <xref:System.Threading.ThreadStart> delegata do wykonania procedury wątku. Poniższy przykład ilustruje tę technikę:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ani <xref:System.Threading.ThreadStart> <xref:System.Threading.ParameterizedThreadStart> delegat nie ma zwracanej wartości, ponieważ nie ma miejsca do zwrócenia danych z wywołania asynchronicznego. Aby pobrać wyniki metody wątku, można użyć metody wywołania zwrotnego, jak pokazano w następnej sekcji.
  
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
