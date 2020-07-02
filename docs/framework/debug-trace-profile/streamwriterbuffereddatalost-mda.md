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
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
`streamWriterBufferedDataLost`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy <xref:System.IO.StreamWriter> jest zapisywana w, ale <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter.Close%2A> Metoda lub nie jest następnie wywoływana przed zniszczeniem wystąpienia elementu <xref:System.IO.StreamWriter> . Po włączeniu tego MDA środowisko uruchomieniowe określa, czy wszystkie dane buforowane nadal istnieją w <xref:System.IO.StreamWriter> . Jeśli istnieją dane buforowane, zdarzenie MDA zostanie aktywowane. Wywoływanie <xref:System.GC.Collect%2A> <xref:System.GC.WaitForPendingFinalizers%2A> metod i może zmusić finalizatory do uruchomienia. Finalizatory będą działać w sposób pozornie dowolnie dowolną liczbę razy, a nawet w przypadku zakończenia procesu. Jawne uruchamianie finalizatorów z włączonym zdarzeniem MDA pomoże bardziej niezawodne odtwarzanie tego typu problemu.  
  
## <a name="symptoms"></a>Objawy  
 A nie <xref:System.IO.StreamWriter> zapisuje ostatnich 1 – 4 KB danych do pliku.  
  
## <a name="cause"></a>Przyczyna  
 <xref:System.IO.StreamWriter>Dane buforów wewnętrznie, które wymagają, <xref:System.IO.StreamWriter.Close%2A> <xref:System.IO.StreamWriter.Flush%2A> Aby Metoda lub wywoływana w celu zapisu danych buforowanych w źródłowym magazynie danych. Jeśli <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> nie jest odpowiednio wywoływana, dane buforowane w <xref:System.IO.StreamWriter> wystąpieniu mogą nie być zapisywane zgodnie z oczekiwaniami.  
  
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
 Upewnij się, że jest wywoływana <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> w przypadku <xref:System.IO.StreamWriter> przed zamknięciem aplikacji lub dowolnego bloku kodu, który ma wystąpienie elementu <xref:System.IO.StreamWriter> . Jednym z najlepszych mechanizmów do osiągnięcia tego jest utworzenie wystąpienia z `using` blokiem C# ( `Using` w Visual Basic), które zapewni <xref:System.IO.StreamWriter.Dispose%2A> wywołanie metody dla składnika zapisywania, co spowoduje, że wystąpienie jest prawidłowo zamknięte.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 Poniższy kod przedstawia to samo rozwiązanie przy użyciu polecenia `try/finally` zamiast `using` .  
  
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
  
 Jeśli żadne z tych rozwiązań nie mogą być używane (na przykład, jeśli <xref:System.IO.StreamWriter> jest przechowywany w zmiennej statycznej i nie można łatwo uruchomić kodu na końcu jego okresu istnienia), <xref:System.IO.StreamWriter.Flush%2A> <xref:System.IO.StreamWriter> przed tym problemem należy się odwoływać od momentu jego ostatniego użycia lub ustawienia <xref:System.IO.StreamWriter.AutoFlush%2A> właściwości na `true` przed pierwszym użyciem.  
  
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
  
## <a name="configuration"></a>Konfigurowanie  
  
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
