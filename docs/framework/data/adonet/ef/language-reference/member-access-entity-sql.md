---
title: . (Dostęp do elementu członkowskiego) (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 6ebedd2b381d035d199e151f64632acf7d502ff5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760626"
---
# <a name="-member-access-entity-sql"></a>. (Dostęp do elementu członkowskiego) (Jednostka SQL)
Operator kropki (.) jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operator dostępu do elementu członkowskiego. Operator dostępu do elementu członkowskiego umożliwia uzyskanie wartość właściwość lub pole wystąpienia typu modelu koncepcyjnego strukturalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Wystąpienie typu modelu koncepcyjnego strukturalnych.  
  
 `identifier`  
 Właściwość lub pole, które należy do wystąpienia obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Operator kropki (.) może służyć do wyodrębniania pól z rekordu, podobnie jak Wyodrębnianie właściwości typu złożonych lub jednostki. Na przykład jeśli n Nazwa typu jest elementem członkowskim typu osoby i p jest wystąpieniem typu osoby, p.n jest wyrażenia dostępu do elementu członkowskiego prawne, której wynikiem jest wartość typu nazwy.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
