---
title: LINQ do SQL N-warstwowa ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 435f24a0f105a24bbec91a7e70dc5aaaa25e5649
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ do SQL N-warstwowa ASP.NET
W [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikacji, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć <xref:System.Web.UI.WebControls.LinqDataSource> formant serwera sieci Web. Formant obsługuje większość logikę, która musi mieć w zapytaniu dotyczącym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], przekazać dane do przeglądarki, pobrać go i przesłać je do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> który następnie aktualizuje bazę danych. Wystarczy skonfigurować formantu w znaczniku i kontrolka obsługuje wszystkie transferu danych między [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] i przeglądarki. Ponieważ formant obsługuje interakcji z warstwą prezentacji a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje komunikację z warstwą danych, a zespół główny w [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] wielowarstwowej aplikacji znajduje się na pisanie niestandardowej logiki biznesowej.  
  
 Aby uzyskać więcej informacji na temat `LINQDataSource`, zobacz [NIB: omówienie kontrolki serwera sieci Web LinqDataSource](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="see-also"></a>Zobacz też  
 [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
