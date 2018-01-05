---
title: "Porady: Określanie nazwy bazy danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d0dffe22205b2d59dbd77bcd8f86efe4fa56be3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-database-names"></a>Porady: Określanie nazwy bazy danych
Użyj <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwość <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu, aby określić nazwę bazy danych, kiedy nie podano nazwy dla tego połączenia.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### <a name="to-specify-the-name-of-the-database"></a>Aby określić nazwę bazy danych  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu deklaracji klasy dla bazy danych.  
  
2.  Dodaj <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwości <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu.  
  
3.  Ustaw <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> wartość właściwości na nazwę, która ma zostać określony.  
  
## <a name="see-also"></a>Zobacz też  
 [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
