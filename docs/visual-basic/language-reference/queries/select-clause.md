---
title: Select — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 367d810c2358963bfe2f092a390443eccdc66941
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945265"
---
# <a name="select-clause-visual-basic"></a>Select — Klauzula (Visual Basic)
Definiuje wyniku zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Części  
 `var1`  
 Opcjonalna. Alias, który może służyć do odwołania wyniki wyrażenia kolumny.  
  
 `fieldName1`  
 Wymagana. Nazwa pola do zwrócenia w wyniku zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `Select` klauzulę, aby zdefiniować wyników do zwrócenia z zapytania. Dzięki temu można zdefiniować członkowie nowy typ anonimowy, który jest tworzony przez zapytania lub docelowych elementów członkowskich typu nazwanego, który jest zwracany przez zapytanie. `Select` Klauzula nie jest wymagana dla zapytania. Jeśli nie `Select` określono klauzulę, kwerenda będzie zwracać typ zależny od wszystkich elementów członkowskich zmiennych zakresu dla bieżącego zakresu. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Gdy zapytanie tworzy typ nazwany, zwróci wynik o typie <xref:System.Collections.Generic.IEnumerable%601> gdzie `T` jest utworzony typ.  
  
 `Select` Klauzuli można odwoływać się do żadnych zmiennych w bieżącym zakresie. Obejmuje to zmienne zakresu określonej w `From` — klauzula (lub `From` klauzule). Obejmuje również wszelkie nowe zmienne utworzone za pomocą aliasu przez `Aggregate`, `Let`, `Group By`, lub `Group Join` klauzule lub zmiennych z poprzedniego `Select` klauzula w wyrażeniu zapytania. `Select` Klauzuli mogą również obejmować wartości statyczne. Na przykład, poniższy przykład kodu pokazuje wyrażenie zapytania, w którym `Select` klauzuli definiuje wynik zapytania jako nowy typ anonimowy z cztery elementy członkowskie: `ProductName`, `Price`, `Discount`, i `DiscountedPrice`. `ProductName` i `Price` wartości elementów członkowskich są pobierane z zmiennej zakresu produktu, który jest zdefiniowany w `From` klauzuli. `DiscountedPrice` Wartość elementu członkowskiego jest obliczany w `Let` klauzuli. `Discount` Element członkowski jest wartość statyczną.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select` Klauzuli wprowadzono nowy zestaw zmiennych zakresu klauzule kolejnych zapytań i poprzedniej zmiennych zakresu nie są już w zakresie. Ostatni `Select` klauzula w wyrażeniu zapytania określa wartość zwracaną przez zapytanie. Na przykład następujące zapytanie zwraca firmy nazwy i kolejność Identyfikatora dla każdego zamówienia klienta, dla których suma przekracza 500. Pierwszy `Select` klauzula identyfikuje zmienne zakresu `Where` klauzuli, a druga `Select` klauzuli. Drugi `Select` klauzula identyfikuje wartości zwracane przez kwerendy w postaci nowym typem anonimowym.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Jeśli `Select` klauzula identyfikuje jeden element, aby powrócić, wyrażenia zapytania zwraca kolekcję typ ten pojedynczy element. Jeśli `Select` klauzula identyfikuje wielu elementów do zwrócenia, wyrażenia zapytania zwraca kolekcję nowym typem anonimowym, w oparciu o wybrane elementy. Na przykład, następujące dwa zapytania zwracają kolekcje dwa różne typy na podstawie `Select` klauzuli. Pierwsze zapytanie zwraca kolekcję nazwy firmy jako ciągi. Drugie zapytanie zwraca kolekcję `Customer` obiektów wypełniane przy użyciu nazwy firmy i informacje o adresie.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `From` klauzulę, aby zadeklarować zmienną zakresu `cust` dla `customers` kolekcji. `Select` Klauzula wybiera nazwę klienta i wartość Identyfikatora i wypełnia `CompanyName` i `CustomerID` kolumn nowej zmiennej zakresu. `For Each` Instrukcji pętli każdego zwróconego obiektu i wyświetla `CompanyName` i `CustomerID` kolumnach dla każdego rekordu.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
