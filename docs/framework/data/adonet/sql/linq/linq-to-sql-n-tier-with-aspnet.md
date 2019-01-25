---
title: LINQ to SQL N-warstwowa przy użyciu platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: e3cd5cfa34984080b0a2da418d6b6d35858053e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698690"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ to SQL N-warstwowa przy użyciu platformy ASP.NET
W [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikacje, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć <xref:System.Web.UI.WebControls.LinqDataSource> formant serwera sieci Web. Kontrolka obsługuje większość logikę, która musi mieć do wykonywania zapytań względem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], przekazać dane do przeglądarki, pobrać go i prześlij ją na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> który następnie aktualizuje bazę danych. Po prostu skonfigurować kontrolki w znaczniku, a kontrolka obsługuje cały transfer danych między [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a przeglądarką. Ponieważ formant obsługuje interakcji z warstwą prezentacji a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje komunikację z warstwą danych zespół główny w [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikacje wielowarstwowe się na pisaniu niestandardowej logiki biznesowej.  
  
 Aby uzyskać więcej informacji na temat `LINQDataSource`, zobacz [NIB: Omówienie kontrolki serwera sieci Web LinqDataSource](https://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="see-also"></a>Zobacz także
- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
