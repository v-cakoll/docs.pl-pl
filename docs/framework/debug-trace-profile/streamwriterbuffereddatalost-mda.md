---
title: streamWriterBufferedDataLost MDA
description: Zapoznaj się z asystentem debugowania zarządzanego streamWriterBufferedDataLost (MDA), który może zostać aktywowany, jeśli StreamWriter — nie zapisuje ostatnich 1 – 4 KB danych do pliku.
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
ms.openlocfilehash: 0c10ea6bb9dc0aaafa2ac1798696579af7592895
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803485"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="eec2e-103">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="eec2e-103">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="eec2e-104">`streamWriterBufferedDataLost`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy <xref:System.IO.StreamWriter> jest zapisywana w, ale <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter.Close%2A> Metoda lub nie jest następnie wywoływana przed zniszczeniem wystąpienia elementu <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="eec2e-104">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="eec2e-105">Po włączeniu tego MDA środowisko uruchomieniowe określa, czy wszystkie dane buforowane nadal istnieją w <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="eec2e-105">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="eec2e-106">Jeśli istnieją dane buforowane, zdarzenie MDA zostanie aktywowane.</span><span class="sxs-lookup"><span data-stu-id="eec2e-106">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="eec2e-107">Wywoływanie <xref:System.GC.Collect%2A> <xref:System.GC.WaitForPendingFinalizers%2A> metod i może zmusić finalizatory do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="eec2e-107">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="eec2e-108">Finalizatory będą działać w sposób pozornie dowolnie dowolną liczbę razy, a nawet w przypadku zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="eec2e-108">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="eec2e-109">Jawne uruchamianie finalizatorów z włączonym zdarzeniem MDA pomoże bardziej niezawodne odtwarzanie tego typu problemu.</span><span class="sxs-lookup"><span data-stu-id="eec2e-109">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="eec2e-110">Objawy</span><span class="sxs-lookup"><span data-stu-id="eec2e-110">Symptoms</span></span>  
 <span data-ttu-id="eec2e-111">A nie <xref:System.IO.StreamWriter> zapisuje ostatnich 1 – 4 KB danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="eec2e-111">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="eec2e-112">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="eec2e-112">Cause</span></span>  
 <span data-ttu-id="eec2e-113"><xref:System.IO.StreamWriter>Dane buforów wewnętrznie, które wymagają, <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> Aby Metoda lub wywoływana w celu zapisu danych buforowanych w źródłowym magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="eec2e-113">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="eec2e-114">Jeśli <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> nie jest odpowiednio wywoływana, dane buforowane w <xref:System.IO.StreamWriter> wystąpieniu mogą nie być zapisywane zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="eec2e-114">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="eec2e-115">Poniżej przedstawiono przykładowy kod, który ma być przechwytywany przez to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="eec2e-115">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="eec2e-116">Poprzedni kod aktywuje ten obiekt MDA bardziej niezawodnie, jeśli wyrzucanie elementów bezużytecznych zostanie wyzwolone, a następnie zawieszone do momentu zakończenia finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="eec2e-116">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="eec2e-117">Aby śledzić ten typ problemu, można dodać poniższy kod na końcu poprzedniej metody w kompilacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="eec2e-117">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="eec2e-118">Pomoże to w niezawodnym aktywowaniu MDA, ale nie rozwiąże to przyczyny problemu.</span><span class="sxs-lookup"><span data-stu-id="eec2e-118">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="eec2e-119">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="eec2e-119">Resolution</span></span>  
 <span data-ttu-id="eec2e-120">Upewnij się, że jest wywoływana <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> w przypadku <xref:System.IO.StreamWriter> przed zamknięciem aplikacji lub dowolnego bloku kodu, który ma wystąpienie elementu <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="eec2e-120">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="eec2e-121">Jednym z najlepszych mechanizmów do osiągnięcia tego jest utworzenie wystąpienia z `using` blokiem C# ( `Using` w Visual Basic), które zapewni <xref:System.IO.StreamWriter.Dispose%2A> wywołanie metody dla składnika zapisywania, co spowoduje, że wystąpienie jest prawidłowo zamknięte.</span><span class="sxs-lookup"><span data-stu-id="eec2e-121">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="eec2e-122">Poniższy kod przedstawia to samo rozwiązanie przy użyciu polecenia `try/finally` zamiast `using` .</span><span class="sxs-lookup"><span data-stu-id="eec2e-122">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="eec2e-123">Jeśli żadne z tych rozwiązań nie mogą być używane (na przykład, jeśli <xref:System.IO.StreamWriter> jest przechowywany w zmiennej statycznej i nie można łatwo uruchomić kodu na końcu jego okresu istnienia), <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> przed tym problemem należy się odwoływać od momentu jego ostatniego użycia lub ustawienia <xref:System.IO.StreamWriter.AutoFlush%2A> właściwości na `true` przed pierwszym użyciem.</span><span class="sxs-lookup"><span data-stu-id="eec2e-123">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="eec2e-124">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="eec2e-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="eec2e-125">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="eec2e-125">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="eec2e-126">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="eec2e-126">Output</span></span>  
 <span data-ttu-id="eec2e-127">Komunikat informujący o tym, że wystąpiło naruszenie.</span><span class="sxs-lookup"><span data-stu-id="eec2e-127">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="eec2e-128">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="eec2e-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eec2e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eec2e-129">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="eec2e-130">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="eec2e-130">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
