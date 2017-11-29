---
title: bindingFailure MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 89c1ce4b39379aeae80240750cdbcd2e61b6ec11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="bindingfailure-mda"></a>bindingFailure MDA
`bindingFailure` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy zestaw nie udało się załadować.  
  
## <a name="symptoms"></a>Symptomy  
 Kod podjął próbę załadowania zestawu przy użyciu odwołanie statyczne lub jednej z metod modułu ładującego, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>. Zestaw nie został załadowany i <xref:System.IO.FileNotFoundException> lub <xref:System.IO.FileLoadException> wyjątku.  
  
## <a name="cause"></a>Przyczyna  
 Niepowodzenie powiązania występuje, gdy środowisko uruchomieniowe nie może załadować zestawu. Niepowodzenie powiązania może być skutkiem jednej z następujących sytuacji:  
  
-   Środowisko uruchomieniowe języka wspólnego (CLR) nie można odnaleźć żądanego zestawu. Istnieje wiele przyczyn, może to się zdarzyć, takich jak zestaw nie jest zainstalowany lub aplikacja nie jest poprawnie skonfigurowana można znaleźć zestawu.  
  
-   Typowy scenariusz problemu jest przekazanie typu do innej domeny aplikacji, co wymaga CLR można załadować zestawu zawierającego tego typu w innej domenie aplikacji. Nie być może środowiska uruchomieniowego można załadować zestawu, jeśli domena aplikacji jest inaczej skonfigurowana od oryginalnej domeny aplikacji. Na przykład domen aplikacji dwóch mają różne <xref:System.AppDomain.BaseDirectory%2A> wartości właściwości.  
  
-   Żądany zestaw jest uszkodzony lub nie jest zestawem.  
  
-   Podjęto próbę załadowania zestawu kod nie ma uprawnienia zabezpieczeń dostępu kodu poprawne ładowanie zestawów.  
  
-   Poświadczenia użytkownika nie zapewniają wymagane uprawnienia do odczytu pliku.  
  
## <a name="resolution"></a>Rozwiązanie  
 Pierwszym krokiem jest ustalenie, dlaczego CLR nie można powiązać żądany zestaw. Istnieje wiele przyczyn, dlaczego środowiska uruchomieniowego nie zostały znalezione lub został stanie obciążenia żądany zestaw, takich jak scenariusze opisane w sekcji Przyczyna. Aby wyeliminować przyczynę niepowodzenia powiązania zalecane są następujące akcje:  
  
-   Ustal przyczynę przy użyciu danych dostarczonych przez `bindingFailure` MDA:  
  
    -   Uruchom [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) odczytać dzienniki błędów, utworzonego przez obiekt wiążący zestawu.  
  
    -   Ustal, jeśli zestaw w lokalizacji jest wymagane. W przypadku liczby <xref:System.Reflection.Assembly.LoadFrom%2A> i <xref:System.Reflection.Assembly.LoadFile%2A> metod, żądanej lokalizacji można łatwo ustalić. W przypadku liczby <xref:System.Reflection.Assembly.Load%2A> metodę, która wiąże przy użyciu tożsamości zestawu, musisz sprawdzić dla zestawów zgodnych jego tożsamość w domenie aplikacji <xref:System.AppDomain.BaseDirectory%2A> ścieżka sondowania właściwości i globalnej pamięci podręcznej zestawów.  
  
-   Usuń przyczynę oparte na poprzednie określenie. Opcje rozpoznawania możliwe są następujące:  
  
    -   Zainstaluj żądany zestaw w globalnej pamięci podręcznej zestawów i wywołania. <xref:System.Reflection.Assembly.Load%2A>Metoda ładowania zestawu przez tożsamości.  
  
    -   Skopiuj żądany zestaw do katalogu aplikacji i wywołanie <xref:System.Reflection.Assembly.Load%2A> metodę, aby załadować zestawu przez tożsamości.  
  
    -   Skonfiguruj ponownie domeny aplikacji, w którym wystąpił błąd powiązania uwzględnienie ścieżkę zestawu albo zmieniając <xref:System.AppDomain.BaseDirectory%2A> właściwości lub Dodawanie prywatnej sondowania ścieżek.  
  
    -   Zmiana listy kontroli dostępu dla plików umożliwiają zalogowanego użytkownika do odczytu pliku.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Zwraca tylko dane o powiązanie błędów.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA raporty zestawu, którego nie udało się załadować, w tym żądana ścieżka lub nazwa wyświetlana, kontekst powiązania, domena aplikacji, w której zażądano obciążenia i przyczynę błędu.  
  
 Żądana ścieżka lub nazwa wyświetlana może być pusta, jeśli dane nie był dostępny do środowiska CLR. Jeśli wywołanie, której nie można było <xref:System.Reflection.Assembly.Load%2A> — metoda, prawdopodobnie środowiska uruchomieniowego nie można ustalić nazwę wyświetlaną dla zestawu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano sytuację, której można uaktywnić to zdarzenie MDA:  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
