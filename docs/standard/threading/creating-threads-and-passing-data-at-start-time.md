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
ms.openlocfilehash: 028f8b978a7809fa9ae4710ab85d7dc84e7b04fc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878626"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="7a1b3-102">Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="7a1b3-102">Creating threads and passing data at start time</span></span>

<span data-ttu-id="7a1b3-103">Po utworzeniu procesu systemu operacyjnego, system operacyjny wprowadza wątku w celu wykonania kodu w tym procesie, w tym wszelkie oryginalną domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="7a1b3-104">Od tego momentu można tworzyć i zniszczone bez żadnych wątków systemu operacyjnego, niekoniecznie są utworzone lub zniszczone domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="7a1b3-105">Jeśli wykonywany kod jest zarządzany kod, a następnie <xref:System.Threading.Thread> obiekt wykonywany wątek w bieżącej domenie aplikacji można uzyskać przez pobranie statycznej <xref:System.Threading.Thread.CurrentThread%2A> właściwości typu <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="7a1b3-106">W tym temacie opisano tworzenie wątków i omówiono alternatywy przekazywania danych do procedury wątku.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="7a1b3-107">Tworzenie wątku</span><span class="sxs-lookup"><span data-stu-id="7a1b3-107">Creating a thread</span></span>

 <span data-ttu-id="7a1b3-108">Tworzenie nowego <xref:System.Threading.Thread> obiektu tworzy nowy wątek.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="7a1b3-109"><xref:System.Threading.Thread> Klasa ma konstruktory, które przyjmują <xref:System.Threading.ThreadStart> delegować lub <xref:System.Threading.ParameterizedThreadStart> delegować; delegat opakowuje metodę, która jest wywoływana przez nowy wątek, gdy wywołujesz <xref:System.Threading.Thread.Start%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="7a1b3-110">Wywoływanie <xref:System.Threading.Thread.Start%2A> więcej niż jeden raz powoduje, że <xref:System.Threading.ThreadStateException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="7a1b3-111"><xref:System.Threading.Thread.Start%2A> Metoda zwraca natychmiast, często przed faktycznie został uruchomiony nowy wątek.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="7a1b3-112">Możesz użyć <xref:System.Threading.Thread.ThreadState%2A> i <xref:System.Threading.Thread.IsAlive%2A> właściwości, aby określić stan wątku w danym momencie, ale te właściwości nie mogą być używane do synchronizowania działania wątków.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a1b3-113">Po uruchomieniu wątek nie jest konieczne do przechowywania odwołań do <xref:System.Threading.Thread> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="7a1b3-114">Wątek w dalszym ciągu wykonania do czasu zakończenia procedury wątku.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="7a1b3-115">Poniższy przykład kodu tworzy dwa nowe wątki wywołanie wystąpienia i metody statyczne na inny obiekt.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="7a1b3-116">Przekazywanie danych do wątków</span><span class="sxs-lookup"><span data-stu-id="7a1b3-116">Passing data to threads</span></span>

 <span data-ttu-id="7a1b3-117">W .NET Framework w wersji 2.0 <xref:System.Threading.ParameterizedThreadStart> delegata zapewnia łatwy sposób przekazać obiekt zawierający dane do wątku, po wywołaniu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenie metody.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="7a1b3-118">Zobacz <xref:System.Threading.ParameterizedThreadStart> dla przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="7a1b3-119">Za pomocą <xref:System.Threading.ParameterizedThreadStart> delegat nie jest bezpieczny sposób przekazywania danych, ponieważ <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenie metody akceptuje dowolny obiekt.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="7a1b3-120">Alternatywą jest hermetyzacji procedury wątku i dane w klasie pomocy i użyj <xref:System.Threading.ThreadStart> delegata do wykonania procedury wątku.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="7a1b3-121">Poniższy przykład pokazuje tej techniki:</span><span class="sxs-lookup"><span data-stu-id="7a1b3-121">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="7a1b3-122">Ani <xref:System.Threading.ThreadStart> ani <xref:System.Threading.ParameterizedThreadStart> pełnomocnik ma wartość zwracaną, ponieważ nie istnieje żadne miejsce do zwracania danych z wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-122">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="7a1b3-123">Do pobierania wyników metoda wątku, można użyć metody wywołania zwrotnego, jak pokazano w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-123">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="7a1b3-124">Pobieranie danych z wątków, z metodami wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="7a1b3-124">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="7a1b3-125">W poniższym przykładzie pokazano metodę wywołania zwrotnego, która pobiera dane z wątku.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="7a1b3-126">Konstruktor dla klasy, która zawiera dane, a także metoda wątku akceptuje także obiekt delegowany reprezentujący metodę wywołania zwrotnego; przed zakończeniem metoda wątek wywołuje delegata wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="7a1b3-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7a1b3-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a1b3-127">See also</span></span>

- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadStart>  
- <xref:System.Threading.ParameterizedThreadStart>  
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="7a1b3-128">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="7a1b3-128">Threading</span></span>](index.md)  
- [<span data-ttu-id="7a1b3-129">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="7a1b3-129">Using Threads and Threading</span></span>](using-threads-and-threading.md)
