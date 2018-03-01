---
title: "Select — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d8cabcbd8554ca2aee639eaac8a52f0485a266
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="select-clause-visual-basic"></a>Select — Klauzula (Visual Basic)
Definiuje wyniku zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Części  
 `var1`  
 Opcjonalny. Alias, który może służyć do odwołania wynik wyrażenia kolumny.  
  
 `fieldName1`  
 Wymagany. Nazwa pola, które ma zostać zwrócone w wyniku zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Select` klauzuli do definiowania wyników do zwrócenia z zapytania. Dzięki temu można zdefiniować elementów członkowskich nowego typu anonimowego, który jest tworzony przez zapytanie lub docelowych elementów członkowskich typu nazwanego, zwracane przez zapytanie. `Select` Klauzula nie jest wymagana dla zapytania. Jeśli nie `Select` jest określona klauzula, zapytanie zwraca typ na podstawie wszystkich elementów członkowskich zmiennych zakresu dla bieżącego zakresu. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Gdy zapytanie tworzy typ nazwany, zwróci wyniku typu <xref:System.Collections.Generic.IEnumerable%601> gdzie `T` jest utworzony typ.  
  
 `Select` Klauzuli można odwoływać się do żadnych zmiennych w bieżącym zakresie. Dotyczy to również określonych w zmiennych zakresu `From` klauzuli (lub `From` klauzule). Obejmuje też wszystkie nowe zmienne utworzone za pomocą aliasu przez `Aggregate`, `Let`, `Group By`, lub `Group Join` klauzule lub zmienne z poprzedniej `Select` klauzuli w wyrażeniu zapytania. `Select` Klauzuli mogą również obejmować wartości statyczne. Na przykład poniższy przykładowy kod przedstawia wyrażenia zapytania, w którym `Select` klauzuli definiuje wynik zapytania jako nowy typ anonimowy z czterech członków: `ProductName`, `Price`, `Discount`, i `DiscountedPrice`. `ProductName` i `Price` wartości elementów członkowskich są pobierane z zmienną zakresu produktu, który jest zdefiniowany w `From` klauzuli. `DiscountedPrice` Wartość elementu członkowskiego jest obliczane w `Let` klauzuli. `Discount` Element członkowski jest wartością statyczną.  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 `Select` Klauzuli wprowadzono nowy zestaw zmiennych zakresu klauzule kolejne zapytania i poprzednich zmiennych zakresu nie są już w zakresie. Ostatni `Select` klauzuli w wyrażeniu zapytania określa wartość zwracaną przez zapytanie. Na przykład następujące zapytanie zwraca firmy nazwy i kolejność Identyfikatora dla każdego zamówienie klienta, dla której liczba przekracza 500. Pierwszy `Select` klauzuli identyfikuje zmienne zakresu `Where` klauzuli, a drugi `Select` klauzuli. Drugi `Select` klauzuli identyfikuje wartości zwróconych przez zapytanie jako nowego typu anonimowego.  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 Jeśli `Select` klauzuli identyfikuje jeden element, aby zwrócić, wyrażenia zapytania zwraca kolekcję typu ten pojedynczy element. Jeśli `Select` klauzuli identyfikuje wielu elementów do zwrócenia, wyrażenia zapytania zwraca kolekcję nowego typu anonimowego, na podstawie wybranych elementów. Na przykład następujące dwa zapytania zwrócić kolekcje dwóch różnych typów, na podstawie `Select` klauzuli. Pierwsza kwerenda zwraca kolekcję nazw firmy jako ciągi. Drugie zapytanie zwraca kolekcję `Customer` obiektów wypełniane przy użyciu nazwy firmy i informacje o adresie.  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `From` klauzuli, aby zadeklarować zmienną zakresu `cust` dla `customers` kolekcji. `Select` Klauzuli wybiera klienta nazwa i wartość Identyfikatora i wypełnia `CompanyName` i `CustomerID` kolumn nowej zmiennej zakresu. `For Each` Instrukcji pętli każdego zwróconego obiektu i wyświetla `CompanyName` i `CustomerID` kolumn dla każdego rekordu.  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Gdy klauzula](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Order By — klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
