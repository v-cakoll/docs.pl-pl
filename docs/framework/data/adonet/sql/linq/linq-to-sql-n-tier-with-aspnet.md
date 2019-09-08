---
title: N-warstwowa LINQ to SQL z użyciem ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1770d84053b57e05d1a4e41919a3eb4122dc73a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793031"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>N-warstwowa LINQ to SQL z użyciem ASP.NET
W aplikacjach [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ASP.NET korzystających z programu <xref:System.Web.UI.WebControls.LinqDataSource> można użyć kontrolki serwer sieci Web. Kontrolka obsługuje większość logiki, która musi być wymagana do wykonywania zapytań [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], przekazać dane do przeglądarki, pobrać ją i przesłać [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> do niej, a następnie zaktualizować bazę danych. Wystarczy skonfigurować kontrolkę w znaczniku, a kontrolka obsługuje cały transfer danych między [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] programem a przeglądarką. Ponieważ kontrolka obsługuje interakcje z warstwą prezentacji i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje komunikację z warstwą danych, głównym fokusem w aplikacjach wielowarstwowych ASP.NET jest tworzenie niestandardowej logiki biznesowej.  
  
 Aby uzyskać więcej informacji `LINQDataSource`na temat, zobacz temat [formant serwera sieci Web LinqDataSource — Omówienie](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
