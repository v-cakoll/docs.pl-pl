---
title: 'Instrukcje: Wywoływanie funkcji definiowanych przez model w zapytaniach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 33f26896dd0d4ff08beb4a011fa6bd468cba7207
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250754"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Instrukcje: Wywoływanie funkcji definiowanych przez model w zapytaniach
W tym temacie opisano, jak wywoływać funkcje, które są zdefiniowane w modelu koncepcyjnym z zapytań LINQ to Entities.  
  
 Poniższa procedura zawiera konspekt wysokiego poziomu służący do wywoływania funkcji zdefiniowanej przez model z poziomu zapytania LINQ to Entities. Poniższy przykład zawiera bardziej szczegółowe informacje na temat kroków w procedurze. W procedurze przyjęto założenie, że zdefiniowano funkcję w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [jak: Zdefiniuj funkcje niestandardowe w modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))koncepcyjnym.  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Aby wywołać funkcję zdefiniowaną w modelu koncepcyjnym  
  
1. Dodaj do aplikacji metodę środowiska uruchomieniowego języka wspólnego (CLR), która jest mapowana na funkcję zdefiniowaną w modelu koncepcyjnym. Aby zmapować metodę, należy zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody. Należy zauważyć, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry i atrybutu są nazwą przestrzeni nazw modelu koncepcyjnego i nazwą funkcji w modelu koncepcyjnym odpowiednio. Rozpoznawanie nazw funkcji dla LINQ jest rozróżniana wielkość liter.  
  
2. Wywołaj funkcję w kwerendzie LINQ to Entities.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób wywołania funkcji zdefiniowanej w modelu koncepcyjnym z poziomu zapytania LINQ to Entities. W przykładzie zastosowano model szkoły. Aby uzyskać informacje o modelu szkoły, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) i [generowanie pliku szkoły. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 Poniższa funkcja modelu koncepcyjnego zwraca liczbę lat od momentu zatrudnienia instruktora. Aby uzyskać informacje na temat dodawania funkcji do modelu koncepcyjnego, [zobacz How to: Zdefiniuj funkcje niestandardowe w modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))koncepcyjnym.  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Przykład  
 Następnie Dodaj następującą metodę do aplikacji i Użyj <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metody, aby zamapować ją na funkcję modelu koncepcyjnego:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Przykład  
 Teraz można wywołać funkcję modelu koncepcyjnego z poziomu zapytania LINQ to Entities. Poniższy kod wywołuje metodę w celu wyświetlenia wszystkich instruktorów, którzy zostali zatrudnieni ponad dziesięć lat temu:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Plik. edmx — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
- [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
- [Instrukcje: Wywołaj funkcje zdefiniowane przez model jako metody obiektów](how-to-call-model-defined-functions-as-object-methods.md)
