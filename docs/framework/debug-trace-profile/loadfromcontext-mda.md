---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 28ef6e12c82cf5ca56962756b9ea964d0ae9baaa
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216169"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
Asystent debugowania zarządzanego `loadFromContext` (MDA) jest aktywowany, jeśli zestaw jest ładowany do kontekstu `LoadFrom`. Taka sytuacja może wystąpić w wyniku wywołania <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub innych podobnych metod.  
  
## <a name="symptoms"></a>Objawy  
 Użycie niektórych metod ładujących może spowodować załadowanie zestawów w kontekście `LoadFrom`. Użycie tego kontekstu może spowodować nieoczekiwane zachowanie serializacji, rzutowania i rozpoznawania zależności. Ogólnie rzecz biorąc, zaleca się, aby zestawy zostały załadowane do kontekstu `Load`, aby uniknąć tych problemów. Trudno jest określić kontekst, do którego zestaw został załadowany, bez tego MDA.  
  
## <a name="cause"></a>Przyczyna  
 Ogólnie rzecz biorąc, zestaw został załadowany do kontekstu `LoadFrom`, jeśli został załadowany ze ścieżki poza kontekstem `Load`, takich jak globalna pamięć podręczna zestawów lub właściwość <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType>.  
  
## <a name="resolution"></a>Rozwiązanie  
 Skonfiguruj aplikacje, takie jak wywołania <xref:System.Reflection.Assembly.LoadFrom%2A> nie są już potrzebne. W tym celu można użyć następujących technik:  
  
- Zainstaluj zestawy w globalnej pamięci podręcznej zestawów.  
  
- Umieść zestawy w <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu dla <xref:System.AppDomain>. W przypadku domeny domyślnej katalog <xref:System.AppDomainSetup.ApplicationBase%2A> jest taki, który zawiera plik wykonywalny, który uruchomił proces. Może to również wymagać utworzenia nowego <xref:System.AppDomain>, jeśli nie jest to wygodne do przenoszenia zestawu.  
  
- Dodaj ścieżkę do sondowania do pliku konfiguracji aplikacji (. config) lub do domen aplikacji pomocniczych, jeśli zależne zestawy znajdują się w katalogach podrzędnych względem pliku wykonywalnego.  
  
 W każdym przypadku kod można zmienić, aby użyć metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Zdarzenie MDA nie ma żadnego wpływu na środowisko CLR. Raportuje kontekst, który został użyty w wyniku żądania załadowania.  
  
## <a name="output"></a>Dane wyjściowe  
 Raport MDA, że zestaw został załadowany do kontekstu `LoadFrom`. Określa prostą nazwę zestawu i ścieżkę. Sugeruje również środki zaradcze, aby uniknąć używania kontekstu `LoadFrom`.  
  
## <a name="configuration"></a>Konfiguracja  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
