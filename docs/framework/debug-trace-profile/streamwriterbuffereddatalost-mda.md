---
title: streamWriterBufferedDataLost MDA
ms.date: 03/30/2017
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b35e6ab4de699126b4b3b5f74d7a9a8dacfa4a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117394"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="2acc8-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="2acc8-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="2acc8-103">`streamWriterBufferedDataLost` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po <xref:System.IO.StreamWriter> są zapisywane, ale <xref:System.IO.StreamWriter.Flush%2A> lub <xref:System.IO.StreamWriter.Close%2A> metoda nie jest później wywoływana przed wystąpieniem programu <xref:System.IO.StreamWriter> zostanie zniszczony.</span><span class="sxs-lookup"><span data-stu-id="2acc8-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="2acc8-104">Gdy to zdarzenie MDA jest włączona, środowisko wykonawcze określa, czy wszystkie buforowane dane nadal istnieje w ramach <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="2acc8-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="2acc8-105">Jeśli istnieje buforowane dane, to zdarzenie MDA jest aktywowane.</span><span class="sxs-lookup"><span data-stu-id="2acc8-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="2acc8-106">Wywoływanie <xref:System.GC.Collect%2A> i <xref:System.GC.WaitForPendingFinalizers%2A> metod można wymusić finalizatory do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="2acc8-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="2acc8-107">Finalizatory w przeciwnym razie zostanie uruchomiony w czasie pozornie dowolnego i prawdopodobnie w ogóle nie będzie na zakończenie procesu.</span><span class="sxs-lookup"><span data-stu-id="2acc8-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="2acc8-108">Jawnie uruchamianie finalizatorów z tego MDA włączona ma na celu bardziej niezawodnie odtworzyć ten typ problemu.</span><span class="sxs-lookup"><span data-stu-id="2acc8-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2acc8-109">Symptomy</span><span class="sxs-lookup"><span data-stu-id="2acc8-109">Symptoms</span></span>  
 <span data-ttu-id="2acc8-110">Element <xref:System.IO.StreamWriter> nie zapisuje ostatni 1 – 4 KB danych w pliku.</span><span class="sxs-lookup"><span data-stu-id="2acc8-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2acc8-111">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="2acc8-111">Cause</span></span>  
 <span data-ttu-id="2acc8-112"><xref:System.IO.StreamWriter> Buforuje dane, które wymaga, aby <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> metoda jest wywoływana w celu zapisania buforowane dane do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="2acc8-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="2acc8-113">Jeśli <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> nie jest prawidłowo wywoływany, danych, lecz buforowane w <xref:System.IO.StreamWriter> wystąpienia nie może być zapisana, zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="2acc8-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="2acc8-114">Oto przykład źle kod, który należy przechwytywać to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="2acc8-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="2acc8-115">Poprzedni kod będzie aktywuje tego zdarzenia MDA bardziej niezawodne, gdy wyrzucanie elementów bezużytecznych jest wyzwalane, a następnie wstrzymane do czasu zakończenia finalizatory.</span><span class="sxs-lookup"><span data-stu-id="2acc8-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="2acc8-116">Do śledzenia tego rodzaju problem, można dodać następujący kod na końcu poprzedniego metody do kompilacji debugowanej.</span><span class="sxs-lookup"><span data-stu-id="2acc8-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="2acc8-117">Pomoże to niezawodne aktywować MDA, ale oczywiście nie ustalić przyczynę problemu.</span><span class="sxs-lookup"><span data-stu-id="2acc8-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="2acc8-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="2acc8-118">Resolution</span></span>  
 <span data-ttu-id="2acc8-119">Upewnij się, należy wywołać <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> przed zamknięciem aplikacji lub dowolnym blok kodu, który zawiera wystąpienie <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="2acc8-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="2acc8-120">Jedną z najlepszych mechanizmy służące osiągnięciu tego celu jest utworzenie wystąpienia z C# `using` bloku (`Using` w języku Visual Basic), który zapewni <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda dla edytora, co w przypadku poprawnie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="2acc8-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="2acc8-121">Poniższy kod przedstawia tego samego rozwiązania przy użyciu `try/finally` zamiast `using`.</span><span class="sxs-lookup"><span data-stu-id="2acc8-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
```csharp
StreamWriter sw;  
try   
{  
    sw = new StreamWriter("file.txt"));  
    sw.WriteLine("Data");  
}  
finally   
{  
    if (sw != null)  
        sw.Close();  
}  
```  
  
 <span data-ttu-id="2acc8-122">Jeśli żadna z tych rozwiązań nie może być używana (na przykład, jeśli <xref:System.IO.StreamWriter> są przechowywane w statycznych zmienną i możesz łatwo nie można uruchomić kod na końcu okresu jego istnienia), następnie wywoływania <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po jej ostatniego użycia lub ustawienie <xref:System.IO.StreamWriter.AutoFlush%2A> Właściwość `true` przed pierwszym użyciem należy unikać tego problemu.</span><span class="sxs-lookup"><span data-stu-id="2acc8-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
```csharp
private static StreamWriter log;  
// static class constructor.  
static WriteToFile()   
{  
    StreamWriter sw = new StreamWriter("log.txt");  
    sw.AutoFlush = true;  
  
    // Publish the StreamWriter for other threads.  
    log = sw;  
}  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2acc8-123">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2acc8-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="2acc8-124">To zdarzenie MDA nie ma wpływu na środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2acc8-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2acc8-125">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="2acc8-125">Output</span></span>  
 <span data-ttu-id="2acc8-126">Komunikat wskazujący, że to naruszenie wystąpił.</span><span class="sxs-lookup"><span data-stu-id="2acc8-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2acc8-127">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="2acc8-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2acc8-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2acc8-128">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="2acc8-129">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="2acc8-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
