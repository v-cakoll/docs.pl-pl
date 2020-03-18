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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138102"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia

Po utworzeniu procesu systemu operacyjnego system operacyjny wstrzykuje wątek do wykonania kodu w tym procesie, w tym dowolnej oryginalnej domeny aplikacji. Od tego momentu domeny aplikacji mogą być tworzone i niszczone bez żadnych wątków systemu operacyjnego muszą być tworzone lub niszczone. Jeśli wykonywany kod jest kodem <xref:System.Threading.Thread> zarządzanym, obiekt dla wątku wykonywanego w bieżącej <xref:System.Threading.Thread.CurrentThread%2A> domenie aplikacji można uzyskać, pobierając właściwość statyczną typu <xref:System.Threading.Thread>. W tym temacie opisano tworzenie wątku i omówiono alternatywy przekazywania danych do procedury wątku.  
  
## <a name="creating-a-thread"></a>Tworzenie wątku

 Tworzenie nowego <xref:System.Threading.Thread> obiektu tworzy nowy wątek zarządzany. Klasa <xref:System.Threading.Thread> ma konstruktorów, <xref:System.Threading.ThreadStart> które przyjmują <xref:System.Threading.ParameterizedThreadStart> delegata lub delegata; delegat owija metodę, która jest wywoływana przez nowy <xref:System.Threading.Thread.Start%2A> wątek podczas wywoływania metody. Wywołanie <xref:System.Threading.Thread.Start%2A> więcej niż <xref:System.Threading.ThreadStateException> jeden raz powoduje, że zostanie wyrzucony.  
  
 Metoda <xref:System.Threading.Thread.Start%2A> zwraca natychmiast, często przed rozpoczęciem nowego wątku. Można użyć <xref:System.Threading.Thread.ThreadState%2A> i <xref:System.Threading.Thread.IsAlive%2A> właściwości, aby określić stan wątku w dowolnym momencie, ale te właściwości nigdy nie powinny być używane do synchronizowania działań wątków.  
  
> [!NOTE]
> Po uruchomieniu wątku nie jest konieczne zachowanie <xref:System.Threading.Thread> odwołania do obiektu. Wątek kontynuuje wykonywanie, dopóki procedura wątku się nie zakończy.  
  
 Poniższy przykład kodu tworzy dwa nowe wątki do wywołania wystąpienia i metod statycznych na innym obiekcie.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>Przekazywanie danych do wątków

 W .NET Framework w wersji <xref:System.Threading.ParameterizedThreadStart> 2.0 pełnomocnik zapewnia łatwy sposób przekazywania obiektu zawierającego <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> dane do wątku podczas wywoływania przeciążenia metody. Zobacz <xref:System.Threading.ParameterizedThreadStart> przykład kodu.  
  
 Za <xref:System.Threading.ParameterizedThreadStart> pomocą delegata nie jest bezpieczny sposób przekazywania <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> danych, ponieważ przeciążenie metody akceptuje dowolny obiekt. Alternatywą jest hermetyzowanie procedury wątku i danych w <xref:System.Threading.ThreadStart> klasie pomocnika i użyć delegata do wykonania procedury wątku. W poniższym przykładzie przedstawiono tę technikę:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<xref:System.Threading.ThreadStart> Ani <xref:System.Threading.ParameterizedThreadStart> delegować ma wartość zwracaną, ponieważ nie ma miejsca do zwracania danych z wywołania asynchronicznego. Aby pobrać wyniki metody wątku, można użyć metody wywołania odwróconego, jak pokazano w następnej sekcji.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Pobieranie danych z wątków za pomocą metod wywołania zwrotu

 W poniższym przykładzie przedstawiono metodę wywołania odwróconego, która pobiera dane z wątku. Konstruktor dla klasy, która zawiera dane i metoda wątku akceptuje również delegatreprezentujący metodę wywołania wywołania; przed zakończeniem metody wątku wywołuje delegata wywołania odwróconego.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [Wątków](index.md)
- [Korzystanie z wątków i wątków](using-threads-and-threading.md)
