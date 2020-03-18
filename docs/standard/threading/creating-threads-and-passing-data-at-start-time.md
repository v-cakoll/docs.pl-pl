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
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="062f4-102">Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="062f4-102">Creating threads and passing data at start time</span></span>

<span data-ttu-id="062f4-103">Po utworzeniu procesu systemu operacyjnego system operacyjny wstrzykuje wątek do wykonania kodu w tym procesie, w tym dowolnej oryginalnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="062f4-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="062f4-104">Od tego momentu domeny aplikacji mogą być tworzone i niszczone bez żadnych wątków systemu operacyjnego muszą być tworzone lub niszczone.</span><span class="sxs-lookup"><span data-stu-id="062f4-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="062f4-105">Jeśli wykonywany kod jest kodem <xref:System.Threading.Thread> zarządzanym, obiekt dla wątku wykonywanego w bieżącej <xref:System.Threading.Thread.CurrentThread%2A> domenie aplikacji można uzyskać, pobierając właściwość statyczną typu <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="062f4-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="062f4-106">W tym temacie opisano tworzenie wątku i omówiono alternatywy przekazywania danych do procedury wątku.</span><span class="sxs-lookup"><span data-stu-id="062f4-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="062f4-107">Tworzenie wątku</span><span class="sxs-lookup"><span data-stu-id="062f4-107">Creating a thread</span></span>

 <span data-ttu-id="062f4-108">Tworzenie nowego <xref:System.Threading.Thread> obiektu tworzy nowy wątek zarządzany.</span><span class="sxs-lookup"><span data-stu-id="062f4-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="062f4-109">Klasa <xref:System.Threading.Thread> ma konstruktorów, <xref:System.Threading.ThreadStart> które przyjmują <xref:System.Threading.ParameterizedThreadStart> delegata lub delegata; delegat owija metodę, która jest wywoływana przez nowy <xref:System.Threading.Thread.Start%2A> wątek podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="062f4-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="062f4-110">Wywołanie <xref:System.Threading.Thread.Start%2A> więcej niż <xref:System.Threading.ThreadStateException> jeden raz powoduje, że zostanie wyrzucony.</span><span class="sxs-lookup"><span data-stu-id="062f4-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="062f4-111">Metoda <xref:System.Threading.Thread.Start%2A> zwraca natychmiast, często przed rozpoczęciem nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="062f4-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="062f4-112">Można użyć <xref:System.Threading.Thread.ThreadState%2A> i <xref:System.Threading.Thread.IsAlive%2A> właściwości, aby określić stan wątku w dowolnym momencie, ale te właściwości nigdy nie powinny być używane do synchronizowania działań wątków.</span><span class="sxs-lookup"><span data-stu-id="062f4-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="062f4-113">Po uruchomieniu wątku nie jest konieczne zachowanie <xref:System.Threading.Thread> odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="062f4-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="062f4-114">Wątek kontynuuje wykonywanie, dopóki procedura wątku się nie zakończy.</span><span class="sxs-lookup"><span data-stu-id="062f4-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="062f4-115">Poniższy przykład kodu tworzy dwa nowe wątki do wywołania wystąpienia i metod statycznych na innym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="062f4-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="062f4-116">Przekazywanie danych do wątków</span><span class="sxs-lookup"><span data-stu-id="062f4-116">Passing data to threads</span></span>

 <span data-ttu-id="062f4-117">W .NET Framework w wersji <xref:System.Threading.ParameterizedThreadStart> 2.0 pełnomocnik zapewnia łatwy sposób przekazywania obiektu zawierającego <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> dane do wątku podczas wywoływania przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="062f4-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="062f4-118">Zobacz <xref:System.Threading.ParameterizedThreadStart> przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="062f4-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="062f4-119">Za <xref:System.Threading.ParameterizedThreadStart> pomocą delegata nie jest bezpieczny sposób przekazywania <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> danych, ponieważ przeciążenie metody akceptuje dowolny obiekt.</span><span class="sxs-lookup"><span data-stu-id="062f4-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="062f4-120">Alternatywą jest hermetyzowanie procedury wątku i danych w <xref:System.Threading.ThreadStart> klasie pomocnika i użyć delegata do wykonania procedury wątku.</span><span class="sxs-lookup"><span data-stu-id="062f4-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="062f4-121">W poniższym przykładzie przedstawiono tę technikę:</span><span class="sxs-lookup"><span data-stu-id="062f4-121">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="062f4-122"><xref:System.Threading.ThreadStart> Ani <xref:System.Threading.ParameterizedThreadStart> delegować ma wartość zwracaną, ponieważ nie ma miejsca do zwracania danych z wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="062f4-122">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="062f4-123">Aby pobrać wyniki metody wątku, można użyć metody wywołania odwróconego, jak pokazano w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="062f4-123">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="062f4-124">Pobieranie danych z wątków za pomocą metod wywołania zwrotu</span><span class="sxs-lookup"><span data-stu-id="062f4-124">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="062f4-125">W poniższym przykładzie przedstawiono metodę wywołania odwróconego, która pobiera dane z wątku.</span><span class="sxs-lookup"><span data-stu-id="062f4-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="062f4-126">Konstruktor dla klasy, która zawiera dane i metoda wątku akceptuje również delegatreprezentujący metodę wywołania wywołania; przed zakończeniem metody wątku wywołuje delegata wywołania odwróconego.</span><span class="sxs-lookup"><span data-stu-id="062f4-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="062f4-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="062f4-127">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="062f4-128">Wątków</span><span class="sxs-lookup"><span data-stu-id="062f4-128">Threading</span></span>](index.md)
- [<span data-ttu-id="062f4-129">Korzystanie z wątków i wątków</span><span class="sxs-lookup"><span data-stu-id="062f4-129">Using Threads and Threading</span></span>](using-threads-and-threading.md)
