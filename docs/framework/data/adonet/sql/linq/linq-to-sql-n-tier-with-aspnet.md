---
title: N-warstwowa LINQ to SQL z użyciem ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 85ead36d1d927084c11dca1bd73a192b16e4ab7b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880751"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>N-warstwowa LINQ to SQL z użyciem ASP.NET
W aplikacjach ASP.NET, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć <xref:System.Web.UI.WebControls.LinqDataSource> formant serwera sieci Web. Kontrolka obsługuje większość logikę, która musi mieć do wykonywania zapytań względem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], przekazać dane do przeglądarki, pobrać go i prześlij ją na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> który następnie aktualizuje bazę danych. Po prostu skonfigurować kontrolki w znaczniku, a kontrolka obsługuje cały transfer danych między [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a przeglądarką. Ponieważ formant obsługuje interakcji z warstwą prezentacji a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje komunikację z warstwą danych zespół główny w wielowarstwowej aplikacji platformy ASP.NET jest o pisaniu niestandardowej logiki biznesowej.  
  
 Aby uzyskać więcej informacji na temat `LINQDataSource`, zobacz [omówienie kontrolki serwera sieci Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
