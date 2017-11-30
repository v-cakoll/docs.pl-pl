---
title: REF (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dfc91b60c68f55def8e7f81c2c5dd068c23f6e69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ref-entity-sql"></a>REF (jednostka SQL)
Zwraca odwołanie do wystąpienia jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie zwracające wystąpienia typu jednostki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do wystąpienia określonej jednostki.  
  
## <a name="remarks"></a>Uwagi  
 Odwołanie do jednostki składa się z kluczem jednostki i nazwa zestawu jednostek. Ponieważ zestawów jednostek różnych może bazować na ten sam typ obiektu klucza danego podmiotu może występować w wielu zestawach jednostek. Jednak odwołania do obiektu jest zawsze unikatowa. Jeśli wyrażenie wejściowe reprezentuje jednostkę utrwalonego, zostanie zwrócony odwołania do tej jednostki. Jeśli wyrażenie wejściowe nie jest utrwalona jednostki, zostanie zwrócony odwołanie o wartości null.  
  
 Jeśli właściwość operator wyodrębniania (.) są używane do dostępu do właściwości jednostki, odwołanie jest automatycznie wyłuskiwany.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora REF do zwrócenia odwołania dla argumentu wejściowego jednostki. Samo zapytanie wyłuskań odwołanie, ponieważ operacja wyodrębniania właściwości (.) jest używany do dostępu do właściwości jednostki produktu. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>Zobacz też  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [KLUCZ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Definicje typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
