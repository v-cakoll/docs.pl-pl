---
title: 'Porady: Wywołaj funkcje zdefiniowane przez Model w zapytaniach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 575c7cff64608257646bde0ef08abe4c0096e477
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Porady: Wywołaj funkcje zdefiniowane przez Model w zapytaniach
W tym temacie opisano sposób wywołania funkcji, które są zdefiniowane w modelu koncepcyjnym z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
 Poniższa procedura zawiera WYSOKOPOZIOMOWY zarys wywoływania funkcję zdefiniowaną w modelu z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. Przykład, w którym następuje zawiera więcej szczegółów na temat czynności opisane w procedurze. W procedurze założono, że funkcja ma zdefiniowany w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie funkcje niestandardowe w modelu koncepcyjnym](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Wywoływanie funkcji zdefiniowanej w modelu koncepcyjnym  
  
1.  Dodaj powszechnie używaną metodą języka wspólnego (CLR) do aplikacji, który jest mapowany na funkcję zdefiniowaną w modelu koncepcyjnym. Aby mapować metody, należy zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody. Należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> atrybutu są odpowiednio nazwę przestrzeni nazw modelu koncepcyjnego i nazwa funkcji w modelu koncepcyjnym. Funkcja rozpoznawania nazw dla LINQ jest rozróżniana wielkość liter.  
  
2.  Wywołanie funkcji [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób wywołania funkcji, która jest zdefiniowana w modelu koncepcyjnym z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. W przykładzie użyto modelu służbowe. Informacje o modelu służbowe, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) i [generowania edmx służbowe pliku](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 Następująca funkcja modelu koncepcyjnego zwraca liczbę lat, ponieważ został dzierżawione instruktora. Aby uzyskać informacje na temat dodawania funkcji do modelu koncepcyjnego, zobacz [porady: Definiowanie funkcje niestandardowe w modelu koncepcyjnym](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Przykład  
 Następnie dodaj następującą metodę do aplikacji i użyj <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do mapowany na funkcję modelu koncepcyjnego:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Przykład  
 Teraz można wywołać funkcję modelu koncepcyjnego z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. Poniższy kod wywołuje metodę w celu wyświetlenia wszystkich instruktorów, którzy zostali zatrudnieni ponad 10 lat temu:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie plików edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Instrukcje: Wywoływanie funkcji definiowanych przez model jako metod obiektu](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
