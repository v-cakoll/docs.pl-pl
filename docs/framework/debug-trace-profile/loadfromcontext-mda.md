---
title: loadFromContext MDA
description: Informacje o programie loadFromContext Managed Debug Assistant (MDA) w programie .NET, który jest uaktywniany w przypadku załadowania zestawu do kontekstu LoadFrom.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 8d55268f2b2106dde4e488a6f0271fd3b17349da
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051652"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
`loadFromContext`Asystent debugowania zarządzanego (MDA) jest aktywowany, jeśli zestaw jest ładowany do `LoadFrom` kontekstu. Taka sytuacja może wystąpić w wyniku wywołania <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub innych podobnych metod.  
  
## <a name="symptoms"></a>Objawy  
 Użycie niektórych metod ładujących może spowodować załadowanie zestawów w `LoadFrom` kontekście. Użycie tego kontekstu może spowodować nieoczekiwane zachowanie serializacji, rzutowania i rozpoznawania zależności. Ogólnie rzecz biorąc, zaleca się, aby zestawy zostały załadowane do `Load` kontekstu, aby uniknąć tych problemów. Trudno jest określić kontekst, do którego zestaw został załadowany, bez tego MDA.  
  
## <a name="cause"></a>Przyczyna  
 Ogólnie rzecz biorąc, zestaw został załadowany do `LoadFrom` kontekstu, jeśli został załadowany ze ścieżki poza `Load` kontekstem, takiej jak globalna pamięć podręczna zestawu lub <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> Właściwość.  
  
## <a name="resolution"></a>Rozwiązanie  
 Skonfiguruj aplikacje, takie jak wywołania, które <xref:System.Reflection.Assembly.LoadFrom%2A> nie są już potrzebne. W tym celu można użyć następujących technik:  
  
- Zainstaluj zestawy w globalnej pamięci podręcznej zestawów.  
  
- Umieść zestawy w <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu dla <xref:System.AppDomain> . W przypadku domeny domyślnej <xref:System.AppDomainSetup.ApplicationBase%2A> katalog jest tym, który zawiera plik wykonywalny, który uruchomił proces. Może to również wymagać utworzenia nowego, <xref:System.AppDomain> Jeśli nie jest wygodne przenoszenie zestawu.  
  
- Dodaj ścieżkę do sondowania do pliku konfiguracji aplikacji (. config) lub do domen aplikacji pomocniczych, jeśli zależne zestawy znajdują się w katalogach podrzędnych względem pliku wykonywalnego.  
  
 W każdym przypadku kod można zmienić, aby użyć <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Zdarzenie MDA nie ma żadnego wpływu na środowisko CLR. Raportuje kontekst, który został użyty w wyniku żądania załadowania.  
  
## <a name="output"></a>Dane wyjściowe  
 Raport MDA, że zestaw został załadowany do `LoadFrom` kontekstu. Określa prostą nazwę zestawu i ścieżkę. Sugeruje również środki zaradcze, aby uniknąć korzystania z `LoadFrom` kontekstu.  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sytuację, w której można aktywować to MDA:  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is
            // located outside of the Load context probing path.
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
