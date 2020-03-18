---
title: Typy anonimowe — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: 63bc5560ba19ff36764465a6b89b81c13beec97a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170341"
---
# <a name="anonymous-types-c-programming-guide"></a>Typy anonimowe (Przewodnik programowania w języku C#)

Typy anonimowe zapewniają wygodny sposób hermetyzacji zestawu właściwości tylko do odczytu w jeden obiekt bez konieczności jawnie zdefiniować typ pierwszy. Nazwa typu jest generowany przez kompilator i nie jest dostępna na poziomie kodu źródłowego. Typ każdej właściwości jest wywnioskowany przez kompilator.  
  
 Typy anonimowe można tworzyć przy użyciu [nowego](../../language-reference/operators/new-operator.md) operatora wraz z inicjatora obiektu. Aby uzyskać więcej informacji na temat inicjatorów obiektów, zobacz [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md).  
  
 W poniższym przykładzie przedstawiono typ anonimowy, który `Amount` jest `Message`inicjowany z dwiema właściwościami o nazwie i .  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Typy anonimowe są zazwyczaj używane w [select](../../language-reference/keywords/select-clause.md) klauzuli wyrażenia kwerendy, aby zwrócić podzbiór właściwości z każdego obiektu w sekwencji źródłowej. Aby uzyskać więcej informacji na temat zapytań, zobacz [LINQ w języku C#](../../linq/index.md).  
  
 Typy anonimowe zawierają co najmniej jedną publiczną właściwości tylko do odczytu. Żadne inne rodzaje elementów członkowskich klasy, takich jak metody lub zdarzenia, są prawidłowe. Wyrażenie, które jest używane do inicjowania `null`właściwości nie może być , funkcja anonimowa lub typ wskaźnika.  
  
 Najczęstszym scenariuszem jest zainicjowanie typu anonimowego z właściwościami innego typu. W poniższym przykładzie załóżmy, że `Product`istnieje klasa o nazwie . Obejmuje `Product` `Color` klasę `Price` i właściwości, wraz z innymi właściwościami, które nie są zainteresowane. Zmienna `products` jest `Product` kolekcją obiektów. Deklaracja typu anonimowego `new` rozpoczyna się od słowa kluczowego. Deklaracja inicjuje nowy typ, który używa `Product`tylko dwóch właściwości z . Powoduje to mniejszą ilość danych, które mają być zwracane w kwerendzie.  
  
 Jeśli nie określisz nazwy elementów członkowskich w typie anonimowym, kompilator daje członków typu anonimowego taką samą nazwę jak właściwość używana do ich inicjowania. Należy podać nazwę właściwości, która jest inicjowana z wyrażeniem, jak pokazano w poprzednim przykładzie. W poniższym przykładzie nazwy właściwości typu anonimowego `Color` są `Price`i .  
  
 [!code-csharp[csRef30Features#81](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csRef30Features/CS/csref30.cs#81)]  
  
 Zazwyczaj, gdy używasz typu anonimowego do inicjowania zmiennej, deklarujesz zmienną jako niejawnie wpisaną zmienną lokalną przy użyciu [var](../../language-reference/keywords/var.md). Nie można określić nazwy typu w deklaracji zmiennej, ponieważ tylko kompilator ma dostęp do podstawowej nazwy typu anonimowego. Aby uzyskać `var`więcej informacji na temat , zobacz [Niejawnie wpisane zmienne lokalne](./implicitly-typed-local-variables.md).  
  
 Tablicę elementów wpisanych anonimowo można utworzyć, łącząc niejawnie wpisaną zmienną lokalną z tablicą wpisaną niejawnie, jak pokazano w poniższym przykładzie.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Uwagi  
 Typy anonimowe są typami [klas,](../../language-reference/keywords/class.md) które pochodzą bezpośrednio z [obiektu](../../language-reference/builtin-types/reference-types.md)i których nie można rzutować na dowolny typ z wyjątkiem [obiektu.](../../language-reference/builtin-types/reference-types.md) Kompilator zawiera nazwę dla każdego typu anonimowego, mimo że aplikacja nie może uzyskać do niego dostępu. Z punktu widzenia wspólnego języka wykonywania typu anonimowego nie różni się od innego typu odwołania.  
  
 Jeśli dwa lub więcej anonimowych inicjatorów obiektów w zestawie określić sekwencję właściwości, które są w tej samej kolejności i które mają te same nazwy i typy, kompilator traktuje obiekty jako wystąpienia tego samego typu. Mają one te same informacje o typie generowanym przez kompilator.  
  
 Nie można zadeklarować pola, właściwości, zdarzenia lub typu zwracanego metody jako typu anonimowego. Podobnie nie można zadeklarować formalny parametr metody, właściwości, konstruktora lub indeksatora jako o typie anonimowym. Aby przekazać typ anonimowy lub kolekcję zawierającą typy anonimowe jako argument metody, można zadeklarować parametr jako obiekt typu. Jednak w ten sposób pokonuje cel silnego pisania. Jeśli musisz przechowywać wyniki kwerendy lub przekazać je poza granicami metody, należy rozważyć użycie zwykłej struktury lub klasy o nazwie zamiast typu anonimowego.  
  
 Ponieważ <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> metody na typy anonimowe są `Equals` zdefiniowane `GetHashCode` w kategoriach i metody właściwości, dwa wystąpienia tego samego typu anonimowego są równe tylko wtedy, gdy wszystkie ich właściwości są równe.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md)
- [Wprowadzenie do korzystania z LINQ w C#](../concepts/linq/index.md)
- [LINQ w C#](../../linq/index.md)
