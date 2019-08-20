---
title: Porównania równości — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: bc3ce4b94bfc72e058d4660d01eb16ef0e0f11db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588720"
---
# <a name="equality-comparisons-c-programming-guide"></a>Porównania równości (C# Przewodnik programowania)

Czasami trzeba porównać dwie wartości pod kątem równości. W niektórych przypadkach testowanie pod kątem *równości wartości*, nazywane również równoważeniem,co oznacza, że wartości, które są zawarte w dwóch zmiennych są równe. W innych przypadkach należy określić, czy dwie zmienne odwołują się do tego samego bazowego obiektu w pamięci. Równość tego typu jest nazywana *równość odwołania*lub *tożsamością*. W tym temacie opisano te dwa rodzaje równości i przedstawiono linki do innych tematów, aby uzyskać więcej informacji.  
  
## <a name="reference-equality"></a>Równość odwołania

 Równość odniesienia oznacza, że dwa odwołania do obiektów odwołują się do tego samego obiektu podstawowego. Może to być spowodowane przypisaniem prostym, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 W tym kodzie tworzone są dwa obiekty, ale po instrukcji przypisania obydwa odwołania odnoszą się do tego samego obiektu. W związku z tym mają równość odwołań. Użyj metody <xref:System.Object.ReferenceEquals%2A> , aby określić, czy dwa odwołania odwołują się do tego samego obiektu.  
  
 Koncepcja równości odwołań dotyczy tylko typów referencyjnych. Obiekty typu wartości nie mogą mieć równości odwołań, ponieważ gdy wystąpienie typu wartości jest przypisane do zmiennej, zostanie wykonana kopia wartości. W związku z tym nigdy nie można mieć dwóch nieopakowanych struktur odwołujących się do tej samej lokalizacji w pamięci. Ponadto, jeśli używasz <xref:System.Object.ReferenceEquals%2A> do porównywania dwóch typów wartości, wynik będzie `false`zawsze, nawet jeśli wartości, które są zawarte w obiektach są identyczne. Jest to spowodowane tym, że każda zmienna jest opakowana w oddzielnym wystąpieniu obiektu. Aby uzyskać więcej informacji, zobacz [jak: Test pod kątem równości odwołań (tożsamość](./how-to-test-for-reference-equality-identity.md)).  

## <a name="value-equality"></a>Równość wartości

 Równość wartości oznacza, że dwa obiekty zawierają tę samą wartość lub wartości. W przypadku typów wartości pierwotnych, takich jak [int](../../language-reference/builtin-types/integral-numeric-types.md) lub [bool](../../language-reference/keywords/bool.md), testy pod kątem równości wartości są bezpośrednie. Możesz użyć [==](../../language-reference/operators/equality-operators.md#equality-operator-) operatora, jak pokazano w poniższym przykładzie.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 W przypadku większości innych typów testowanie pod kątem równości wartości jest bardziej skomplikowane, ponieważ wymaga zrozumienia sposobu jego definiowania. Dla klas i struktur, które mają wiele pól lub właściwości, równość wartości jest często zdefiniowana tak, aby oznaczało, że wszystkie pola lub właściwości mają tę samą wartość. Na przykład dwa `Point` obiekty mogą być zdefiniowane jako równoważne, jeśli punkt a. x jest równy pointB. x, a punkt a. y jest równy pointB. y.  
  
 Nie ma jednak potrzeby równoważności na podstawie wszystkich pól w typie. Może ona być oparta na podzestawie. Porównując nieposiadane typy, należy się upewnić, że rozumiesz, w jaki sposób ma być określona równoważność dla tego typu. Aby uzyskać więcej informacji na temat sposobu definiowania równości wartości we własnych klasach i strukturach, [zobacz How to: Zdefiniuj równość wartości dla typu](./how-to-define-value-equality-for-a-type.md).  
  
### <a name="value-equality-for-floating-point-values"></a>Równość wartości dla wartości zmiennoprzecinkowych

 Porównywanie wartości zmiennoprzecinkowych (podwójna[](../../language-reference/builtin-types/floating-point-numeric-types.md) i [zmiennoprzecinkowa](../../language-reference/builtin-types/floating-point-numeric-types.md)) jest problematyczne ze względu na niedokładność arytmetycznych liczb zmiennoprzecinkowych na komputerach binarnych. Aby uzyskać więcej informacji, zobacz uwagi w temacie <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Testowanie równości odwołań (tożsamość)](./how-to-test-for-reference-equality-identity.md)|Opisuje sposób określenia, czy dwie zmienne mają równość odwołania.|  
|[Instrukcje: Definiowanie równości wartości dla typu](./how-to-define-value-equality-for-a-type.md)|Opisuje, jak zapewnić niestandardową definicję równości wartości dla typu.|  
|[Przewodnik programowania w języku C#](../index.md)|Zawiera linki do szczegółowych informacji na temat C# ważnych funkcji i funkcji języka, które są C# dostępne dla .NET Framework.|  
|[Typy](../types/index.md)|Zawiera informacje o systemie C# typów i linki do dodatkowych informacji.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
