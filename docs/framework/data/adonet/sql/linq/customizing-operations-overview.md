---
title: "Dostosowywanie operacji: omówienie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6d3491ccd183224063c435f6b377f60b175d5383
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="customizing-operations-overview"></a>Dostosowywanie operacji: omówienie
Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamiczne SQL insert, update i operacji delete na podstawie mapowania. Jednak w praktyce zwykle chcesz dodać własne logiki biznesowej w celu zapewnienia bezpieczeństwa, weryfikacji i tak dalej.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]następujące techniki te operacje dostosowywania.  
  
## <a name="loading-options"></a>Trwa ładowanie opcji  
 Zapytania można kontrolować, ile danych związanych z urządzenie docelowe głównej są pobierane, gdy połączenie z bazą danych. Ta funkcja jest zaimplementowana w znacznym stopniu przy użyciu <xref:System.Data.Linq.DataLoadOptions>. Aby uzyskać więcej informacji, zobacz [odroczone i ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Metody częściowe  
 W jego domyślne mapowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] udostępnia metody częściowe ułatwiająca implementację logiki biznesowej. Aby uzyskać więcej informacji, zobacz [Dodawanie firm logiki przez przy użyciu metody częściowe](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Procedury składowane i funkcje zdefiniowane przez użytkownika  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje procedury składowane i funkcje zdefiniowane przez użytkownika. Procedury składowane są często używane do dostosowania operacji. Aby uzyskać więcej informacji, zobacz [procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
