---
title: loadFromContext MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0910e4bdd2cc9c99afc55c5f70f4d225a87deb5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
`loadFromContext` Zarządzany Asystent debugowania (MDA) jest włączone, jeśli zestaw jest ładowany do `LoadFrom` kontekstu. Taka sytuacja może wystąpić w wyniku wywołania <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub innych metod podobne.  
  
## <a name="symptoms"></a>Symptomy  
 Korzystanie z niektórych metod modułu ładującego może spowodować zestawy ładowane w `LoadFrom` kontekstu. Użycie tego kontekstu może spowodować nieoczekiwane zachowanie w przypadku serializacji, rzutowania i rozpoznawania zależności. Ogólnie rzecz biorąc, zaleca się, że można załadować do zestawów `Load` kontekstu, aby uniknąć tych problemów. Jest trudne do ustalenia, które kontekstu zestaw został załadowany do bez to zdarzenie MDA.  
  
## <a name="cause"></a>Przyczyna  
 Ogólnie rzecz biorąc, zestaw został załadowany do `LoadFrom` kontekstu, jeśli został załadowany z ścieżki poza `Load` kontekstu, takich jak globalnej pamięci podręcznej zestawów lub <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="resolution"></a>Rozwiązanie  
 Skonfigurowanie aplikacji tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> wywołania nie są już potrzebne. Tak, można użyć następujące techniki:  
  
-   Instalowanie zestawów w globalnej pamięci podręcznej zestawów.  
  
-   Umieść zestawów w <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu dla <xref:System.AppDomain>. W przypadku domyślnej domeny <xref:System.AppDomainSetup.ApplicationBase%2A> katalog jest ten, który zawiera plik wykonywalny, który uruchomiony proces. Może to również wymagać tworzenia nowego <xref:System.AppDomain> Jeśli nie jest wygodne można przenieść zestawu.  
  
-   Dodaj ścieżki próbkowania do pliku konfiguracji (config) aplikacji lub do domen aplikacji dodatkowej zależne zestawy są w katalogach podrzędnych względem pliku wykonywalnego.  
  
 W każdym przypadku można zmienić kod do użycia <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 MDA nie ma wpływu na środowisko CLR. Raporty kontekstu, którego użyto w wyniku żądania obciążenia.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA zgłasza, że zestaw został załadowany do `LoadFrom` kontekstu. Określa prostą nazwę zestawu oraz ścieżki. Podano tu także środki zaradcze, aby uniknąć używania `LoadFrom` kontekstu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano sytuację, której można uaktywnić to zdarzenie MDA:  
  
```  
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
