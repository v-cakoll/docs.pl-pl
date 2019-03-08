---
title: Delegaty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
  - 'delegates [Visual Basic]'
  - 'Visual Basic code, delegates'
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
---

# <a name="delegates-visual-basic"></a>Delegaty (Visual Basic)

Obiekty delegowane są obiekty, które odwołują się do metody. Są czasami określane jako *wskaźniki funkcji bezpiecznego typu* ponieważ są one podobne do wskaźników funkcji używanych w innych językach programowania. Ale w przeciwieństwie do wskaźników funkcji delegatów w języku Visual Basic typu odwołania na podstawie klasy <xref:System.Delegate?displayProperty=nameWithType>. Delegatów można odwoływać się do obu metod udostępnionego — metody, które mogą być wywoływane bez określonego wystąpienia klasy — lub wystąpienie metody.

## <a name="delegates-and-events"></a>Delegaci i zdarzenia

Delegaty są przydatne w sytuacjach, w którym ma być pośrednik pomiędzy procedury wywołującej i procedury, wywoływana. Na przykład możesz zechcieć obiekt, który wywołuje zdarzenia, aby można było wywołać procedury obsługi zdarzeń różne w różnych okolicznościach. Niestety obiekt wywoływanie zdarzeń nie ma informacji wcześniejsze obsługi zdarzeń, które obsługuje określone zdarzenie. Visual Basic umożliwia obsługę zdarzeń dynamicznie Powiąż ze zdarzeniami, tworząc delegata dla Ciebie, gdy używasz `AddHandler` instrukcji. W czasie wykonywania delegat przekazuje wywołania programu obsługi zdarzeń właściwe.

Chociaż można utworzyć własne delegatów w większości przypadków Visual Basic, tworzy delegata i zajmuje się szczegółowe informacje dla Ciebie. Na przykład `Event` instrukcji niejawnie definiuje klasę delegata, o nazwie `<EventName>EventHandler` jako klasa zagnieżdżona klasa zawierającego `Event` instrukcji i z taką samą sygnaturę jak zdarzenia. `AddressOf` Instrukcja niejawnie tworzy wystąpienie delegata, która odwołuje się do określonej procedury. Następujące dwa wiersze kodu są równoważne. W pierwszym wierszu, zostanie wyświetlony jawne utworzenie wystąpienia `EventHandler`, za pomocą odwołania do metody `Button1_Click` wysyłane jako argument. Drugi wiersz jest wygodniejszy sposób zrobić to samo.

[!code-vb[VbVbalrDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#6)]

Możesz użyć skrótu sposób tworzenia delegatów w dowolnym miejscu kompilator można określić typ delegata w kontekście.

## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Typ delegata deklarującego zdarzenia, które Użyj istniejącego

W niektórych sytuacjach można zadeklarować zdarzenie, aby użyć istniejącego typu delegata jako jego podstawowy delegata. Następująca składnia pokazuje, jak:

[!code-vb[VbVbalrDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#7)]

Jest to przydatne, gdy chcesz skierować wiele zdarzeń do tego samego programu obsługi.

## <a name="delegate-variables-and-parameters"></a>Delegat zmienne i parametry

Można używać delegatów dla innych, niepowiązane zdarzenia powiązane zadania, takie jak wolnych wątków lub za pomocą procedur, które należy wywołać różne wersje funkcji w czasie wykonywania.

Załóżmy na przykład, aplikacja sklasyfikowane ad, która zawiera pola listy z nazwami samochodów. Reklam są sortowane według tytułu, który jest zwykle wykonującego samochodu. Może występować problem występuje, gdy niektóre samochodów obejmują rok samochodu przed wykonującego. Problem polega na to, że funkcje wbudowane sortowanie pola listy podczas sortowania tylko kody znaków; umieszcza wszystkie reklam, począwszy od daty najpierw, a następnie reklam, począwszy od markę.

Aby rozwiązać ten problem, można utworzyć procedury sortowania w klasie, która używa standardowych sortowania alfabetycznego na większości pola listy, ale jest w stanie przełączyć się w czasie wykonywania procedury sortowania niestandardowego samochodu reklam. Aby to zrobić, należy przekazać procedury sortowania niestandardowego do klasy sortowania w czasie wykonywania przy użyciu delegatów.

## <a name="addressof-and-lambda-expressions"></a>AddressOf, jak i wyrażenia Lambda

Każda klasa obiektu delegowanego definiuje konstruktora, który jest przekazywany do specyfikacji metody obiektu. Argument do konstruktora obiektu delegowanego musi być odwołanie do metody lub wyrażenia lambda.

Aby określić odwołanie do metody, użyj następującej składni:

`AddressOf` [`expression`.]`methodName`

Typ kompilacji `expression` musi być nazwą klasy lub interfejsu, który zawiera metodę o określonej nazwie, którego podpis pasuje do podpisu klasa obiektu delegowanego. `methodName` Może być udostępnionej metody lub metodą wystąpienia. `methodName` Nie jest opcjonalny, nawet wtedy, gdy utworzenia delegata dla metody domyślnej klasy.

Aby określić wyrażenie lambda, użyj następującej składni:

`Function` ([`parm` Jako `type`, `parm2` jako `type2`,...]) `expression`

W poniższym przykładzie pokazano oba `AddressOf` i wyrażenia lambda, używany do określenia odwołania dla delegata.

[!code-vb[VbVbalrDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class2.vb#15)]

Podpis funkcji musi być zgodny z typem delegata. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md). Aby uzyskać więcej przykładów wyrażenia lambda i `AddressOf` przypisania do delegatów, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: Wywoływanie metody delegata](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|Przykład pokazujący sposób skojarzyć metodę z delegata, a następnie wywołać tę metodę przez delegat.|
|[Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|Pokazuje, jak używać delegatów do przekazania jednej procedury do innej procedury.|
|[Swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|W tym artykule opisano, jak można przypisać subskrypcji i funkcji do delegatów lub obsługi nawet wtedy, gdy ich podpisy nie są identyczne|
|[Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)|Omówienie zdarzeń w języku Visual Basic.|
