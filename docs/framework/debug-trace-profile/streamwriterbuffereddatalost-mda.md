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
ms.openlocfilehash: 18b2a5a95756ed125d26b2846c0b1ddc320463ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181741"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="87059-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="87059-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="87059-103">Asystent `streamWriterBufferedDataLost` debugowania zarządzanego (MDA) jest <xref:System.IO.StreamWriter> aktywowany, gdy <xref:System.IO.StreamWriter.Flush%2A> jest <xref:System.IO.StreamWriter.Close%2A> zapisywany, ale lub metoda <xref:System.IO.StreamWriter> nie jest następnie wywoływana przed wystąpieniem jest niszczony.</span><span class="sxs-lookup"><span data-stu-id="87059-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="87059-104">Gdy to mda jest włączone, środowisko wykonawcze określa, czy buforowane dane nadal istnieją w ramach <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="87059-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="87059-105">Jeśli istnieją buforowane dane, mda jest aktywowany.</span><span class="sxs-lookup"><span data-stu-id="87059-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="87059-106">Wywołanie <xref:System.GC.Collect%2A> <xref:System.GC.WaitForPendingFinalizers%2A> i metody może wymusić finalizatorów do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="87059-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="87059-107">Finalizatory będą w przeciwnym razie uruchamiane w pozornie arbitralnych czasach i być może w ogóle nie przy wyjściu z procesu.</span><span class="sxs-lookup"><span data-stu-id="87059-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="87059-108">Jawnie uruchomione finalizatory z włączoną funkcją MDA pomogą bardziej niezawodnie odtworzyć ten typ problemu.</span><span class="sxs-lookup"><span data-stu-id="87059-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="87059-109">Objawy</span><span class="sxs-lookup"><span data-stu-id="87059-109">Symptoms</span></span>  
 <span data-ttu-id="87059-110">A <xref:System.IO.StreamWriter> nie zapisuje ostatnich 1–4 KB danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="87059-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="87059-111">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="87059-111">Cause</span></span>  
 <span data-ttu-id="87059-112">Bufory <xref:System.IO.StreamWriter> danych wewnętrznie, co wymaga, aby <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> metoda zostanie wywołana do zapisu buforowanych danych do magazynu danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="87059-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="87059-113">Jeśli <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> lub nie jest odpowiednio wywoływane, <xref:System.IO.StreamWriter> dane buforowane w wystąpieniu może nie być zapisywane zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="87059-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="87059-114">Poniżej przedstawiono przykład źle napisanego kodu, który ten MDA powinien złapać.</span><span class="sxs-lookup"><span data-stu-id="87059-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="87059-115">Poprzedni kod aktywuje ten MDA bardziej niezawodnie, jeśli wyrzucanie elementów bezużytecznych jest wyzwalane, a następnie zawieszone do zakończenia finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="87059-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="87059-116">Aby wyśledzić ten typ problemu, można dodać następujący kod na końcu poprzedniej metody w kompilacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="87059-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="87059-117">Pomoże to niezawodnie aktywować MDA, ale oczywiście nie naprawi przyczyny problemu.</span><span class="sxs-lookup"><span data-stu-id="87059-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="87059-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="87059-118">Resolution</span></span>  
 <span data-ttu-id="87059-119">Upewnij się, <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> że <xref:System.IO.StreamWriter> dzwonisz lub na przed zamknięciem aplikacji <xref:System.IO.StreamWriter>lub dowolnego bloku kodu, który ma wystąpienie .</span><span class="sxs-lookup"><span data-stu-id="87059-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="87059-120">Jednym z najlepszych mechanizmów do osiągnięcia tego jest `using` tworzenie`Using` wystąpienia z bloku C# <xref:System.IO.StreamWriter.Dispose%2A> (w języku Visual Basic), który zapewni, że metoda modułu zapisującego jest wywoływana, w wyniku wystąpienia jest poprawnie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="87059-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="87059-121">Poniższy kod przedstawia to `try/finally` samo rozwiązanie, używając zamiast `using`.</span><span class="sxs-lookup"><span data-stu-id="87059-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="87059-122">Jeśli żadne z tych rozwiązań nie może być <xref:System.IO.StreamWriter> używany (na przykład, jeśli jest przechowywany w zmiennej statycznej <xref:System.IO.StreamWriter.Flush%2A> i <xref:System.IO.StreamWriter> nie można łatwo <xref:System.IO.StreamWriter.AutoFlush%2A> uruchomić `true` kod na koniec jego istnienia), a następnie wywołanie po jego ostatnim użyciu lub ustawienie właściwości przed pierwszym użyciem należy uniknąć tego problemu.</span><span class="sxs-lookup"><span data-stu-id="87059-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="87059-123">Wpływ na czas działania</span><span class="sxs-lookup"><span data-stu-id="87059-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="87059-124">To narzędzie MDA nie ma wpływu na środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="87059-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="87059-125">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="87059-125">Output</span></span>  
 <span data-ttu-id="87059-126">Komunikat informujący, że wystąpiło to naruszenie.</span><span class="sxs-lookup"><span data-stu-id="87059-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="87059-127">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="87059-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87059-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87059-128">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="87059-129">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="87059-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
