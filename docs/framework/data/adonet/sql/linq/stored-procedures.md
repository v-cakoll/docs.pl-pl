---
title: Procedury składowane
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 198c5240a83c2bc0fcec7d1a2b3487c282adbe82
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="stored-procedures"></a>Procedury składowane
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używa metody w modelu obiektu do reprezentowania procedur przechowywanych w bazie danych. Wyznaczyć procedur składowanych jako metody, stosując <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu i, jeżeli jest to wymagane, <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutu. Aby uzyskać więcej informacji, zobacz [LINQ w modelu obiektu SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Za pomocą programu Visual Studio Deweloperzy zazwyczaj użyje [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowania procedur składowanych. Tematy w tej sekcji przedstawiają sposób tworzą i wywołania tych metod w aplikacji, podczas pisania kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Zwracane zestawy wierszy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 Zawiera opis sposobu zwracanie wszystkich wierszy danych i przedstawia sposób użycia parametru wejściowego.  
  
 [Instrukcje: Używanie procedur składowanych, które przyjmują parametry](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 Informacje dotyczące używania parametrów wejściowych i wyjściowych.  
  
 [Instrukcje: Używanie procedur składowanych zmapowanych do wielu kształtów wyników](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 Opisuje sposób zapewnienia zwraca wiele kształtów w tej samej procedury składowanej.  
  
 [Instrukcje: Używanie procedur składowanych zmapowanych do sekwencyjnych kształtów wyników](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 Opisuje sposób zapewnienia wielu kształtów, gdzie jest znany sekwencji zwrotnej.  
  
 [Dostosowywanie operacji przy użyciu procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 W tym artykule opisano sposób użycia procedury składowane służące do implementacji insert, update i operacji usuwania.  
  
 [Dostosowywanie operacji przy użyciu wyłącznie procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 Informacje dotyczące używania nic, ale procedury składowane służące do implementacji insert, update i operacji usuwania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przewodnik programowania](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Zawiera informacje o sposobie tworzenia i używania programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektu modelu.  
  
 [Przewodnik: Tylko przy użyciu procedur składowanych (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 Zawiera procedury, które przedstawiają sposób użycia procedury składowane w języku Visual Basic.  
  
 [Przewodnik: Tylko przy użyciu procedur składowanych (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 Zawiera procedury, które przedstawiają sposób użycia procedury składowane w języku C#.
