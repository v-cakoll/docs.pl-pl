---
title: 'Instrukcje: Wywoływanie funkcji definiowanych przez Model w zapytaniach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: febeceefc48d54f52c132e78eaf236b6548656f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514737"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Instrukcje: Wywoływanie funkcji definiowanych przez Model w zapytaniach
W tym temacie opisano sposób wywołania funkcji, które są zdefiniowane w modelu koncepcyjnym z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
 Poniższa procedura zawiera WYSOKOPOZIOMOWY zarys wywoływania funkcji definiowanych przez model z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. W poniższym przykładzie zapewnia więcej szczegółów na temat czynności opisane w procedurze. W procedurze przyjęto założenie, że zdefiniowano funkcję w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Aby wywołać funkcję zdefiniowaną w modelu koncepcyjnym  
  
1.  Dodaj powszechnie używaną metodą języka wspólnego (CLR) do aplikacji, która mapuje do funkcji zdefiniowanych w modelu koncepcyjnym. Aby zmapować metody, należy najpierw zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody. Należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametrów atrybutu są odpowiednio nazwę przestrzeni nazw modelu koncepcyjnego i nazwy funkcji w modelu koncepcyjnym. Funkcja rozpoznawania nazw dla programu LINQ jest uwzględniana wielkość liter.  
  
2.  Wywołaj funkcję [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób wywołania funkcji, która jest zdefiniowana w modelu koncepcyjnym z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. W przykładzie użyto modelu szkoły. Aby uzyskać informacje na temat modelu szkoły, zobacz [tworzenie przykładowej bazy danych School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) i [generowania edmx School pliku](https://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 Następująca funkcja modelu koncepcyjnego zwraca liczbę lat, ponieważ został zatrudniony pod kierunkiem instruktora. Aby uzyskać informacje dotyczące dodawania funkcji do modelu koncepcyjnego, zobacz [jak: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
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
- [Omówienie pliku edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)
- [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Instrukcje: Wywoływanie funkcji definiowanych przez Model jako metod obiektu](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
