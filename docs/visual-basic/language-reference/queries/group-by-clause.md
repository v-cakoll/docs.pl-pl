---
title: Group By, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: 5fce4f818e22373de7f1b37b941fd88155f3a33f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359893"
---
# <a name="group-by-clause-visual-basic"></a>Group By — Klauzula (Visual Basic)
Grupuje elementy wyniku zapytania. Może również służyć do stosowania funkcji agregujących do każdej grupy. Operacja grupowania jest oparta na jednym lub większej liczbie kluczy.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Części  
  
- `listField1`, `listField2`  
  
     Opcjonalny. Co najmniej jedno pole zmiennej zapytania lub zmienne, które jawnie identyfikują pola, które mają być uwzględnione w zgrupowanym wyniku. Jeśli nie określono żadnych pól, do pogrupowanego wyniku są uwzględniane wszystkie pola zmiennej zapytania lub zmiennych.  
  
- `keyExp1`  
  
     Wymagany. Wyrażenie, które identyfikuje klucz używany do określenia grup elementów. Można określić więcej niż jeden klucz do określenia klucza złożonego.  
  
- `keyExp2`  
  
     Opcjonalny. Co najmniej jeden dodatkowy klucz połączony z programem `keyExp1` w celu utworzenia klucza złożonego.  
  
- `aggregateList`  
  
     Wymagany. Co najmniej jedno wyrażenie określające sposób agregowania grup. Aby zidentyfikować nazwę elementu członkowskiego pogrupowanych wyników, użyj `Group` słowa kluczowego, które może znajdować się w jednej z następujących form:  
  
    ```vb  
    Into Group  
    ```  
  
     -lub-  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     Można również dołączyć funkcje agregujące, które mają zostać zastosowane do grupy.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć klauzuli, `Group By` Aby przerwać wyniki zapytania do grup. Grupowanie jest oparte na kluczu lub złożonym kluczu składającym się z wielu kluczy. Elementy, które są skojarzone z pasującymi wartościami klucza, są uwzględniane w tej samej grupie.  
  
 Użyj `aggregateList` parametru `Into` klauzuli i `Group` słowa kluczowego, aby zidentyfikować nazwę elementu członkowskiego, który jest używany do odwoływania się do grupy. Możesz również uwzględnić funkcje agregujące w `Into` klauzuli, aby obliczyć wartości dla zgrupowanych elementów. Aby zapoznać się z listą standardowych funkcji agregujących, zobacz [klauzula Aggregate](aggregate-clause.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu grupuje listę klientów w oparciu o ich lokalizację (kraj/region) i udostępnia liczbę klientów w każdej grupie. Wyniki są uporządkowane według nazwy kraju/regionu. Pogrupowane wyniki są uporządkowane według nazwy miasta.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [SELECT — klauzula](select-clause.md)
- [Klauzula from](from-clause.md)
- [Order By, klauzula](order-by-clause.md)
- [Aggregate, klauzula](aggregate-clause.md)
- [Group Join. klauzula](group-join-clause.md)
