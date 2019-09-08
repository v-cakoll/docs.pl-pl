---
title: 'Instrukcje: Reprezentacja kolumn obliczanych'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 7b37e698419fae7590ac1853309a7f394917f6a0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781739"
---
# <a name="how-to-represent-computed-columns"></a>Instrukcje: Reprezentacja kolumn obliczanych
Użyj właściwości dla<xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby reprezentować kolumnę, której zawartość jest wynikiem obliczania. <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Program nie obsługuje kolumn obliczanych jako kluczy podstawowych.  
  
### <a name="to-represent-a-computed-column"></a>Aby przedstawić kolumnę obliczaną  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.  
  
2. Przypisz ciąg reprezentujący formułę do <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
