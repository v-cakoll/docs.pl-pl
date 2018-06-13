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
ms.openlocfilehash: 15957ce03925d75021d88bc81d12809c3fe31c2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389944"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="02e8f-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="02e8f-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="02e8f-103">`streamWriterBufferedDataLost` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.IO.StreamWriter> są zapisywane, ale <xref:System.IO.StreamWriter.Flush%2A> lub <xref:System.IO.StreamWriter.Close%2A> metoda nie jest następnie wywoływana przed wystąpienie <xref:System.IO.StreamWriter> zostanie zniszczony.</span><span class="sxs-lookup"><span data-stu-id="02e8f-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="02e8f-104">Po włączeniu to zdarzenie MDA środowiska uruchomieniowego Określa, czy wszystkie buforowane dane nadal istnieje w ramach <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="02e8f-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="02e8f-105">Jeśli istnieje buforowane dane, MDA jest aktywowane.</span><span class="sxs-lookup"><span data-stu-id="02e8f-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="02e8f-106">Wywoływanie <xref:System.GC.Collect%2A> i <xref:System.GC.WaitForPendingFinalizers%2A> metod można wymusić finalizatory do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="02e8f-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="02e8f-107">Finalizatory w przeciwnym razie zostanie uruchomiony w czasie pozornie dowolnego i prawdopodobnie w ogóle na zakończenie procesu.</span><span class="sxs-lookup"><span data-stu-id="02e8f-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="02e8f-108">Jawnie systemie finalizatory to zdarzenie MDA włączone pomogą bardziej niezawodnie odtworzyć ten typ problemu.</span><span class="sxs-lookup"><span data-stu-id="02e8f-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="02e8f-109">Symptomy</span><span class="sxs-lookup"><span data-stu-id="02e8f-109">Symptoms</span></span>  
 <span data-ttu-id="02e8f-110">A <xref:System.IO.StreamWriter> nie zapisuje ostatni 1 – 4 KB danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="02e8f-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="02e8f-111">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="02e8f-111">Cause</span></span>  
 <span data-ttu-id="02e8f-112"><xref:System.IO.StreamWriter> Buforów danych, które wymaga, aby <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> do zapisu buforowane dane odpowiedni magazyn danych można wywołać metody.</span><span class="sxs-lookup"><span data-stu-id="02e8f-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="02e8f-113">Jeśli <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> nie jest odpowiednio wywoływany, dane buforowane w <xref:System.IO.StreamWriter> wystąpienia nie mogą być zapisane, zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="02e8f-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="02e8f-114">Oto przykładowy kod niepoprawnie napisane, że to zdarzenie MDA powinien catch.</span><span class="sxs-lookup"><span data-stu-id="02e8f-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="02e8f-115">Poprzedni kod zostanie aktywowany, to zdarzenie MDA bardziej niezawodnie Jeśli wyrzucania elementów bezużytecznych jest wyzwalane, a następnie wstrzymane do czasu zakończenia finalizatory.</span><span class="sxs-lookup"><span data-stu-id="02e8f-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="02e8f-116">Do śledzenia tego rodzaju problem, można dodać następujący kod na końcu poprzedniego metody kompilacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="02e8f-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="02e8f-117">Dzięki temu można niezawodnie aktywować MDA, ale oczywiście nie ustalić przyczynę problemu.</span><span class="sxs-lookup"><span data-stu-id="02e8f-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="02e8f-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="02e8f-118">Resolution</span></span>  
 <span data-ttu-id="02e8f-119">Upewnij się, że należy wywołać <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> przed zamknięciem aplikacji lub dowolnego blok kodu, który ma wystąpienie <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="02e8f-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="02e8f-120">Z mechanizmów najlepsze na osiągnięcie tego celu jest utworzenia wystąpienia w języku C# `using` bloku (`Using` w języku Visual Basic), który zapewni <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda dla edytora, co powoduje wystąpienie prawidłowo zamknięte.</span><span class="sxs-lookup"><span data-stu-id="02e8f-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="02e8f-121">Poniższy kod przedstawia to samo rozwiązanie przy użyciu `try/finally` zamiast `using`.</span><span class="sxs-lookup"><span data-stu-id="02e8f-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="02e8f-122">Jeśli żadna z tych rozwiązań nie może być używany (na przykład, jeśli <xref:System.IO.StreamWriter> są przechowywane w statycznych zmienną i możesz łatwo nie można uruchomić kod z końcem okresu obowiązywania), wywołując <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po jej ostatniego użycia lub ustawienie <xref:System.IO.StreamWriter.AutoFlush%2A> dla właściwości `true` przed pierwszym użyciem powinien uniknąć tego problemu.</span><span class="sxs-lookup"><span data-stu-id="02e8f-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="02e8f-123">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="02e8f-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="02e8f-124">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="02e8f-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="02e8f-125">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="02e8f-125">Output</span></span>  
 <span data-ttu-id="02e8f-126">Komunikat informujący, że wystąpiło to naruszenie.</span><span class="sxs-lookup"><span data-stu-id="02e8f-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="02e8f-127">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="02e8f-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02e8f-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02e8f-128">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="02e8f-129">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="02e8f-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
