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
ms.openlocfilehash: 88707ed6c0e3e5a0ecf1f0812d31634bbdca3123
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534610"
---
# <a name="group-by-clause-visual-basic"></a>Group By — Klauzula (Visual Basic)
Grupuje elementy wyników zapytań. Można również zastosowanie funkcji agregujących do każdej grupy. W operacji grupowania opiera się na co najmniej jeden klucz.  
  
## <a name="syntax"></a>Składnia  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Części  
  
-   `listField1`, `listField2`  
  
     Opcjonalna. Co najmniej jednego pola zmienna zapytania lub zmienne, które jawnie identyfikować pola, które mają zostać uwzględnione w wynikach zgrupowane. Jeśli nie określono żadnych pól, w wyniku pogrupowanych znajdują się wszystkie pola zmienna zapytania lub zmienne.  
  
-   `keyExp1`  
  
     Wymagane. Wyrażenie identyfikujące klawisz, aby użyć do określenia grupy elementów. Można określić więcej niż jeden klucz w celu określenia klucza złożonego.  
  
-   `keyExp2`  
  
     Opcjonalna. Co najmniej jeden klucz dodatkowe, które są połączone z `keyExp1` można utworzyć klucza złożonego.  
  
-   `aggregateList`  
  
     Wymagane. Co najmniej jednego wyrażenia, które określają, jak te grupy są agregowane. Aby zidentyfikować nazwę elementu członkowskiego pogrupowane wyniki, należy użyć `Group` słowo kluczowe, które mogą znajdować się w jednej z następujących form:  
  
    ```  
    Into Group  
    ```  
  
     —lub—  
  
    ```  
    Into <alias> = Group  
    ```  
  
     Może również zawierać funkcje agregujące do zastosowania w grupie.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `Group By` klauzuli, aby przerwać wyników zapytania z grupy. Grupowanie jest oparte na klucz lub klucz złożony składający się z wielu kluczy. Elementy, które są skojarzone z takimi samymi wartościami klucza znajdują się w tej samej grupie.  
  
 Możesz użyć `aggregateList` parametru `Into` klauzuli i `Group` — słowo kluczowe, aby zidentyfikować nazwę elementu członkowskiego, służący do odwoływać się do niej. Możesz również uwzględnić w funkcjach agregujących `Into` klauzuli do obliczenia wartości pogrupowanych elementów. Aby uzyskać listę standardowych funkcji agregujących, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu grupuje listę klientów, na podstawie ich lokalizacji (kraj) i zapewnia liczenie klientom w każdej grupie. Wyniki są uporządkowane według nazwy kraju. Pogrupowane wyniki są uporządkowane według nazwy miasta.  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/index.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Klauzula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Klauzula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
