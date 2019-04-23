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
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
`streamWriterBufferedDataLost` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po <xref:System.IO.StreamWriter> są zapisywane, ale <xref:System.IO.StreamWriter.Flush%2A> lub <xref:System.IO.StreamWriter.Close%2A> metoda nie jest później wywoływana przed wystąpieniem programu <xref:System.IO.StreamWriter> zostanie zniszczony. Gdy to zdarzenie MDA jest włączona, środowisko wykonawcze określa, czy wszystkie buforowane dane nadal istnieje w ramach <xref:System.IO.StreamWriter>. Jeśli istnieje buforowane dane, to zdarzenie MDA jest aktywowane. Wywoływanie <xref:System.GC.Collect%2A> i <xref:System.GC.WaitForPendingFinalizers%2A> metod można wymusić finalizatory do uruchomienia. Finalizatory w przeciwnym razie zostanie uruchomiony w czasie pozornie dowolnego i prawdopodobnie w ogóle nie będzie na zakończenie procesu. Jawnie uruchamianie finalizatorów z tego MDA włączona ma na celu bardziej niezawodnie odtworzyć ten typ problemu.  
  
## <a name="symptoms"></a>Symptomy  
 Element <xref:System.IO.StreamWriter> nie zapisuje ostatni 1 – 4 KB danych w pliku.  
  
## <a name="cause"></a>Przyczyna  
 <xref:System.IO.StreamWriter> Buforuje dane, które wymaga, aby <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> metoda jest wywoływana w celu zapisania buforowane dane do magazynu danych. Jeśli <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> nie jest prawidłowo wywoływany, danych, lecz buforowane w <xref:System.IO.StreamWriter> wystąpienia nie może być zapisana, zgodnie z oczekiwaniami.  
  
 Oto przykład źle kod, który należy przechwytywać to zdarzenie MDA.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Poprzedni kod będzie aktywuje tego zdarzenia MDA bardziej niezawodne, gdy wyrzucanie elementów bezużytecznych jest wyzwalane, a następnie wstrzymane do czasu zakończenia finalizatory. Do śledzenia tego rodzaju problem, można dodać następujący kod na końcu poprzedniego metody do kompilacji debugowanej. Pomoże to niezawodne aktywować MDA, ale oczywiście nie ustalić przyczynę problemu.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, należy wywołać <xref:System.IO.StreamWriter.Close%2A> lub <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> przed zamknięciem aplikacji lub dowolnym blok kodu, który zawiera wystąpienie <xref:System.IO.StreamWriter>. Jedną z najlepszych mechanizmy służące osiągnięciu tego celu jest utworzenie wystąpienia z C# `using` bloku (`Using` w języku Visual Basic), który zapewni <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda dla edytora, co w przypadku poprawnie zamknięte.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Poniższy kod przedstawia tego samego rozwiązania przy użyciu `try/finally` zamiast `using`.  
  
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
  
 Jeśli żadna z tych rozwiązań nie może być używana (na przykład, jeśli <xref:System.IO.StreamWriter> są przechowywane w statycznych zmienną i możesz łatwo nie można uruchomić kod na końcu okresu jego istnienia), następnie wywoływania <xref:System.IO.StreamWriter.Flush%2A> na <xref:System.IO.StreamWriter> po jej ostatniego użycia lub ustawienie <xref:System.IO.StreamWriter.AutoFlush%2A> Właściwość `true` przed pierwszym użyciem należy unikać tego problemu.  
  
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
 To zdarzenie MDA nie ma wpływu na środowiska uruchomieniowego.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat wskazujący, że to naruszenie wystąpił.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
