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
ms.openlocfilehash: c3dcdd329318d48efa203d2b9dcbfe3501d94b3e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052271"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="64aa5-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="64aa5-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="64aa5-103"><xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> Asystent debugowania zarządzanego(MDA)jestuaktywniany,gdyjestzapisywanaw,alemetodalubniejestnastępniewywoływanaprzedzniszczeniemwystąpieniaelementu.`streamWriterBufferedDataLost`</span><span class="sxs-lookup"><span data-stu-id="64aa5-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="64aa5-104">Po włączeniu tego MDA środowisko uruchomieniowe określa, czy wszystkie dane buforowane nadal istnieją w <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="64aa5-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="64aa5-105">Jeśli istnieją dane buforowane, zdarzenie MDA zostanie aktywowane.</span><span class="sxs-lookup"><span data-stu-id="64aa5-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="64aa5-106">Wywoływanie metod <xref:System.GC.WaitForPendingFinalizers%2A>imoże zmusić finalizatory do uruchomienia. <xref:System.GC.Collect%2A></span><span class="sxs-lookup"><span data-stu-id="64aa5-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="64aa5-107">Finalizatory będą działać w sposób pozornie dowolnie dowolną liczbę razy, a nawet w przypadku zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="64aa5-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="64aa5-108">Jawne uruchamianie finalizatorów z włączonym zdarzeniem MDA pomoże bardziej niezawodne odtwarzanie tego typu problemu.</span><span class="sxs-lookup"><span data-stu-id="64aa5-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="64aa5-109">Symptomy</span><span class="sxs-lookup"><span data-stu-id="64aa5-109">Symptoms</span></span>  
 <span data-ttu-id="64aa5-110">A <xref:System.IO.StreamWriter> nie zapisuje ostatnich 1 – 4 KB danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="64aa5-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="64aa5-111">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="64aa5-111">Cause</span></span>  
 <span data-ttu-id="64aa5-112">Dane buforów wewnętrznie, które wymagają <xref:System.IO.StreamWriter.Close%2A> , aby Metoda <xref:System.IO.StreamWriter.Flush%2A> lub wywoływana w celu zapisu danych buforowanych w źródłowym magazynie danych. <xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="64aa5-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="64aa5-113">Jeśli <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter> lub <xref:System.IO.StreamWriter.Flush%2A> nie jest odpowiednio wywoływana, dane buforowane w wystąpieniu mogą nie być zapisywane zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="64aa5-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="64aa5-114">Poniżej przedstawiono przykładowy kod, który ma być przechwytywany przez to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="64aa5-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="64aa5-115">Poprzedni kod aktywuje ten obiekt MDA bardziej niezawodnie, jeśli wyrzucanie elementów bezużytecznych zostanie wyzwolone, a następnie zawieszone do momentu zakończenia finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="64aa5-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="64aa5-116">Aby śledzić ten typ problemu, można dodać poniższy kod na końcu poprzedniej metody w kompilacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="64aa5-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="64aa5-117">Pomoże to w niezawodnym aktywowaniu MDA, ale nie rozwiąże to przyczyny problemu.</span><span class="sxs-lookup"><span data-stu-id="64aa5-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="64aa5-118">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="64aa5-118">Resolution</span></span>  
 <span data-ttu-id="64aa5-119">Upewnij się, że <xref:System.IO.StreamWriter.Close%2A> jest <xref:System.IO.StreamWriter.Flush%2A> wywoływana lub <xref:System.IO.StreamWriter> w przypadku przed zamknięciem aplikacji lub dowolnego bloku kodu, który ma wystąpienie <xref:System.IO.StreamWriter>elementu.</span><span class="sxs-lookup"><span data-stu-id="64aa5-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="64aa5-120">Jednym z najlepszych mechanizmów do osiągnięcia tego jest utworzenie wystąpienia z C# `using` blokiem (`Using` w <xref:System.IO.StreamWriter.Dispose%2A> Visual Basic), które zapewni wywołanie metody dla składnika zapisywania, co spowoduje, że wystąpienie jest prawidłowo zamknięte.</span><span class="sxs-lookup"><span data-stu-id="64aa5-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="64aa5-121">Poniższy kod przedstawia to samo rozwiązanie przy użyciu `try/finally` polecenia `using`zamiast.</span><span class="sxs-lookup"><span data-stu-id="64aa5-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="64aa5-122">Jeśli żadne z tych rozwiązań nie mogą być używane (na przykład, jeśli <xref:System.IO.StreamWriter> jest przechowywany w zmiennej statycznej i nie można łatwo uruchomić kodu na końcu jego okresu istnienia), nastąpi wywołanie <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Flush%2A> po ostatnim użyciu lub ustawienie <xref:System.IO.StreamWriter.AutoFlush%2A> `true` przed pierwszym użyciem należy unikać tego problemu.</span><span class="sxs-lookup"><span data-stu-id="64aa5-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="64aa5-123">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="64aa5-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="64aa5-124">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="64aa5-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="64aa5-125">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="64aa5-125">Output</span></span>  
 <span data-ttu-id="64aa5-126">Komunikat informujący o tym, że wystąpiło naruszenie.</span><span class="sxs-lookup"><span data-stu-id="64aa5-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="64aa5-127">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="64aa5-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64aa5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64aa5-128">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="64aa5-129">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="64aa5-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
