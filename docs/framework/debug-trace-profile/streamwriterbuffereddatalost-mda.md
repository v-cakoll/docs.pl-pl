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
ms.openlocfilehash: 82940b40b302f4a928547f2e6a0c285727e13934
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216103"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
Asystent debugowania zarządzanego `streamWriterBufferedDataLost` (MDA) jest uaktywniany, gdy <xref:System.IO.StreamWriter> jest zapisywana w, ale metoda <xref:System.IO.StreamWriter.Flush%2A> lub <xref:System.IO.StreamWriter.Close%2A> nie jest następnie wywoływana przed zniszczeniem wystąpienia <xref:System.IO.StreamWriter>. Po włączeniu tego MDA środowisko uruchomieniowe określa, czy wszystkie dane buforowane nadal istnieją w <xref:System.IO.StreamWriter>. Jeśli istnieją dane buforowane, zdarzenie MDA zostanie aktywowane. Wywoływanie metod <xref:System.GC.Collect%2A> i <xref:System.GC.WaitForPendingFinalizers%2A> może wymusić uruchomienie finalizatorów. Finalizatory będą działać w sposób pozornie dowolnie dowolną liczbę razy, a nawet w przypadku zakończenia procesu. Jawne uruchamianie finalizatorów z włączonym zdarzeniem MDA pomoże bardziej niezawodne odtwarzanie tego typu problemu.  
  
## <a name="symptoms"></a>Objawy  
 <xref:System.IO.StreamWriter> nie zapisuje ostatnich 1 – 4 KB danych do pliku.  
  
## <a name="cause"></a>Przyczyna  
 <xref:System.IO.StreamWriter> buforuje dane wewnętrznie, co wymaga wywołania metody <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> w celu zapisania danych buforowanych w źródłowym magazynie danych. Jeśli <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> nie jest odpowiednio wywoływana, dane buforowane w wystąpieniu <xref:System.IO.StreamWriter> mogą nie być zapisywane zgodnie z oczekiwaniami.  
  
 Poniżej przedstawiono przykładowy kod, który ma być przechwytywany przez to zdarzenie MDA.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Poprzedni kod aktywuje ten obiekt MDA bardziej niezawodnie, jeśli wyrzucanie elementów bezużytecznych zostanie wyzwolone, a następnie zawieszone do momentu zakończenia finalizatorów. Aby śledzić ten typ problemu, można dodać poniższy kod na końcu poprzedniej metody w kompilacji debugowania. Pomoże to w niezawodnym aktywowaniu MDA, ale nie rozwiąże to przyczyny problemu.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Rozwiązanie  
 Przed zamknięciem aplikacji lub dowolnego bloku kodu, który ma wystąpienie <xref:System.IO.StreamWriter>, należy się upewnić, że jest wywoływana <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Flush%2A>. Jednym z najlepszych mechanizmów do osiągnięcia tego jest utworzenie wystąpienia z blokiem C# `using` (`Using` w Visual Basic), które zapewni wywołanie metody <xref:System.IO.StreamWriter.Dispose%2A> dla składnika zapisywania, co spowoduje, że wystąpienie jest prawidłowo zamknięte.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Poniższy kod przedstawia to samo rozwiązanie przy użyciu `try/finally`, a nie `using`.  
  
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
  
 Jeśli żadne z tych rozwiązań nie mogą być używane (na przykład, jeśli <xref:System.IO.StreamWriter> jest przechowywany w zmiennej statycznej i nie można łatwo uruchomić kodu na końcu jego okresu istnienia), należy wywołać <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po jego ostatnim użyciu lub ustawić właściwość <xref:System.IO.StreamWriter.AutoFlush%2A> na `true` przed pierwszym użyciem powinien uniknąć tego problemu.  
  
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
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informujący o tym, że wystąpiło naruszenie.  
  
## <a name="configuration"></a>Konfiguracja  
  
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
