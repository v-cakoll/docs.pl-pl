---
title: 'Porady: Wywołaj funkcje zdefiniowane przez Model, jako metody obiektów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 055b77697a525fd2d94192ff5b1586c885b22f94
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763374"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a>Porady: Wywołaj funkcje zdefiniowane przez Model, jako metody obiektów
W tym temacie opisano, jak może wywołać funkcję zdefiniowaną w modelu jako metody <xref:System.Data.Objects.ObjectContext> obiektu lub jako metoda statyczna na klasę niestandardową. A *funkcja zdefiniowana przez model* jest funkcją, która jest zdefiniowana w modelu koncepcyjnym. Procedury przedstawione w tym temacie opisano sposób wywoływać te funkcje, zamiast bezpośredniego wywoływania je z poziomu składnika LINQ do jednostek zapytań. Aby dowiedzieć się, jak wywoływanie funkcji zdefiniowanej w modelu w składniku LINQ do jednostek zapytań, zobacz [porady: funkcje Call Model-Defined w zapytaniach](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).  
  
 Czy wywołanie funkcji zdefiniowanej w modelu jako <xref:System.Data.Objects.ObjectContext> metody lub jako metody statycznej klasy niestandardowej, trzeba najpierw zmapować metoda funkcji zdefiniowanej przez model <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Jednak gdy należy zdefiniować metodę <xref:System.Data.Objects.ObjectContext> klasy, należy użyć <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> właściwości do udostępnienia dostawcy LINQ, natomiast podczas definiowania statycznej metody na klasę niestandardową, należy użyć <xref:System.Linq.IQueryable.Provider%2A> właściwości do udostępnienia dostawcy LINQ. Aby uzyskać więcej informacji zobacz przykłady, które należy wykonać procedury opisane poniżej.  
  
 Poniższych procedur zapewnienia wysokiego poziomu opisanych wywoływanie funkcji zdefiniowanej w modelu jako metody na <xref:System.Data.Objects.ObjectContext> obiektu i jako metoda statyczna na klasę niestandardową. Przykłady, które należy wykonać zawierają więcej szczegółów na temat kroków w procedurach. W procedurach założono, że funkcja ma zdefiniowany w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie funkcje niestandardowe w modelu koncepcyjnym](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a>Wywoływanie funkcji zdefiniowanej w modelu jako metody do obiektu ObjectContext  
  
1.  Dodaj plik źródłowy, aby rozszerzyć pochodzi od klasy częściowej <xref:System.Data.Objects.ObjectContext> klasy wygenerowana automatycznie przez narzędzia Entity Framework. Definiowanie CLR stub w pliku źródłowym oddzielne uniemożliwi zmiany utratę gdy plik zostanie ponownie wygenerowany.  
  
2.  Dodaj wspólne języka wspólnego (CLR) metodę z <xref:System.Data.Objects.ObjectContext> klasy, która wykonuje następujące czynności:  
  
    -   Mapowana na funkcję zdefiniowaną w modelu koncepcyjnym. Aby mapować metody, należy zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody. Należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> atrybutu są odpowiednio nazwę przestrzeni nazw modelu koncepcyjnego i nazwa funkcji w modelu koncepcyjnym. Funkcja rozpoznawania nazw dla LINQ jest rozróżniana wielkość liter.  
  
    -   Zwraca wyniki <xref:System.Linq.IQueryProvider.Execute%2A> metodę, która jest zwracana w wyniku <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> właściwości.  
  
3.  Wywołaj metodę jako element członkowski w wystąpieniu <xref:System.Data.Objects.ObjectContext> klasy.  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a>Wywoływanie funkcji zdefiniowanej w modelu jako metoda statyczna na klasę niestandardową  
  
1.  Dodaj klasę do aplikacji z metodą statyczną, która wykonuje następujące czynności:  
  
    -   Mapowana na funkcję zdefiniowaną w modelu koncepcyjnym. Aby mapować metody, należy zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody. Należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> atrybutu są odpowiednio nazwę przestrzeni nazw modelu koncepcyjnego i nazwa funkcji w modelu koncepcyjnym.  
  
    -   Akceptuje <xref:System.Linq.IQueryable> argumentu.  
  
    -   Zwraca wyniki <xref:System.Linq.IQueryProvider.Execute%2A> metodę, która jest zwracana w wyniku <xref:System.Linq.IQueryable.Provider%2A> właściwości.  
  
2.  Wywołaj metodę jako element członkowski metody statycznej klasy niestandardowej  
  
## <a name="example"></a>Przykład  
 **Wywołanie funkcji zdefiniowanej w modelu jako metody do obiektu ObjectContext**  
  
 W poniższym przykładzie pokazano, jak może wywołać funkcję zdefiniowaną w modelu jako metody <xref:System.Data.Objects.ObjectContext> obiektu. W przykładzie użyto [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).  
  
 Należy wziąć pod uwagę, że funkcja modelu koncepcyjnego poniżej zwraca przychód produktu dla określonego produktu. (Aby uzyskać informacje dotyczące dodawania funkcji do modelu koncepcyjnego, zobacz [jak: Zdefiniuj funkcje niestandardowe w modelu koncepcyjnym](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a>Przykład  
 Poniższy kod dodaje metodę `AdventureWorksEntities` klasy, który jest mapowany na funkcję modelu koncepcyjnego powyżej.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod wywołuje metodę powyżej, aby wyświetlić przychód produktu dla określonego produktu:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wywołania funkcji zdefiniowanych w modelu, która zwraca kolekcję (jako <xref:System.Linq.IQueryable%601> obiektu). Należy wziąć pod uwagę poniższe funkcji modelu koncepcyjnego, która zwraca wszystkie `SalesOrderDetails` identyfikatora danego produktu.  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod dodaje metodę `AdventureWorksEntities` klasy, który jest mapowany na funkcję modelu koncepcyjnego powyżej.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod wywołuje metodę. Należy pamiętać, że zwracana <xref:System.Linq.IQueryable%601> zapytania jest dalsze wprowadzono ulepszenia zwracać sumy wiersza dla każdego `SalesOrderDetail`.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a>Przykład  
 **Wywołanie funkcji zdefiniowanej w modelu jako metoda statyczna na klasę niestandardową**  
  
 Kolejnym przykładzie pokazano, jak wywołać funkcję zdefiniowaną w modelu jako metoda statyczna na klasę niestandardową. W przykładzie użyto [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).  
  
> [!NOTE]
>  Jeśli wywołujesz funkcję zdefiniowaną w modelu jako metody statycznej klasy niestandardowej funkcji zdefiniowanej przez model musi zaakceptować kolekcji i zwracać agregacji wartości w kolekcji.  
  
 Należy wziąć pod uwagę, że funkcja modelu koncepcyjnego poniżej zwraca przychodu produktu dla zbioru szczegóły zamówienia sprzedaży. (Aby uzyskać informacje dotyczące dodawania funkcji do modelu koncepcyjnego, zobacz [jak: Zdefiniuj funkcje niestandardowe w modelu koncepcyjnym](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).).  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a>Przykład  
 Poniższy kod dodaje klasę do aplikacji, która zawiera metody statycznej, który jest mapowany na funkcję modelu koncepcyjnego powyżej.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod wywołuje metodę powyżej, aby wyświetlić przychody produktu dla zbioru szczegóły zamówienia sprzedaży:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie plików edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
