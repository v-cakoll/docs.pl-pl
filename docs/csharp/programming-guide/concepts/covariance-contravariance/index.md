---
title: Kowariancja i Kontrawariancja (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: bfd78b1a32b9d4fe11b1dce129c24ceb5aca6754
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="covariance-and-contravariance-c"></a>Kowariancja i Kontrawariancja (C#)
Kowariancja i kontrawariancja w języku C#, Włącz niejawnej konwersji odwołania dla tablic, typów delegowanych i argumentów typu ogólnego. Kowariancja zachowuje zgodność przypisania i kontrawariancja odwraca go.  
  
 Poniższy kod przedstawia różnicę między zgodności przypisania, Kowariancja i kontrawariancja.  
  
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
  
 Kowariancja dla tablic umożliwia niejawna konwersja tablicy typu bardziej pochodnego do tablicy typu mniej pochodnego. Jednak ta operacja nie jest typem bezpieczne, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Kowariancja i kontrawariancja obsługę grupy metod umożliwia dopasowywanie podpisy metod typów delegatów. Ta umożliwia można przypisać do delegatów nie tylko tych metod, które pasują do podpisów, ale również metody, które zwracają się, że więcej pochodnych typów (kowariancja) lub że akceptujesz parametrów, które mają mniej typów pochodnych (kontrawariancja) od określonej przez typ delegata. Aby uzyskać więcej informacji, zobacz [wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje Kowariancja i kontrawariancja obsługę dla grupy metod.  
  
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
  
 W programie .NET Framework 4 lub nowszej C# obsługuje Kowariancja i kontrawariancja w interfejsach i delegatów i umożliwia niejawnej konwersji wartości parametrów typu ogólnego. Aby uzyskać więcej informacji, zobacz [wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje niejawnej konwersji odwołania dla ogólnych interfejsów.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Ogólny interfejs lub delegat jest nazywany *variant* jeśli jego parametrów ogólnych są deklarowane jako kowariantnego lub kontrawariantnego. C# umożliwia tworzenie własnych interfejsów typu variant i delegatów. Aby uzyskać więcej informacji, zobacz [Tworzenie interfejsów ogólnych typu Variant (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) i [wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Zawiera omówienie Kowariancja i kontrawariancja w interfejsach, a także listę interfejsów ogólnych typu variant w programie .NET Framework.|  
|[Tworzenie interfejsów ogólnych typu Variant (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Przedstawia sposób tworzenia niestandardowych interfejsów typu variant.|  
|[Korzystanie z wariancji w interfejsach dla kolekcji (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Pokazuje, jak obsługują Kowariancja i kontrawariancja w <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> interfejsy ułatwia ponowne użycie kodu.|  
|[Wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Zawiera omówienie Kowariancja i kontrawariancja w delegatach ogólne i inny niż ogólny, a także listę variant delegatów w programie .NET Framework.|  
|[Korzystanie z wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Pokazano, jak korzystać z obsługi Kowariancja i kontrawariancja w delegatach nieogólnego odpowiadać podpisy metod typów delegatów.|  
|[Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Pokazuje, jak obsługują Kowariancja i kontrawariancja w `Func` i `Action` delegatów ułatwia ponowne użycie kodu.|
