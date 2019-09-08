---
title: 'Instrukcje: Mapowanie hierarchii dziedziczenia'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1366e8f5f79a8e695e52c405e20a894861453ae7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781767"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Instrukcje: Mapowanie hierarchii dziedziczenia
Aby zaimplementować mapowanie dziedziczenia [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]w programie, należy określić atrybuty i właściwości atrybutów w klasie głównej hierarchii dziedziczenia zgodnie z opisem w poniższych krokach. Deweloperzy korzystający z programu Visual Studio mogą mapować hierarchie dziedziczenia przy użyciu Object Relational Designer. Zobacz [How to: Skonfiguruj dziedziczenie przy użyciu narzędzia O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)Designer.  
  
> [!NOTE]
> Dla podklas nie są wymagane żadne specjalne atrybuty ani właściwości. Należy zwrócić uwagę na <xref:System.Data.Linq.Mapping.TableAttribute> to, że podklasy nie mają atrybutu.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Aby zmapować hierarchię dziedziczenia  
  
1. <xref:System.Data.Linq.Mapping.TableAttribute> Dodaj atrybut do klasy głównej.  
  
2. Także do klasy głównej, Dodaj <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybut dla każdej klasy w strukturze hierarchii.  
  
3. Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> Zdefiniuj właściwość.  
  
     Ta właściwość zawiera wartość, która pojawia się w tabeli bazy danych w <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> kolumnie, aby wskazać klasę lub podklasę, do której należy ten wiersz danych.  
  
4. Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu, należy również <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> dodać właściwość.  
  
     Ta właściwość zawiera wartość określającą klasę lub podklasę wartość klucza.  
  
5. Tylko jeden z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutów, <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> Dodaj właściwość.  
  
     Ta właściwość służy do wyznaczania mapowania *rezerwowego* , gdy wartość rozróżniacza z tabeli bazy danych nie <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> jest zgodna z żadną wartością w mapowaniu dziedziczenia.  
  
6. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> dla atrybutu.  
  
     Ta właściwość oznacza, że jest to kolumna, która zawiera <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartość.  
  
## <a name="example"></a>Przykład  
  
> [!NOTE]
> Jeśli używasz programu Visual Studio, możesz użyć Object Relational Designer, aby skonfigurować dziedziczenie. Zobacz [How to: Konfigurowanie dziedziczenia za pomocą narzędzia Object Relational Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 W poniższym przykładzie `Vehicle` kodu jest zdefiniowany jako Klasa główna, a poprzednie kroki zostały zaimplementowane w celu opisania hierarchii dla programu [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa dziedziczenia](inheritance-support.md)
- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
