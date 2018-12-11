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
ms.openlocfilehash: 3ee575cacbc51fc910770cca145a4280f97b66db
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144442"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
`loadFromContext` Zarządzanego Asystenta debugowania (MDA) jest włączone, jeśli zestaw jest ładowany do `LoadFrom` kontekstu. Taka sytuacja może wystąpić w wyniku wywołania <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub inne podobne metody.  
  
## <a name="symptoms"></a>Symptomy  
 Korzystanie z niektórych metod modułu ładującego może doprowadzić do zestawów, które są ładowane `LoadFrom` kontekstu. Użycie tego kontekstu może spowodować nieoczekiwane zachowanie serializacji, rzutowania i rozpoznawania zależności. Ogólnie rzecz biorąc, zalecane jest, że zestawy wczytanie `Load` kontekstu, aby uniknąć tych problemów. Trudno określić, w którym kontekście zestaw został załadowany do bez to zdarzenie MDA.  
  
## <a name="cause"></a>Przyczyna  
 Ogólnie rzecz biorąc, zestaw został załadowany do `LoadFrom` kontekstu, jeśli został załadowany ze ścieżki poza `Load` kontekstu, takich jak pamięci podręcznej zestawów globalnych lub <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="resolution"></a>Rozwiązanie  
 Skonfigurowanie aplikacji tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> wywołania nie są już potrzebne. Aby to zrobić, można użyć następujących technik:  
  
-   Instalowanie zestawów w globalnej pamięci podręcznej.  
  
-   Umieść zestawów w <xref:System.AppDomainSetup.ApplicationBase%2A> katalog dla <xref:System.AppDomain>. W przypadku domyślnej domeny <xref:System.AppDomainSetup.ApplicationBase%2A> katalog jest ten, który zawiera plik wykonywalny, który uruchomił proces. Może to również wymagać utworzenie nowego <xref:System.AppDomain> Jeśli nie jest wygodne przenieść zestawu.  
  
-   Dodaj badania ścieżki do pliku konfiguracji (.config) aplikacji lub do domen aplikacji dodatkowych zestawów zależnych znajdują się w katalogach podrzędnych względem pliku wykonywalnego.  
  
 W każdym przypadku można zmienić kod do użycia <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 MDA nie ma żadnego wpływu na środowisko CLR. Zgłasza kontekstu, który został użyty w wyniku żądania obciążenia.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA zgłasza, że zestaw został załadowany do `LoadFrom` kontekstu. Określa prostą nazwę zestawu oraz ścieżki. Podano tu także środków zaradczych, które należy unikać `LoadFrom` kontekstu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano sytuację, która może aktywować to zdarzenie MDA:  
  
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
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
