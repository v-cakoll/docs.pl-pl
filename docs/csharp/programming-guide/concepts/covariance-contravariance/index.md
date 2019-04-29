---
title: Kowariancja i Kontrawariancja (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: bfd78b1a32b9d4fe11b1dce129c24ceb5aca6754
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668565"
---
# <a name="covariance-and-contravariance-c"></a>Kowariancja i Kontrawariancja (C#)
W C#, kowariancji i kontrawariancji Włącz niejawna konwersja odwołania dla typów tablicy, typy delegatów i argumenty typu ogólnego. Kowariancja zachowuje zgodność przypisania i kontrawariancja odwraca go.  
  
 Poniższy kod ilustruje różnicę między zgodności przypisania, kowariancji i kontrawariancji.  
  
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
  
 Kowariancja dla tablic umożliwia niejawną konwersję tablicę typu bardziej pochodnego do tablicy typu mniej pochodnego. Jednak ta operacja nie jest typem bezpiecznym, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Kowariancja i kontrawariancja obsługę grupy metod umożliwia podpisów metod dopasowania z typów obiektów delegowanych. Dzięki temu można przypisać do delegatów nie tylko tych metod, które pasują do sygnatur, ale także metody, które zwracają czy pochodne więcej typów (korelacja) lub że akceptujesz parametry, które mają mniej pochodne typy (kontrawariancja) niż określona przez typ delegata. Aby uzyskać więcej informacji, zobacz [wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje obsługę kowariancji i kontrawariancji dla grupy metod.  
  
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
  
 W programie .NET Framework 4 lub nowszej C# obsługuje Kowariancja i kontrawariancja w interfejsach ogólnych i delegatach i umożliwia niejawną konwersję parametrów typu genetycznego. Aby uzyskać więcej informacji, zobacz [wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje niejawna konwersja odwołania dla interfejsów ogólnych.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Ogólny interfejs lub delegat jest nazywany *wariant* jeśli jego parametrów ogólnych są deklarowane jako kowariantny lub kontrawariantny. C#pozwala na tworzenie własnych wariantów interfejsów i delegatów. Aby uzyskać więcej informacji, zobacz [Tworzenie interfejsów ogólnych typu Variant (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) i [wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|W tym artykule omówiono Kowariancja i kontrawariancja w interfejsach ogólnych i zawiera listę interfejsów ogólnych typu variant w programie .NET Framework.|  
|[Tworzenie interfejsów typu Variant (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Przedstawia sposób tworzenia niestandardowych interfejsów typu variant.|  
|[Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Pokazuje, jak obsługiwać kowariancji i kontrawariancji w <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> interfejsy mogą pomóc ponowne użycie kodu.|  
|[Wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Omówiono kowariancji i kontrawariancji w delegatach ogólnych i nieogólnych i lista wariantów ogólnych delegatów w programie .NET Framework.|  
|[Korzystanie z wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Pokazuje, jak korzystać z pomocy technicznej kowariancji i kontrawariancji w delegatach nieogólnego do pasowania podpisy metod typy delegatów.|  
|[Korzystanie z wariancji dla Func i akcji delegatów ogólnych (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Pokazuje, jak obsługiwać kowariancji i kontrawariancji w `Func` i `Action` delegatów mogą pomóc ponowne użycie kodu.|
