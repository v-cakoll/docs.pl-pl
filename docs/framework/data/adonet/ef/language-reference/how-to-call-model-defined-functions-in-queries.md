---
title: 'Instrukcje: Wywoływanie funkcji definiowanych przez model w zapytaniach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 2fe0360a0548bddb0ebba566eca0d121c9ec9160
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300622"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Instrukcje: Wywoływanie funkcji definiowanych przez model w zapytaniach
W tym temacie opisano sposób wywołania funkcji, które są zdefiniowane w modelu koncepcyjnym z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
 Poniższa procedura zawiera WYSOKOPOZIOMOWY zarys wywoływania funkcji definiowanych przez model z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. W poniższym przykładzie zapewnia więcej szczegółów na temat czynności opisane w procedurze. W procedurze przyjęto założenie, że zdefiniowano funkcję w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Aby wywołać funkcję zdefiniowaną w modelu koncepcyjnym  
  
1. Dodaj powszechnie używaną metodą języka wspólnego (CLR) do aplikacji, która mapuje do funkcji zdefiniowanych w modelu koncepcyjnym. Aby zmapować metody, należy najpierw zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody. Należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametrów atrybutu są odpowiednio nazwę przestrzeni nazw modelu koncepcyjnego i nazwy funkcji w modelu koncepcyjnym. Funkcja rozpoznawania nazw dla programu LINQ jest uwzględniana wielkość liter.  
  
2. Wywołaj funkcję [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób wywołania funkcji, która jest zdefiniowana w modelu koncepcyjnym z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. W przykładzie użyto modelu szkoły. Aby uzyskać informacje na temat modelu szkoły, zobacz [tworzenie przykładowej bazy danych School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) i [generowania edmx School pliku](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 Następująca funkcja modelu koncepcyjnego zwraca liczbę lat, ponieważ został zatrudniony pod kierunkiem instruktora. Aby uzyskać informacje dotyczące dodawania funkcji do modelu koncepcyjnego, zobacz [jak: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Przykład  
 Następnie dodaj następującą metodę do aplikacji i użyj <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> celu zamapowania go do funkcji modelu koncepcyjnego:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Przykład  
 Teraz można wywołać funkcję modelu koncepcyjnego z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. Poniższy kod wywołuje metodę w celu wyświetlenia wszystkich instruktorów, które zostały wynajęte ponad dziesięć lat temu:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie pliku edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Instrukcje: Wywoływanie funkcji definiowanych przez Model jako metod obiektu](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
