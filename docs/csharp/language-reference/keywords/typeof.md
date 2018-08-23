---
title: typeof (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 4203b597d7045a13ffed9e61ddbbde57e2113c23
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753986"
---
# <a name="typeof-c-reference"></a>typeof (odwołanie w C#)
Uzywany do uzyskania obiektu `System.Type` dla typu. Wyrazenie `typeof` ma nastepujaca postac:  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskac typ srodowiska wykonawczego wyrazenia, mozna uzyc metody .NET Framework <xref:System.Object.GetType%2A> — jak w ponizszym przykladzie:  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 Operator `typeof` nie moze byc przeciazony.  
  
 Operatora `typeof` mozna tez uzywac na otwartych typach ogólnych. Typy z wiecej niz jednym parametrem typu musza zawierac odpowiednia liczbe przecinków w specyfikacji. W przykladzie ponizej pokazujemy, jak ustalic, czy zwracanym typem metody jest ogólny typ <xref:System.Collections.Generic.IEnumerable%601>. Zalózmy, ze metoda jest wystapieniem typu MethodInfo:  
  
```csharp  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a>Przykład  
 W przykladzie uzyto metody <xref:System.Object.GetType%2A>, aby okreslic typ, który jest zwracany jako wynik obliczenia. Zalezy to od wymagan przechowywania zwiazanych z wynikowa liczba.  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Type?displayProperty=nameWithType>  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)
