---
title: N-warstwowa LINQ to SQL z użyciem ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 80c12d1c9f290657a6e005063d9cc77a17354abd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103736"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>N-warstwowa LINQ to SQL z użyciem ASP.NET
W [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikacje, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć <xref:System.Web.UI.WebControls.LinqDataSource> formant serwera sieci Web. Kontrolka obsługuje większość logikę, która musi mieć do wykonywania zapytań względem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], przekazać dane do przeglądarki, pobrać go i prześlij ją na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> który następnie aktualizuje bazę danych. Po prostu skonfigurować kontrolki w znaczniku, a kontrolka obsługuje cały transfer danych między [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a przeglądarką. Ponieważ formant obsługuje interakcji z warstwą prezentacji a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje komunikację z warstwą danych zespół główny w [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikacje wielowarstwowe się na pisaniu niestandardowej logiki biznesowej.  
  
 Aby uzyskać więcej informacji na temat `LINQDataSource`, zobacz [omówienie kontrolki serwera sieci Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
