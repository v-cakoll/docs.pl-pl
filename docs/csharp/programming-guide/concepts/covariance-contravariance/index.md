---
title: Kowariancja i kontrawariancja (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 80b4d703bb88d0bf1f7f48236c21b7698017e7f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169873"
---
# <a name="covariance-and-contravariance-c"></a>Kowariancja i kontrawariancja (C#)
W języku C#, kowariancja i kontrawariancja umożliwiają niejawną konwersję referencyjną dla typów tablic, typów delegowanych i argumentów typu ogólnego. Kowariancja zachowuje zgodność przypisania i contravariance odwraca go.  
  
 Poniższy kod pokazuje różnicę między zgodnością przypisania, kowariancją i kontrawarancją.  
  
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
  
 Kowariancja dla tablic umożliwia niejawną konwersję tablicy typu bardziej pochodnego do tablicy typu mniej pochodnego. Ale ta operacja nie jest typu bezpieczne, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Obsługa kowariancji i kontrawaracji dla grup metod umożliwia dopasowywanie podpisów metod z typami delegatów. Dzięki temu można przypisać do delegatów nie tylko metody, które mają pasujące podpisy, ale także metody, które zwracają więcej typów pochodnych (kowariancja) lub które akceptują parametry, które mają mniej pochodnych typów (contravariance) niż określone przez typ delegata. Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (C#)](./variance-in-delegates.md) i [Użycie wariancji w delegatach (C#)](./using-variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje obsługę kowariancji i przeciwwariancji dla grup metod.  
  
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
  
 W .NET Framework 4 lub nowszych C# obsługuje kowariancji i kontrawariancji w ogólnych interfejsów i delegatów i umożliwia niejawną konwersję parametrów typu ogólnego. Aby uzyskać więcej informacji, zobacz [Wariancja w interfejsach ogólnych (C#)](./variance-in-generic-interfaces.md) i [Odchylenie w delegatach (C#)](./variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje niejawną konwersję referencyjną dla interfejsów ogólnych.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Ogólny interfejs lub delegat jest nazywany *wariantem,* jeśli jego parametry ogólne są zadeklarowane jako kowariantne lub kontrawariantne. C# umożliwia tworzenie własnych interfejsów warianti i delegatów. Aby uzyskać więcej informacji, zobacz [Tworzenie wariantowych interfejsów ogólnych (C#)](./creating-variant-generic-interfaces.md) i [Odchylenie w delegatach (C#)](./variance-in-delegates.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wariancja w interfejsach ogólnych (C#)](./variance-in-generic-interfaces.md)|W tym artykule omówiono kowariancję i kontrawariancji w interfejsach ogólnych i zawiera listę wariantowych interfejsów ogólnych w .NET Framework.|  
|[Tworzenie wariantowych interfejsów ogólnych (C#)](./creating-variant-generic-interfaces.md)|Pokazuje, jak tworzyć niestandardowe interfejsy wariantowe.|  
|[Używanie wariancji w interfejsach dla kolekcji ogólnych (C#)](./using-variance-in-interfaces-for-generic-collections.md)|Pokazuje, jak obsługa kowariancji i contravariance w <xref:System.Collections.Generic.IEnumerable%601> interfejsach i <xref:System.IComparable%601> może pomóc w ponownym użyciu kodu.|  
|[Wariancja w delegatach (C#)](./variance-in-delegates.md)|W tym artykule omówiono kowariancję i kontrawariancji w delegatów ogólnych i nieogólnych i zawiera listę wariantu delegatów ogólnych w .NET Framework.|  
|[Używanie wariancji w delegatach (C#)](./using-variance-in-delegates.md)|Pokazuje, jak używać obsługi kowariancji i kontrawaracji w delegatach nieogólnych w celu dopasowania podpisów metod do typów delegatów.|  
|[Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)](./using-variance-for-func-and-action-generic-delegates.md)|Pokazuje, jak obsługa kowariancji i contravariance w `Func` delegatów i `Action` może pomóc w ponownym użyciu kodu.|
