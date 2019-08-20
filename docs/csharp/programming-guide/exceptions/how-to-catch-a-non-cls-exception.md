---
title: 'Instrukcje: Przechwytywanie wyjątku typu non-CLS'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: d0ba212610372a89c2a3b4c6a249c6d8a02fa507
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590285"
---
# <a name="how-to-catch-a-non-cls-exception"></a>Instrukcje: Przechwytywanie wyjątku typu non-CLS
Niektóre języki .NET, w C++tym/CLI, umożliwiają obiektom zgłaszanie wyjątków, które nie <xref:System.Exception>pochodzą od. Takie wyjątki są nazywane wyjątkami nienależącymi *do CLS* lub niewyjątkami. C# Nie można zgłosić wyjątków innych niż CLS, ale można je przechwycić na dwa sposoby:  
  
- `catch (RuntimeWrappedException e)` Wewnątrz bloku.
  
     Domyślnie zestaw wizualizacji C# przechwytuje wyjątki niebędące CLS jako wyjątki opakowane. Użyj tej metody, jeśli potrzebujesz dostępu do oryginalnego wyjątku, do którego można uzyskać dostęp za pomocą <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> właściwości. Procedura w dalszej części tego tematu wyjaśnia, jak przechwytywać wyjątki w ten sposób.  
  
- W obrębie ogólnego bloku catch (blok catch bez określonego typu wyjątku) jest umieszczany po wszystkich pozostałych `catch` blokach.
  
     Tej metody należy użyć, gdy chcesz wykonać pewne działania (takie jak zapis w pliku dziennika) w odpowiedzi na wyjątki nienależące do CLS i nie potrzebujesz dostępu do informacji o wyjątku. Domyślnie środowisko uruchomieniowe języka wspólnego otacza wszystkie wyjątki. Aby wyłączyć to zachowanie, Dodaj ten atrybut poziomu zestawu do kodu, zazwyczaj w pliku AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>Aby przechwycić wyjątek niezgodny ze specyfikacją CLS  
  
W bloku Uzyskuj dostęp do oryginalnego wyjątku <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> przez właściwość. `catch(RuntimeWrappedException e)`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przechwytywać wyjątek niezgodny ze specyfikacją CLS zgłoszoną przez bibliotekę klas zapisaną C++w/CLI. Należy zauważyć, że w tym przykładzie C# kod klienta wie z wyprzedzeniem, że zwracany typ wyjątku to <xref:System.String?displayProperty=nameWithType>. Można rzutować Właściwość <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> z powrotem na oryginalny typ, o ile ten typ jest dostępny z kodu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [Wyjątki i obsługa wyjątków](./index.md)
