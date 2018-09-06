---
title: 'Porady: przechwytywanie wyjątku typu non-CLS'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 6a2a0f034a9f01c2c4614589235dc8ebb5224465
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43854882"
---
# <a name="how-to-catch-a-non-cls-exception"></a>Porady: przechwytywanie wyjątku typu non-CLS
Niektórych języków .NET, w tym C + +/ CLI, dopuszcza się użycia obiektów zgłaszają wyjątki, które nie pochodzą z <xref:System.Exception>. Takie wyjątki są nazywane *wyjątki niezgodnych ze specyfikacją CLS* lub *niebędące wyjątkami*. W języku C# nie generują wyjątki niezgodnych ze specyfikacją CLS, ale można przechwytywać na dwa sposoby:  
  
-   W ramach `catch (RuntimeWrappedException e)` bloku.
  
     Domyślnie zestaw Visual C# przechwytuje wyjątki niezgodnych ze specyfikacją CLS, jako wyjątki opakowana. Użyj tej metody, jeśli potrzebny jest dostęp do oryginalnego wyjątku, który jest możliwy za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości. Procedury w dalszej części tego tematu opisano sposób przechwytywanie wyjątków w ten sposób.  
  
-   W ramach ogólnego bloku catch (catch blok bez określony typ wyjątku), który jest umieszczany po wszystkich innych `catch` bloków.
  
     Metoda ta jest używana, gdy chcesz wykonać pewne działania (na przykład zapis do pliku dziennika) w odpowiedzi na wyjątki niezgodnych ze specyfikacją CLS i nie potrzebujesz dostępu do informacji o wyjątku. Domyślnie środowisko uruchomieniowe języka wspólnego opakowuje wszystkie wyjątki. Aby wyłączyć to zachowanie, należy dodać ten atrybut na poziomie zestawu w kodzie, zwykle w pliku AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>Aby przechwycić wyjątek niezgodny ze specyfikacją  
  
W ramach `catch(RuntimeWrappedException e)` blokowania, dostęp do oryginalnego wyjątku za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przechwycić wyjątek niezgodny ze specyfikacją, który został zgłoszony z biblioteki klas, napisany w języku C + +/ interfejsu wiersza polecenia. Należy pamiętać, że w tym przykładzie kodu klienta języka C# wie, z wyprzedzeniem to typ wyjątku jest zgłaszana <xref:System.String?displayProperty=nameWithType>. Można rzutować <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości kopii jego typ oryginalny, tak długo, jak ten typ jest dostępny z poziomu kodu.  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
- [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)
