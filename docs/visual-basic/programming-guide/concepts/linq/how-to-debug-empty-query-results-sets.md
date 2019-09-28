---
title: 'Instrukcje: Debuguj puste zestawy wyników zapytania (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 6fc194432b1d44c1214da32d2c6978a4eeb316dc
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351780"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a>Instrukcje: Debuguj puste zestawy wyników zapytania (Visual Basic)

Jednym z najczęstszych problemów związanych z kwerendą drzewa XML jest to, że jeśli drzewo XML ma domyślną przestrzeń nazw, deweloper czasami zapisuje zapytanie tak, jakby kod XML nie był w przestrzeni nazw.

Pierwszy zestaw przykładów w tym temacie przedstawia typowy sposób ładowania kodu XML w domyślnej przestrzeni nazw i jest on nieprawidłowo przeszukiwany.

Drugi zestaw przykładów pokazuje niezbędne poprawki, aby można było zbadać kod XML w przestrzeni nazw.

Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).

## <a name="example"></a>Przykład

Ten przykład pokazuje tworzenie XML w przestrzeni nazw i zapytanie zwracające pusty zestaw wyników.

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

Ten przykład generuje następujący wynik:

```console
Result set follows:
End of result set
```

## <a name="example"></a>Przykład

Ten przykład pokazuje tworzenie kodu XML w przestrzeni nazw oraz zakodowane prawidłowo zapytanie.

Rozwiązaniem jest zadeklarowanie i zainicjowanie globalnej domyślnej przestrzeni nazw. Spowoduje to umieszczenie wszystkich właściwości XML w domyślnej przestrzeni nazw. Do poprawnego działania tego przykładu nie są wymagane żadne inne modyfikacje.

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

Ten przykład generuje następujący wynik:

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>Zobacz także

- [Zapytania podstawowe (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
