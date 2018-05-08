---
title: 'Porady: identyfikowanie typu dopuszczającego wartość zerową (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: f3ac4ebd77fc92a133eb326919d5ba55264ced97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Porady: identyfikowanie typu dopuszczającego wartość zerową (Przewodnik programowania w języku C#)
Można użyć języka C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operatora do utworzenia <xref:System.Type> obiekt, który reprezentuje typ dopuszczający wartość null:  
  
```  
System.Type type = typeof(int?);  
```  
  
 Można również użyć klasy i metody <xref:System.Reflection> przestrzeni nazw, aby wygenerować <xref:System.Type> obiektów, które reprezentują typy dopuszczające wartości zerowe. Jednak Jeśli spróbujesz uzyskać informacji o typie z wartości null zmienne w czasie wykonywania za pomocą <xref:System.Object.GetType%2A> — metoda lub `is` operatora, wynikiem jest <xref:System.Type> obiekt, który reprezentuje typ podstawowy nie Nullable wpisz samej siebie.  
  
 Wywoływanie `GetType` na typu Nullable typu powoduje, że na opakowanie operacji można wykonać, gdy typ jest niejawnie przekonwertowana na <xref:System.Object>. W związku z tym <xref:System.Object.GetType%2A> zawsze zwraca <xref:System.Type> obiekt, który reprezentuje typ podstawowy typ dopuszczający wartość null.  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 C# [jest](../../../csharp/language-reference/keywords/is.md) operator również działa na typ podstawowy typu Nullable. W związku z tym nie można użyć `is` do ustalenia, czy zmienna jest typu dopuszczającego wartość null. W poniższym przykładzie pokazano, że `is` operator traktuje typu Nullable\<int > zmiennej jako int.  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod umożliwia określenie, czy <xref:System.Type> obiekt reprezentuje typ dopuszczający wartość null. Należy pamiętać, że ten kod zawsze zwraca wartość false, jeśli `Type` obiektu zwróconego przez wywołanie <xref:System.Object.GetType%2A>, jak opisano wcześniej w tym temacie.  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)  
 [Konwersja boxing typów dopuszczających wartości null](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
