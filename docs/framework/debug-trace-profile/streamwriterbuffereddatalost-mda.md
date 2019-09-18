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
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
<xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> Asystent debugowania zarządzanego(MDA)jestuaktywniany,gdyjestzapisywanaw,alemetodalubniejestnastępniewywoływanaprzedzniszczeniemwystąpieniaelementu.`streamWriterBufferedDataLost` Po włączeniu tego MDA środowisko uruchomieniowe określa, czy wszystkie dane buforowane nadal istnieją w <xref:System.IO.StreamWriter>. Jeśli istnieją dane buforowane, zdarzenie MDA zostanie aktywowane. Wywoływanie metod <xref:System.GC.WaitForPendingFinalizers%2A>imoże zmusić finalizatory do uruchomienia. <xref:System.GC.Collect%2A> Finalizatory będą działać w sposób pozornie dowolnie dowolną liczbę razy, a nawet w przypadku zakończenia procesu. Jawne uruchamianie finalizatorów z włączonym zdarzeniem MDA pomoże bardziej niezawodne odtwarzanie tego typu problemu.  
  
## <a name="symptoms"></a>Symptomy  
 A <xref:System.IO.StreamWriter> nie zapisuje ostatnich 1 – 4 KB danych do pliku.  
  
## <a name="cause"></a>Przyczyna  
 Dane buforów wewnętrznie, które wymagają <xref:System.IO.StreamWriter.Close%2A> , aby Metoda <xref:System.IO.StreamWriter.Flush%2A> lub wywoływana w celu zapisu danych buforowanych w źródłowym magazynie danych. <xref:System.IO.StreamWriter> Jeśli <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter> lub <xref:System.IO.StreamWriter.Flush%2A> nie jest odpowiednio wywoływana, dane buforowane w wystąpieniu mogą nie być zapisywane zgodnie z oczekiwaniami.  
  
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
 Upewnij się, że <xref:System.IO.StreamWriter.Close%2A> jest <xref:System.IO.StreamWriter.Flush%2A> wywoływana lub <xref:System.IO.StreamWriter> w przypadku przed zamknięciem aplikacji lub dowolnego bloku kodu, który ma wystąpienie <xref:System.IO.StreamWriter>elementu. Jednym z najlepszych mechanizmów do osiągnięcia tego jest utworzenie wystąpienia z C# `using` blokiem (`Using` w <xref:System.IO.StreamWriter.Dispose%2A> Visual Basic), które zapewni wywołanie metody dla składnika zapisywania, co spowoduje, że wystąpienie jest prawidłowo zamknięte.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Poniższy kod przedstawia to samo rozwiązanie przy użyciu `try/finally` polecenia `using`zamiast.  
  
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
  
 Jeśli żadne z tych rozwiązań nie mogą być używane (na przykład, jeśli <xref:System.IO.StreamWriter> jest przechowywany w zmiennej statycznej i nie można łatwo uruchomić kodu na końcu jego okresu istnienia), nastąpi wywołanie <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Flush%2A> po ostatnim użyciu lub ustawienie <xref:System.IO.StreamWriter.AutoFlush%2A> `true` przed pierwszym użyciem należy unikać tego problemu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
