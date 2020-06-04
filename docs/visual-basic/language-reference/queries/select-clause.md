---
title: Select, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: a909b1d79b10f82ece03bab788ae889c64b27124
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359697"
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
 Możesz użyć klauzuli, `Select` Aby zdefiniować wyniki do zwrócenia z zapytania. Dzięki temu można zdefiniować elementy członkowskie nowego typu anonimowego, który jest tworzony przez zapytanie lub aby wskazać elementy członkowskie typu nazwanego zwracanego przez zapytanie. `Select`Klauzula nie jest wymagana w przypadku zapytania. Jeśli `Select` klauzula nie jest określona, zapytanie zwróci typ na podstawie wszystkich elementów członkowskich zmiennych zakresu zidentyfikowanych dla bieżącego zakresu. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../programming-guide/language-features/objects-and-classes/anonymous-types.md). Gdy zapytanie tworzy nazwany typ, zwróci wynik typu, <xref:System.Collections.Generic.IEnumerable%601> gdzie `T` jest utworzony typ.  
  
 `Select`Klauzula może odwoływać się do wszelkich zmiennych w bieżącym zakresie. Obejmuje to zmienne zakresów identyfikowane w `From` klauzuli ( `From` klauzule). Zawiera również wszelkie nowe zmienne utworzone za pomocą aliasu przez `Aggregate` , `Let` , `Group By` , lub `Group Join` zmienne z poprzedniej `Select` klauzuli w wyrażeniu zapytania. `Select`Klauzula może również zawierać wartości statyczne. Na przykład poniższy kod ilustruje wyrażenie zapytania, w którym `Select` klauzula definiuje wynik zapytania jako nowy typ anonimowy z czterema elementami członkowskimi: `ProductName` , `Price` , `Discount` , i `DiscountedPrice` . `ProductName` `Price` Wartości elementów członkowskich są pobierane z zmiennej zakresu produktu zdefiniowanej w `From` klauzuli. `DiscountedPrice`Wartość elementu członkowskiego jest obliczana w `Let` klauzuli. `Discount`Element członkowski jest wartością statyczną.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select`Klauzula wprowadza nowy zestaw zmiennych zakresu dla kolejnych klauzul zapytania i poprzednie zakresy nie znajdują się już w zakresie. Ostatnia `Select` klauzula w wyrażeniu zapytania określa wartość zwracaną zapytania. Na przykład następujące zapytanie zwraca nazwę firmy i identyfikator zamówienia dla każdego zamówienia klienta, dla którego suma przekracza 500. Pierwsza `Select` klauzula identyfikuje zmienne zakresów dla `Where` klauzuli i drugiej `Select` klauzuli. Druga `Select` klauzula identyfikuje wartości zwracane przez zapytanie jako nowy typ anonimowy.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Jeśli `Select` klauzula identyfikuje pojedynczy element do zwrócenia, wyrażenie zapytania zwraca kolekcję typu tego pojedynczego elementu. Jeśli `Select` klauzula identyfikuje wiele elementów do zwrócenia, wyrażenie zapytania zwraca kolekcję nowego typu anonimowego na podstawie wybranych elementów. Na przykład następujące dwa zapytania zwracają kolekcje dwóch różnych typów na podstawie `Select` klauzuli. Pierwsze zapytanie zwraca kolekcję nazw firmowych jako ciągi. Drugie zapytanie zwraca kolekcję `Customer` obiektów uzupełnioną informacjami o nazwach i adresach firmy.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli, `From` Aby zadeklarować zmienną zakresu `cust` dla `customers` kolekcji. `Select`Klauzula wybiera nazwę i identyfikator klienta oraz wypełnia `CompanyName` `CustomerID` kolumny nowej zmiennej zakresu. `For Each`Instrukcja pętli dla każdego zwróconego obiektu i wyświetla `CompanyName` kolumny i `CustomerID` dla każdego rekordu.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [Klauzula from](from-clause.md)
- [Klauzula WHERE](where-clause.md)
- [Order By, klauzula](order-by-clause.md)
- [Typy anonimowe](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
