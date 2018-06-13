---
title: extern (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 996888a585f8355bdda14e09b6bb9544257ae824
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172296"
---
# <a name="extern-c-reference"></a>extern (odwołanie w C#)
`extern` Modyfikator służy do deklarowania metodę, która jest zaimplementowana zewnętrznie. Typowym zastosowaniem `extern` modyfikator jest z `DllImport` atrybutu podczas korzystania z międzyoperacyjnego usług do wywołania do kodu niezarządzanego. W tym przypadku metoda również musi być zadeklarowany jako `static`, jak pokazano w poniższym przykładzie:  
  
```csharp  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 `extern` — Słowo kluczowe można również zdefiniować aliasu zewnętrznego zestawu, dzięki czemu można odwoływać się różne wersje tego samego składnika od w jednym zestawie. Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](../../../csharp/language-reference/keywords/extern-alias.md).  
  
 Jest błędem [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md) i `extern` Modyfikatory ze sobą, aby zmodyfikować tego samego członka. Przy użyciu `extern` modyfikator oznacza, że metoda jest wykonywane poza kodu C# natomiast przy użyciu `abstract` modyfikator oznacza, że implementacja metody nie jest dostępny w klasie.  
  
 Użycie słowa kluczowego extern podlega większym ograniczeniom w języku C# niż w języku C++. Aby porównać to słowo kluczowe w języku C# z wersją w języku C++, zobacz temat „Używanie słowa kluczowego extern w celu określenia powiązania” w dokumentacji języka C++.  
  
## <a name="example"></a>Przykład  
 **Przykład 1.** W tym przykładzie program odbiera ciąg od użytkownika i wyświetla go w oknie komunikatu. Program używa `MessageBox` zaimportowany z biblioteki User32.dll metody.  
  
 [!code-csharp[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]  
  
## <a name="example"></a>Przykład  
 **Przykład 2.** W tym przykładzie przedstawiono program C#, który odwołuje się do biblioteki C (natywnej biblioteki DLL).  
  
 1. Utworzyć następującego pliku C i nadaj mu nazwę `cmdll.c`:  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a>Przykład  
 2. Otwórz okno Wiersz polecenia narzędzi natywnego x64 (lub x32) programu Visual Studio z poziomu katalogu instalacyjnego programu Visual Studio i skompilować `cmdll.c` pliku, wpisując **cl /LD cmdll.c** w wierszu polecenia.  
  
 3. W tym samym katalogu, należy utworzyć następującego pliku C# i nadaj jej nazwę `cm.cs`:  
  
```csharp  
// cm.cs  
using System;  
using System.Runtime.InteropServices;  
public class MainClass   
{  
   [DllImport("Cmdll.dll")]  
   public static extern int SampleMethod(int x);  
  
   static void Main()   
   {  
      Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));  
   }  
}  
```  
  
## <a name="example"></a>Przykład  
 3. Otwórz okno Wiersz polecenia narzędzi natywnego x64 (lub x32) programu Visual Studio z poziomu katalogu instalacyjnego programu Visual Studio i skompilować `cm.cs` pliku, wpisz:  
  
> **CSC cm.cs** (dla x64 wiersza polecenia)   
>  —lub—  
> **CSC — x 86 cm.cs** (dla x32 wiersza polecenia)  
  
 Spowoduje to utworzenie pliku wykonywalnego `cm.exe`.  
  
 4. Run `cm.exe`. `SampleMethod` Metoda przekazuje wartość 5 do pliku DLL, która zwraca wartość pomnożona przez 10.  Program tworzy następujące dane wyjściowe:  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
