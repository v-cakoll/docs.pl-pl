---
title: 'Porady: mapowania hierarchii dziedziczenia'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 93f3eb40e96c0735218464c8ee69a3e6fe358a03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-map-inheritance-hierarchies"></a>Porady: mapowania hierarchii dziedziczenia
Aby zaimplementować mapowania dziedziczenia w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], należy określić atrybuty i właściwości atrybutu dla klasy głównym hierarchii dziedziczenia zgodnie z opisem w poniższych krokach. Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowania hierarchii dziedziczenia. Zobacz [porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
>  Na podklasy są wymagane nie specjalne atrybutów lub właściwości. Pamiętaj, szczególnie podklasy nie mają <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Do mapowania hierarchii dziedziczenia  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.TableAttribute> do klasy głównym atrybutu.  
  
2.  Również do klasy głównym, należy dodać <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu dla każdej klasy, struktury hierarchii.  
  
3.  Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu, zdefiniuj <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> właściwości.  
  
     Ta właściwość ma wartość, która pojawia się w tabeli bazy danych w <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> kolumny, która wskazuje, które klasy lub podklasy ten wiersz danych należy.  
  
4.  Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu, należy również dodać <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> właściwości.  
  
     Ta właściwość ma wartość, która określa, które klasy lub podklasy oznacza wartość klucza.  
  
5.  Tylko na jednym z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybuty, Dodaj <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> właściwości.  
  
     Ta właściwość służy do wyznaczania *rezerwowy* mapowania, gdy wartość dyskryminatora z tabeli bazy danych nie jest zgodna z żadną <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartość mapowań dziedziczenia.  
  
6.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
     Ta właściwość oznacza, że jest to kolumna, która przechowuje <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartość.  
  
## <a name="example"></a>Przykład  
  
> [!NOTE]
>  Jeśli używasz [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] skonfigurować dziedziczenia. Zobacz [porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 W poniższym przykładzie kodu `Vehicle` jest zdefiniowany jako klasy głównym i poprzednie kroki zostały wdrożone do opisywania hierarchia [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa dziedziczenia](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)  
 [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
