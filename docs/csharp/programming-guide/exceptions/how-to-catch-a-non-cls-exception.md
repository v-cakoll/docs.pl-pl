---
title: Przechwytywanie wyjątku typu non-CLS
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346279"
---
# <a name="how-to-catch-a-non-cls-exception"></a>Przechwytywanie wyjątku typu non-CLS
Niektóre języki .NET, w tym C++/CLI, zezwalają obiektom <xref:System.Exception>na zgłaszanie wyjątków, które nie pochodzą z . Takie wyjątki są nazywane *wyjątkami innych* niż CLS lub *non-Exceptions*. W języku C# nie można zgłaszać wyjątków innych niż CLS, ale można je przechwycić na dwa sposoby:  
  
- W `catch (RuntimeWrappedException e)` obrębie bloku.
  
     Domyślnie visual C# zestaw przechwytuje wyjątki innych niż CLS jako opakowane wyjątki. Użyj tej metody, jeśli potrzebujesz dostępu do oryginalnego wyjątku, który jest dostępny za pośrednictwem <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości. Procedura w dalszej części tego tematu wyjaśnia, jak w ten sposób wychwycić wyjątki.  
  
- W obrębie ogólnego bloku catch (catch bloku bez określonego typu `catch` wyjątku), który jest umieszczany po wszystkich innych bloków.
  
     Tej metody należy użyć, gdy chcesz wykonać niektóre działania (takie jak zapis do pliku dziennika) w odpowiedzi na wyjątki innych niż CLS i nie trzeba dostępu do informacji o wyjątku. Domyślnie czas wykonywania języka wspólnego zawija wszystkie wyjątki. Aby wyłączyć to zachowanie, dodaj ten atrybut na poziomie zestawu do `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`kodu, zazwyczaj w pliku AssemblyInfo.cs: .  
  
### <a name="to-catch-a-non-cls-exception"></a>Aby przechwycić wyjątek niebędący cls  
  
W `catch(RuntimeWrappedException e)` bloku, dostęp do oryginalnego wyjątku <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> za pośrednictwem właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak przechwycić wyjątek niecls, który został wygenerowany z biblioteki klas napisanych w Języku C++/CLI. Należy zauważyć, że w tym przykładzie kod klienta Języka C# <xref:System.String?displayProperty=nameWithType>wie z góry, że zgłaszany jest typ wyjątku . Można rzutować <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwość z powrotem jego oryginalny typ tak długo, jak ten typ jest dostępny z kodu.  
  
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
- [Wyjątki i obsługa wyjątków](./index.md)
