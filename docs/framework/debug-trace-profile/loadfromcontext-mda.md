---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89605a119e8251ffd577ff402366dff0fd4af4d7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052516"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
Asystent `loadFromContext` debugowania zarządzanego (MDA) jest aktywowany, jeśli zestaw jest ładowany `LoadFrom` do kontekstu. Taka sytuacja może wystąpić w wyniku wywołania <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub innych podobnych metod.  
  
## <a name="symptoms"></a>Symptomy  
 Użycie niektórych metod ładujących może spowodować załadowanie zestawów w `LoadFrom` kontekście. Użycie tego kontekstu może spowodować nieoczekiwane zachowanie serializacji, rzutowania i rozpoznawania zależności. Ogólnie rzecz biorąc, zaleca się, aby zestawy zostały załadowane `Load` do kontekstu, aby uniknąć tych problemów. Trudno jest określić kontekst, do którego zestaw został załadowany, bez tego MDA.  
  
## <a name="cause"></a>Przyczyna  
 Ogólnie rzecz biorąc, zestaw został załadowany do `LoadFrom` kontekstu, jeśli został załadowany ze ścieżki `Load` poza kontekstem, takiej jak <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> globalna pamięć podręczna zestawu lub właściwość.  
  
## <a name="resolution"></a>Rozwiązanie  
 Skonfiguruj aplikacje, takie <xref:System.Reflection.Assembly.LoadFrom%2A> jak wywołania, które nie są już potrzebne. W tym celu można użyć następujących technik:  
  
- Zainstaluj zestawy w globalnej pamięci podręcznej zestawów.  
  
- Umieść zestawy w <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu <xref:System.AppDomain>dla. W przypadku domeny <xref:System.AppDomainSetup.ApplicationBase%2A> domyślnej katalog jest tym, który zawiera plik wykonywalny, który uruchomił proces. Może to również wymagać utworzenia nowego <xref:System.AppDomain> , jeśli nie jest wygodne przenoszenie zestawu.  
  
- Dodaj ścieżkę do sondowania do pliku konfiguracji aplikacji (. config) lub do domen aplikacji pomocniczych, jeśli zależne zestawy znajdują się w katalogach podrzędnych względem pliku wykonywalnego.  
  
 W każdym przypadku kod można zmienić, aby użyć <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Zdarzenie MDA nie ma żadnego wpływu na środowisko CLR. Raportuje kontekst, który został użyty w wyniku żądania załadowania.  
  
## <a name="output"></a>Dane wyjściowe  
 Raport MDA, że zestaw został załadowany do `LoadFrom` kontekstu. Określa prostą nazwę zestawu i ścieżkę. Sugeruje również środki zaradcze, aby uniknąć korzystania `LoadFrom` z kontekstu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
