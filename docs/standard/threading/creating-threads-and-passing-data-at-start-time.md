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
ms.openlocfilehash: 96c0c898f103c058c370a0d108568056b1ff8196
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586581"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="76a89-102">Tworzenie wątków i przekazywanie danych w czasie rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="76a89-102">Creating Threads and Passing Data at Start Time</span></span>
<span data-ttu-id="76a89-103">Po utworzeniu procesu systemu operacyjnego, systemu operacyjnego injects wątku wykonania kodu w tego procesu, w tym wszelkie oryginalnego domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="76a89-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="76a89-104">Od tego momentu można tworzyć i zniszczone bez żadnych wątków systemu operacyjnego zawsze tworzona lub zniszczony domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="76a89-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="76a89-105">Jeśli kod wykonywany jest zarządzany kod, a następnie <xref:System.Threading.Thread> obiekt wątku wykonywania w bieżącej domenie aplikacji można uzyskać, pobierając statycznych <xref:System.Threading.Thread.CurrentThread%2A> właściwości typu <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="76a89-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="76a89-106">W tym temacie opisano tworzenie wątków i omówiono alternatyw przekazywania danych do procedury wątku.</span><span class="sxs-lookup"><span data-stu-id="76a89-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="76a89-107">Tworzenie wątku</span><span class="sxs-lookup"><span data-stu-id="76a89-107">Creating a Thread</span></span>  
 <span data-ttu-id="76a89-108">Tworzenie nowego <xref:System.Threading.Thread> obiektu tworzy nowego wątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="76a89-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="76a89-109"><xref:System.Threading.Thread> Klasa ma konstruktorów przyjmujących <xref:System.Threading.ThreadStart> delegować lub <xref:System.Threading.ParameterizedThreadStart> delegata; delegat opakowuje wywoływanej przez nowego wątku po wywołaniu metody <xref:System.Threading.Thread.Start%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="76a89-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="76a89-110">Wywoływanie <xref:System.Threading.Thread.Start%2A> więcej niż raz spowoduje, że <xref:System.Threading.ThreadStateException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="76a89-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="76a89-111"><xref:System.Threading.Thread.Start%2A> Metoda zwraca natychmiast, często przed nowego wątku rzeczywiście została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="76a89-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="76a89-112">Można użyć <xref:System.Threading.Thread.ThreadState%2A> i <xref:System.Threading.Thread.IsAlive%2A> właściwości, aby określić stan wątku w danym momencie, ale te właściwości nie mogą być używane do synchronizacji działania wątków.</span><span class="sxs-lookup"><span data-stu-id="76a89-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76a89-113">Po uruchomieniu wątku nie jest konieczne do zachowania odwołanie do <xref:System.Threading.Thread> obiektu.</span><span class="sxs-lookup"><span data-stu-id="76a89-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="76a89-114">Wątek w dalszym ciągu wykonania do czasu zakończenia procedury wątku.</span><span class="sxs-lookup"><span data-stu-id="76a89-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="76a89-115">Poniższy przykład kodu tworzy dwa nowe wątki wywołanie wystąpienia i metod statycznych na inny obiekt.</span><span class="sxs-lookup"><span data-stu-id="76a89-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a><span data-ttu-id="76a89-116">Przekazywanie danych do wątków i pobierania danych z wątków</span><span class="sxs-lookup"><span data-stu-id="76a89-116">Passing Data to Threads and Retrieving Data from Threads</span></span>  
 <span data-ttu-id="76a89-117">W programie .NET Framework w wersji 2.0 <xref:System.Threading.ParameterizedThreadStart> delegowanie umożliwia łatwe do przekazania obiekt zawierający dane do wątku po wywołaniu <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenie metody.</span><span class="sxs-lookup"><span data-stu-id="76a89-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="76a89-118">Zobacz <xref:System.Threading.ParameterizedThreadStart> dla przykładowego kodu.</span><span class="sxs-lookup"><span data-stu-id="76a89-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="76a89-119">Przy użyciu <xref:System.Threading.ParameterizedThreadStart> delegat nie jest bezpieczny sposób przekazywania danych, ponieważ <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> przeciążenie metody akceptuje dowolny obiekt.</span><span class="sxs-lookup"><span data-stu-id="76a89-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="76a89-120">Alternatywą jest Hermetyzowanie procedury wątku i danych w klasie pomocy i użyj <xref:System.Threading.ThreadStart> delegata do wykonywania procedury wątku.</span><span class="sxs-lookup"><span data-stu-id="76a89-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="76a89-121">Ta technika przedstawiono w przykładach dwóch kodu, które należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="76a89-121">This technique is shown in the two code examples that follow.</span></span>  
  
 <span data-ttu-id="76a89-122">Oba te obiekty delegowane ma wartość zwracaną, ponieważ nie istnieje żadne miejsce do zwrócić dane z wywołanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="76a89-122">Neither of these delegates has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="76a89-123">Można pobrać wyników metody wątku, używając metody wywołania zwrotnego, jak pokazano w drugim przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="76a89-123">To retrieve the results of a thread method, you can use a callback method, as demonstrated in the second code example.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a><span data-ttu-id="76a89-124">Pobieranie danych z metody wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="76a89-124">Retrieving Data with Callback Methods</span></span>  
 <span data-ttu-id="76a89-125">W poniższym przykładzie pokazano metodę wywołania zwrotnego, która pobiera dane z wątku.</span><span class="sxs-lookup"><span data-stu-id="76a89-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="76a89-126">Konstruktor klasy, która zawiera dane, a także metoda wątku również akceptuje delegata reprezentującego metodę wywołania zwrotnego; przed zakończeniem metody wątku wywołuje delegata wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="76a89-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="76a89-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76a89-127">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="76a89-128">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="76a89-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="76a89-129">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="76a89-129">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
