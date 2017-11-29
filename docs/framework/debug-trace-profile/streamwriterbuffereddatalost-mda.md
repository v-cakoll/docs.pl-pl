---
title: streamWriterBufferedDataLost MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fa6b64d37052c40dbef83a25b622e415f6946c1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
`streamWriterBufferedDataLost` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.IO.StreamWriter> są zapisywane, ale <xref:System.IO.StreamWriter.Flush%2A> lub <xref:System.IO.StreamWriter.Close%2A> metoda nie jest następnie wywoływana przed wystąpienie <xref:System.IO.StreamWriter> zostanie zniszczony. Po włączeniu to zdarzenie MDA środowiska uruchomieniowego Określa, czy wszystkie buforowane dane nadal istnieje w ramach <xref:System.IO.StreamWriter>. Jeśli istnieje buforowane dane, MDA jest aktywowane. Wywoływanie <xref:System.GC.Collect%2A> i <xref:System.GC.WaitForPendingFinalizers%2A> metod można wymusić finalizatory do uruchomienia. Finalizatory w przeciwnym razie zostanie uruchomiony w czasie pozornie dowolnego i prawdopodobnie w ogóle na zakończenie procesu. Jawnie systemie finalizatory to zdarzenie MDA włączone pomogą bardziej niezawodnie odtworzyć ten typ problemu.  
  
## <a name="symptoms"></a>Symptomy  
 A <xref:System.IO.StreamWriter> nie zapisuje ostatni 1 – 4 KB danych do pliku.  
  
## <a name="cause"></a>Przyczyna  
 <xref:System.IO.StreamWriter> Buforów danych, które wymaga, aby <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> do zapisu buforowane dane odpowiedni magazyn danych można wywołać metody. Jeśli <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> nie jest odpowiednio wywoływany, dane buforowane w <xref:System.IO.StreamWriter> wystąpienia nie mogą być zapisane, zgodnie z oczekiwaniami.  
  
 Oto przykładowy kod niepoprawnie napisane, że to zdarzenie MDA powinien catch.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Poprzedni kod zostanie aktywowany, to zdarzenie MDA bardziej niezawodnie Jeśli wyrzucania elementów bezużytecznych jest wyzwalane, a następnie wstrzymane do czasu zakończenia finalizatory. Do śledzenia tego rodzaju problem, można dodać następujący kod na końcu poprzedniego metody kompilacji debugowania. Dzięki temu można niezawodnie aktywować MDA, ale oczywiście nie ustalić przyczynę problemu.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, że należy wywołać <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> przed zamknięciem aplikacji lub dowolnego blok kodu, który ma wystąpienie <xref:System.IO.StreamWriter>. Z mechanizmów najlepsze na osiągnięcie tego celu jest utworzenia wystąpienia w języku C# `using` bloku (`Using` w języku Visual Basic), który zapewni <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda dla edytora, co powoduje wystąpienie prawidłowo zamknięte.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Poniższy kod przedstawia to samo rozwiązanie przy użyciu `try/finally` zamiast `using`.  
  
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
  
 Jeśli żadna z tych rozwiązań nie może być używany (na przykład, jeśli <xref:System.IO.StreamWriter> są przechowywane w statycznych zmienną i możesz łatwo nie można uruchomić kod z końcem okresu obowiązywania), wywołując <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po jej ostatniego użycia lub ustawienie <xref:System.IO.StreamWriter.AutoFlush%2A> dla właściwości `true` przed pierwszym użyciem powinien uniknąć tego problemu.  
  
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
 Komunikat informujący, że wystąpiło to naruszenie.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamWriter>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
