---
title: 'Dostosowywanie operacji: Omówienie'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: 48116887471709c60c9666f68c7ebdd0e6d128a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247516"
---
# <a name="customizing-operations-overview"></a>Dostosowywanie operacji: Omówienie
Domyślnie program [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamiczny SQL dla operacji INSERT, Update i DELETE na podstawie mapowania. Jednak w przypadku zwykle warto dodać własną logikę biznesową, aby zapewnić bezpieczeństwo, sprawdzanie poprawności i tak dalej.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]metody dostosowywania tych operacji obejmują następujące elementy:  
  
## <a name="loading-options"></a>Opcje ładowania  
 W zapytaniach można kontrolować, ile danych związanych z głównym celem jest pobieranych podczas łączenia się z bazą danych. Ta funkcja jest wdrażana za pomocą programu <xref:System.Data.Linq.DataLoadOptions>. Aby uzyskać więcej informacji, zobacz [odroczone względem natychmiastowego ładowania](deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Metody częściowe  
 W domyślnym mapowaniu program udostępnia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] metody częściowe, które ułatwiają wdrożenie logiki biznesowej. Aby uzyskać więcej informacji, zobacz [Dodawanie logiki biznesowej przy użyciu metod częściowych](adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Procedury składowane i funkcje zdefiniowane przez użytkownika  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje korzystanie z procedur składowanych i funkcji zdefiniowanych przez użytkownika. Procedury składowane są często używane do dostosowywania operacji. Aby uzyskać więcej informacji, zobacz [procedury składowane](stored-procedures.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md)
