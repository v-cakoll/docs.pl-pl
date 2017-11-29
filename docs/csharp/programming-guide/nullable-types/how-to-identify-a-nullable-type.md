---
title: "Porady: identyfikowanie typu dopuszczającego wartość zerową (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 610ed18308df02c5632361cd09ef94330dea598b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md)  
 [Konwersja boxing typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
