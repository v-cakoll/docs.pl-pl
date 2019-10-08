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
ms.openlocfilehash: 087472c51d203be083fea0d39ade6f12066cfcb4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004736"
---
# <a name="select-clause-visual-basic"></a>Select — Klauzula (Visual Basic)
Definiuje wynik zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Części  
 `var1`  
 Opcjonalny. Alias, który może służyć do odwoływania się do wyników wyrażenia kolumny.  
  
 `fieldName1`  
 Wymagany. Nazwa pola, które ma zostać zwrócone w wyniku zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć klauzuli `Select`, aby zdefiniować wyniki do zwrócenia z zapytania. Dzięki temu można zdefiniować elementy członkowskie nowego typu anonimowego, który jest tworzony przez zapytanie lub aby wskazać elementy członkowskie typu nazwanego zwracanego przez zapytanie. Klauzula `Select` nie jest wymagana w przypadku zapytania. Jeśli nie jest określona klauzula `Select`, zapytanie zwróci typ na podstawie wszystkich elementów członkowskich zmiennych zakresu zidentyfikowanych dla bieżącego zakresu. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Gdy zapytanie tworzy nazwany typ, zwróci wynik typu <xref:System.Collections.Generic.IEnumerable%601>, gdzie `T` jest utworzonym typem.  
  
 Klauzula `Select` może odwoływać się do wszelkich zmiennych w bieżącym zakresie. Obejmuje to zmienne zakresów identyfikowane w klauzuli `From` (lub `From` klauzule). Zawiera również wszelkie nowe zmienne utworzone za pomocą aliasu przez `Aggregate`, `Let`, `Group By` lub `Group Join` klauzule lub zmienne z poprzedniej klauzuli `Select` w wyrażeniu zapytania. Klauzula `Select` może również zawierać wartości statyczne. Na przykład poniższy kod ilustruje wyrażenie zapytania, w którym klauzula `Select` definiuje wynik zapytania jako nowy typ anonimowy z czterema elementami członkowskimi: `ProductName`, `Price`, `Discount` i `DiscountedPrice`. Wartości elementów członkowskich `ProductName` i `Price` są pobierane z zmiennej zakresu produktu zdefiniowanej w klauzuli `From`. Wartość elementu członkowskiego `DiscountedPrice` jest obliczana w klauzuli `Let`. Członek `Discount` jest wartością statyczną.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 Klauzula `Select` wprowadza nowy zestaw zmiennych zakresu dla kolejnych klauzul zapytania i poprzednie zakresy nie znajdują się już w zakresie. Ostatnia klauzula `Select` w wyrażeniu zapytania określa wartość zwracaną zapytania. Na przykład następujące zapytanie zwraca nazwę firmy i identyfikator zamówienia dla każdego zamówienia klienta, dla którego suma przekracza 500. Pierwsza klauzula `Select` identyfikuje zmienne zakresów dla klauzuli `Where` i drugiej `Select` klauzuli. Druga klauzula `Select` identyfikuje wartości zwracane przez zapytanie jako nowy typ anonimowy.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Jeśli klauzula `Select` identyfikuje pojedynczy element do zwrócenia, wyrażenie zapytania zwróci kolekcję typu tego pojedynczego elementu. Jeśli klauzula `Select` identyfikuje wiele elementów do zwrócenia, wyrażenie zapytania zwróci kolekcję nowego typu anonimowego na podstawie wybranych elementów. Na przykład następujące dwa zapytania zwracają kolekcje dwóch różnych typów na podstawie klauzuli `Select`. Pierwsze zapytanie zwraca kolekcję nazw firmowych jako ciągi. Drugie zapytanie zwraca kolekcję obiektów `Customer` wypełnione informacjami o nazwach i adresach firmy.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli `From`, aby zadeklarować zmienną zakresu `cust` dla kolekcji `customers`. Klauzula `Select` wybiera wartość Nazwa i identyfikator klienta oraz wypełnia kolumny `CompanyName` i `CustomerID` nowej zmiennej zakresu. Instrukcja `For Each` pętli dla każdego zwróconego obiektu i wyświetla kolumny `CompanyName` i `CustomerID` dla każdego rekordu.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
