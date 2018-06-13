---
title: Group By — Klauzula (Visual Basic)
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
ms.openlocfilehash: 7cf688dc2e0ccd10c8bfbe5f0308f0aa808fbef0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605033"
---
# <a name="group-by-clause-visual-basic"></a>Group By — Klauzula (Visual Basic)
Grupuje elementy w wyniku zapytania. Można również zastosować funkcje agregujące do każdej grupy. Operacja grupowania jest oparta na co najmniej jeden klucz.  
  
## <a name="syntax"></a>Składnia  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Części  
  
-   `listField1`, `listField2`  
  
     Opcjonalna. Co najmniej jedno pole zmienną zapytania lub zmiennych, które jawnie określić pola do uwzględnienia w wyniku grupowanych. Jeśli nie określono pól, wszystkie pola zmienną zapytania lub zmienne są uwzględnione w grupowanych wynik.  
  
-   `keyExp1`  
  
     Wymagana. Wyrażenie identyfikujące klucz do użycia w celu określenia grupy elementów. Można określić więcej niż jednego klucza do określenia klucza złożonego.  
  
-   `keyExp2`  
  
     Opcjonalna. Jeden lub więcej dodatkowych kluczy, które są połączone z `keyExp1` można utworzyć klucza złożonego.  
  
-   `aggregateList`  
  
     Wymagana. Co najmniej jednego wyrażenia, które identyfikują agregowaniem grup. Aby zidentyfikować nazwę elementu członkowskiego grupowanych wyników, należy użyć `Group` — słowo kluczowe, które mogą być w jednym z następujących formatów:  
  
    ```  
    Into Group  
    ```  
  
     —lub—  
  
    ```  
    Into <alias> = Group  
    ```  
  
     Możesz również uwzględnić funkcje agregujące do zastosowania do grupy.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Group By` klauzuli można przerwać wyników zapytania w grupach. Grupowanie jest oparta na klucz lub klucz złożony składające się z wielu kluczy. Elementy, które są skojarzone z takimi samymi wartościami klucza znajdują się w tej samej grupie.  
  
 Możesz użyć `aggregateList` parametr `Into` klauzuli i `Group` — słowo kluczowe, aby zidentyfikować nazwę elementu członkowskiego używanego w taki sposób, aby odwołać się do grupy. Możesz również uwzględnić w funkcji agregujących `Into` klauzuli do obliczenia wartości pogrupowanych elementów. Aby uzyskać listę standardowych funkcji agregujących, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu grupuje listę klientów, na podstawie ich lokalizacji (kraj) i zapewnia liczenie klienci w każdej grupie. Wyniki są uporządkowane według nazwy kraju. Grupowanych wyniki są uporządkowane według nazwy miasta.  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Aggregate, klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Group Join, klauzula](../../../visual-basic/language-reference/queries/group-join-clause.md)
