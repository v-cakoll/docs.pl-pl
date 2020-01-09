---
title: 'Instrukcje: mapowanie hierarchii dziedziczenia'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 737cb8743d8fd9c93cd46ebf50fba3fe554a35f2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634667"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Instrukcje: mapowanie hierarchii dziedziczenia
Aby zaimplementować mapowanie dziedziczenia w LINQ, należy określić atrybuty i właściwości atrybutów w klasie głównej hierarchii dziedziczenia, zgodnie z opisem w poniższych krokach. Deweloperzy korzystający z programu Visual Studio mogą mapować hierarchie dziedziczenia przy użyciu Object Relational Designer. Zobacz [jak: Konfigurowanie dziedziczenia przy użyciu narzędzia O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
> Dla podklas nie są wymagane żadne specjalne atrybuty ani właściwości. Należy zwrócić uwagę na to, że podklasy nie mają atrybutu <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Aby zmapować hierarchię dziedziczenia  
  
1. Dodaj atrybut <xref:System.Data.Linq.Mapping.TableAttribute> do klasy głównej.  
  
2. Także do klasy głównej, Dodaj atrybut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> dla każdej klasy w strukturze hierarchii.  
  
3. Dla każdego atrybutu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, zdefiniuj Właściwość <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
     Ta właściwość zawiera wartość, która pojawia się w tabeli bazy danych w kolumnie <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>, aby wskazać klasę lub podklasę, do której należy ten wiersz danych.  
  
4. Dla każdego atrybutu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> należy również dodać właściwość <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.  
  
     Ta właściwość zawiera wartość określającą klasę lub podklasę wartość klucza.  
  
5. Tylko jeden z atrybutów <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> Dodaj właściwość <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.  
  
     Ta właściwość służy do wyznaczania mapowania *rezerwowego* , gdy wartość rozróżniacza z tabeli bazy danych nie jest zgodna z żadną <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartością w mapowaniu dziedziczenia.  
  
6. Dodaj właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> dla atrybutu <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
     Ta właściwość oznacza, że jest to kolumna, która zawiera wartość <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
## <a name="example"></a>Przykład  
  
> [!NOTE]
> Jeśli używasz programu Visual Studio, możesz użyć Object Relational Designer, aby skonfigurować dziedziczenie. Zobacz [jak: Konfigurowanie dziedziczenia przy użyciu projektanta o/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 W poniższym przykładzie kodu `Vehicle` jest definiowana jako Klasa główna, a poprzednie kroki zostały zaimplementowane w celu opisania hierarchii dla LINQ.  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa dziedziczenia](inheritance-support.md)
- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
