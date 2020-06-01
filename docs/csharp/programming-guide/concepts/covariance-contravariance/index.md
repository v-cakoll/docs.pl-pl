---
title: Kowariancja i kontrawariancja (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 23633675059b9c295dda7ddf3d78754c0223f5f8
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241373"
---
# <a name="covariance-and-contravariance-c"></a>Kowariancja i kontrawariancja (C#)
W języku C#, Kowariancja i kontrawariancja umożliwiają włączenie niejawnej konwersji odwołań dla typów tablic, typów delegatów i argumentów typu ogólnego. Kowariancja zachowuje zgodność przypisania i kontrawariancja ją odwraca.  
  
 Poniższy kod ilustruje różnicę między zgodnością przypisania, kowariancją i kontrawariancja.  
  
```csharp  
// Assignment compatibility.
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.
object obj = str;  
  
// Covariance.
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument
// is assigned to an object instantiated with a less derived type argument.
// Assignment compatibility is preserved.
IEnumerable<object> objects = strings;  
  
// Contravariance.
// Assume that the following method is in the class:
// static void SetObject(object o) { }
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument
// is assigned to an object instantiated with a more derived type argument.
// Assignment compatibility is reversed.
Action<string> actString = actObject;  
```  
  
 Kowariancja dla tablic umożliwia niejawną konwersję tablicy o bardziej pochodny typ do tablicy mniej pochodnego typu. Ale ta operacja nie jest bezpieczna, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Obsługa kowariancji i kontrawariancja dla grup metod umożliwia dopasowywanie sygnatur metod przy użyciu typów delegatów. Dzięki temu można przypisywać do delegatów nie tylko metod, które mają pasujące podpisy, ale również metody, które zwracają więcej typów pochodnych (Kowariancja) lub akceptują parametry, które mają mniej pochodne typy (kontrawariancja) niż określone przez typ delegata. Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (c#)](./variance-in-delegates.md) i [Korzystanie z wariancji w delegatach (c#)](./using-variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje kowariancję i obsługę kontrawariancja dla grup metod.  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 W .NET Framework 4 i nowszych wersjach język C# obsługuje kowariancję i kontrawariancja w interfejsach ogólnych i delegatach i umożliwia niejawną konwersję parametrów typu ogólnego. Aby uzyskać więcej informacji, zobacz [Wariancja w interfejsach ogólnych (c#)](./variance-in-generic-interfaces.md) i [Wariancja w delegatach (c#)](./variance-in-delegates.md).  
  
 Poniższy przykład kodu przedstawia niejawną konwersję odwołań dla interfejsów ogólnych.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Ogólny interfejs lub delegat jest nazywany *wariantem* , jeśli jego parametry ogólne są zadeklarowane jako współvariant lub kontrawariantne. Język C# umożliwia tworzenie własnych interfejsów i delegatów wariantów. Aby uzyskać więcej informacji, zobacz [Tworzenie wariantów ogólnych interfejsów (c#)](./creating-variant-generic-interfaces.md) i [Wariancja w delegatach (c#)](./variance-in-delegates.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wariancja w interfejsach ogólnych (C#)](./variance-in-generic-interfaces.md)|Omawia kowariancję i kontrawariancja w interfejsach ogólnych i zawiera listę podstawowych interfejsów w .NET Framework.|  
|[Tworzenie interfejsów ogólnych typu Variant (C#)](./creating-variant-generic-interfaces.md)|Pokazuje, jak utworzyć niestandardowe interfejsy wariantów.|  
|[Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)](./using-variance-in-interfaces-for-generic-collections.md)|Pokazuje, jak Kowariancja i obsługa kontrawariancja w <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IComparable%601> interfejsie i mogą ułatwić ponowne użycie kodu.|  
|[Wariancja w delegatach (C#)](./variance-in-delegates.md)|Omawia kowariancję i kontrawariancja w obiektach ogólnych i nieogólnych oraz zawiera listę delegatów ogólnych typu Variant w .NET Framework.|  
|[Korzystanie z wariancji w delegatach (C#)](./using-variance-in-delegates.md)|Pokazuje, w jaki sposób używać kowariancji i obsługi kontrawariancja w delegatach innych niż ogólne do dopasowywania sygnatur metod z typami delegatów.|  
|[Korzystanie z wariancji dla delegatów funkcji Func i Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)|Pokazuje, jak Kowariancja i obsługa kontrawariancja w `Func` `Action` delegatach i mogą ułatwić ponowne użycie kodu.|
