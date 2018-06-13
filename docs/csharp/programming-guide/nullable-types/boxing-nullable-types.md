---
title: Konwersja boxing typów dopuszczających wartości zerowe (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
ms.openlocfilehash: e2c7602bf45f1861d3a32a73824e9fedf0a4d29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334759"
---
# <a name="boxing-nullable-types-c-programming-guide"></a>Konwersja boxing typów dopuszczających wartości zerowe (Przewodnik programowania w języku C#)
Obiekty na podstawie typów wartości null są opakowany tylko, jeśli obiekt jest inne niż null. Jeśli <xref:System.Nullable%601.HasValue%2A> jest `false`, odwołanie do obiektu jest przypisany do `null` zamiast boxing. Na przykład:  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 Jeśli obiekt jest różna od null — Jeśli <xref:System.Nullable%601.HasValue%2A> jest `true` — następnie konwersja boxing występuje, ale tylko na podstawie wartości null obiekt podstawowy typ jest opakowany. Konwersja boxing typ innych niż null wartości null wartości pola typu wartości, nie <xref:System.Nullable%601?displayProperty=nameWithType> zawija się typ wartości. Na przykład:  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 Dwa obiekty opakowanego są takie same jak te utworzone przez boxing typów wartości null. I tak samo jak typy opakowanego wartości null, mogą być rozpakowany do typów dopuszczających wartości zerowe, jak w poniższym przykładzie:  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a>Uwagi  
 Zachowanie typy dopuszczające wartości null, gdy opakowany dwie zalety:  
  
1.  Dopuszczające wartości zerowe obiektów i ich odpowiednika ramce można sprawdzane pod kątem wartości null:  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  Opakowany typy dopuszczające wartości zerowe obsługują w pełni funkcje typ bazowy:  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)  
 [Instrukcje: identyfikowanie typu dopuszczającego wartość null](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
