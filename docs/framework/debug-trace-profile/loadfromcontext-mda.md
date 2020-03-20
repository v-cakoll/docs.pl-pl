---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: d0090a0272d1c3b6175b351175689df1e1e4fdbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181808"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
Asystent `loadFromContext` debugowania zarządzanego (MDA) jest aktywowany, `LoadFrom` jeśli zestaw jest ładowany do kontekstu. Taka sytuacja może wystąpić w <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> wyniku wywołania lub innych podobnych metod.  
  
## <a name="symptoms"></a>Objawy  
 Użycie niektórych metod modułu ładującego może spowodować `LoadFrom` zestawy są ładowane w kontekście. Użycie tego kontekstu może spowodować nieoczekiwane zachowanie serializacji, rzutowania i rozpoznawania zależności. Ogólnie rzecz biorąc zaleca się, że `Load` zestawy mają być ładowane do kontekstu, aby uniknąć tych problemów. Trudno jest określić, który kontekst zestaw został załadowany do bez tego MDA.  
  
## <a name="cause"></a>Przyczyna  
 Ogólnie rzecz biorąc zestaw został `LoadFrom` załadowany do kontekstu, `Load` jeśli został załadowany ze ścieżki <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> poza kontekstem, takich jak globalnej pamięci podręcznej zestawu lub właściwości.  
  
## <a name="resolution"></a>Rozwiązanie  
 Skonfiguruj <xref:System.Reflection.Assembly.LoadFrom%2A> aplikacje w taki sposób, aby wywołania nie były już potrzebne. W tym celu można użyć następujących technik:  
  
- Zainstaluj zestawy w globalnej pamięci podręcznej zestawów.  
  
- Umieść zestawy w <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu dla <xref:System.AppDomain>pliku . W przypadku domeny domyślnej <xref:System.AppDomainSetup.ApplicationBase%2A> katalog jest tym, który zawiera plik wykonywalny, który rozpoczął proces. Może to również wymagać <xref:System.AppDomain> utworzenia nowego, jeśli nie jest wygodne, aby przenieść zestaw.  
  
- Dodaj ścieżkę sondowania do pliku konfiguracji aplikacji (.config) lub do domen aplikacji pomocniczych, jeśli zestawy zależne znajdują się w katalogach podrzędnych względem pliku wykonywalnego.  
  
 W każdym przypadku kod można zmienić, aby użyć <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na czas działania  
 MDA nie ma żadnego wpływu na CLR. Raportuje kontekst, który został użyty w wyniku żądania obciążenia.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA raporty, że zestaw został `LoadFrom` załadowany do kontekstu. Określa prostą nazwę zestawu i ścieżkę. Sugeruje również środki zaradcze, aby uniknąć korzystania z kontekstu. `LoadFrom`  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sytuację, która może aktywować ten MDA:  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
