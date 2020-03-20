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
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
Asystent `streamWriterBufferedDataLost` debugowania zarządzanego (MDA) jest <xref:System.IO.StreamWriter> aktywowany, gdy <xref:System.IO.StreamWriter.Flush%2A> jest <xref:System.IO.StreamWriter.Close%2A> zapisywany, ale lub metoda <xref:System.IO.StreamWriter> nie jest następnie wywoływana przed wystąpieniem jest niszczony. Gdy to mda jest włączone, środowisko wykonawcze określa, czy buforowane dane nadal istnieją w ramach <xref:System.IO.StreamWriter>. Jeśli istnieją buforowane dane, mda jest aktywowany. Wywołanie <xref:System.GC.Collect%2A> <xref:System.GC.WaitForPendingFinalizers%2A> i metody może wymusić finalizatorów do uruchomienia. Finalizatory będą w przeciwnym razie uruchamiane w pozornie arbitralnych czasach i być może w ogóle nie przy wyjściu z procesu. Jawnie uruchomione finalizatory z włączoną funkcją MDA pomogą bardziej niezawodnie odtworzyć ten typ problemu.  
  
## <a name="symptoms"></a>Objawy  
 A <xref:System.IO.StreamWriter> nie zapisuje ostatnich 1–4 KB danych do pliku.  
  
## <a name="cause"></a>Przyczyna  
 Bufory <xref:System.IO.StreamWriter> danych wewnętrznie, co wymaga, aby <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> metoda zostanie wywołana do zapisu buforowanych danych do magazynu danych źródłowych. Jeśli <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> lub nie jest odpowiednio wywoływane, <xref:System.IO.StreamWriter> dane buforowane w wystąpieniu może nie być zapisywane zgodnie z oczekiwaniami.  
  
 Poniżej przedstawiono przykład źle napisanego kodu, który ten MDA powinien złapać.  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Poprzedni kod aktywuje ten MDA bardziej niezawodnie, jeśli wyrzucanie elementów bezużytecznych jest wyzwalane, a następnie zawieszone do zakończenia finalizatorów. Aby wyśledzić ten typ problemu, można dodać następujący kod na końcu poprzedniej metody w kompilacji debugowania. Pomoże to niezawodnie aktywować MDA, ale oczywiście nie naprawi przyczyny problemu.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> że <xref:System.IO.StreamWriter> dzwonisz lub na przed zamknięciem aplikacji <xref:System.IO.StreamWriter>lub dowolnego bloku kodu, który ma wystąpienie . Jednym z najlepszych mechanizmów do osiągnięcia tego jest `using` tworzenie`Using` wystąpienia z bloku C# <xref:System.IO.StreamWriter.Dispose%2A> (w języku Visual Basic), który zapewni, że metoda modułu zapisującego jest wywoływana, w wyniku wystąpienia jest poprawnie zamknięty.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 Poniższy kod przedstawia to `try/finally` samo rozwiązanie, używając zamiast `using`.  
  
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
  
 Jeśli żadne z tych rozwiązań nie może być <xref:System.IO.StreamWriter> używany (na przykład, jeśli jest przechowywany w zmiennej statycznej <xref:System.IO.StreamWriter.Flush%2A> i <xref:System.IO.StreamWriter> nie można łatwo <xref:System.IO.StreamWriter.AutoFlush%2A> uruchomić `true` kod na koniec jego istnienia), a następnie wywołanie po jego ostatnim użyciu lub ustawienie właściwości przed pierwszym użyciem należy uniknąć tego problemu.  
  
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
  
## <a name="effect-on-the-runtime"></a>Wpływ na czas działania  
 To narzędzie MDA nie ma wpływu na środowisko wykonawcze.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informujący, że wystąpiło to naruszenie.  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
