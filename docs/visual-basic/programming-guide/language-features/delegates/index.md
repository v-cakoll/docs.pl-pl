---
title: Delegaci
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
ms.openlocfilehash: 1f161248fa04f8fab0e5335413e69ca565732f71
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410685"
---
# <a name="delegates-visual-basic"></a>Delegaty (Visual Basic)

Delegaty są obiektami odwołującymi się do metod. Są czasami opisywane jako *wskaźniki funkcji bezpiecznych dla typu* , ponieważ są podobne do wskaźników funkcji używanych w innych językach programowania. Ale w przeciwieństwie do wskaźników funkcji, Visual Basic delegatów jest typem referencyjnym opartym na klasie <xref:System.Delegate?displayProperty=nameWithType> . Delegaty mogą odwoływać się do obu metod wspólnych — metod, które mogą być wywoływane bez określonego wystąpienia klasy — oraz metod wystąpień.

## <a name="delegates-and-events"></a>Delegaci i zdarzenia

Delegaty są przydatne w sytuacjach, gdy potrzebujesz pośrednika między procedurą wywołującą a wywoływaną procedurą. Na przykład możesz chcieć, aby obiekt, który zgłasza zdarzenia, aby mógł wywołać inne procedury obsługi zdarzeń w różnych warunkach. Niestety, obiekt wywołujący zdarzenia nie może wiedzieć przed czasem, w którym program obsługi zdarzeń obsługuje określone zdarzenie. Visual Basic umożliwia dynamiczne kojarzenie programów obsługi zdarzeń ze zdarzeniami przez utworzenie delegata przy użyciu `AddHandler` instrukcji. W czasie wykonywania delegat przekazuje wywołania do odpowiedniego programu obsługi zdarzeń.

Chociaż można tworzyć własnych delegatów, w większości przypadków Visual Basic tworzy delegata i bierze pod uwagę szczegółowe informacje. Na przykład `Event` instrukcja niejawnie definiuje klasę delegata o nazwie `<EventName>EventHandler` jako klasę zagnieżdżoną klasy zawierającej `Event` instrukcję i z tą samą sygnaturą co zdarzenie. `AddressOf`Instrukcja niejawnie tworzy wystąpienie delegata, który odwołuje się do określonej procedury. Poniższe dwa wiersze kodu są równoważne. W pierwszym wierszu zobaczysz jawne utworzenie wystąpienia `EventHandler` , z odwołaniem do metody `Button1_Click` wysyłanej jako argument. Drugi wiersz jest bardziej wygodnym sposobem wykonania tego samego zadania.

[!code-vb[VbVbalrDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#6)]

Można użyć skróconej metody tworzenia delegatów gdziekolwiek kompilator może określić typ delegata według kontekstu.

## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Deklarowanie zdarzeń wykorzystujących istniejący typ delegata

W niektórych sytuacjach może zaistnieć potrzeba zadeklarować zdarzenie, aby użyć istniejącego typu delegata jako jego podstawowego delegata. Poniższa składnia ilustruje, jak:

[!code-vb[VbVbalrDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#7)]

Jest to przydatne, gdy chcesz skierować wiele zdarzeń do tej samej procedury obsługi.

## <a name="delegate-variables-and-parameters"></a>Delegowanie zmiennych i parametrów

Delegatów można używać do innych zadań niezwiązanych z zdarzeniami, takich jak bezpłatne wątki lub procedury, które muszą wywołać różne wersje funkcji w czasie wykonywania.

Załóżmy na przykład, że masz aplikację z klasyfikacją AD, która zawiera pole listy z nazwami samochodów. Reklamy są sortowane według tytułu, co jest zwykle markami samochodu. Problem, który może wystąpić, gdy niektóre samochody obejmują rok samochodu przed markami. Problem polega na tym, że Wbudowana funkcja sortowania pola listy sortuje tylko według kodów znaków; najpierw umieszcza wszystkie reklamy zaczynające się od dat, a następnie reklamy, rozpoczynając od marki.

Aby rozwiązać ten problem, można utworzyć procedurę sortowania w klasie, która korzysta z standardowego sortowania alfabetycznego w większości pól listy, ale jest możliwe przełączenie w czasie wykonywania do niestandardowej procedury sortowania dla reklam samochodowych. W tym celu należy przekazać niestandardową procedurę sortowania do klasy sortowania w czasie wykonywania za pomocą delegatów.

## <a name="addressof-and-lambda-expressions"></a>Wyrażenia AddressOf i lambda

Każda Klasa delegatów definiuje konstruktora, który przekazał specyfikację metody obiektu. Argument konstruktora delegata musi być odwołaniem do metody lub wyrażeniem lambda.

Aby określić odwołanie do metody, należy użyć następującej składni:

`AddressOf` [`expression`.]`methodName`

Typ czasu kompilacji `expression` musi być nazwą klasy lub interfejsem zawierającym metodę o określonej nazwie, której sygnatura pasuje do sygnatury klasy delegata. `methodName`Może to być Metoda wspólna lub metoda wystąpienia. `methodName`Nie jest opcjonalna, nawet jeśli utworzysz delegata dla metody domyślnej klasy.

Aby określić wyrażenie lambda, należy użyć następującej składni:

`Function`([ `parm` AS `type` , `parm2` AS, `type2` ...])`expression`

W poniższym przykładzie pokazano zarówno `AddressOf` wyrażenie, jak i wyrażenia lambda używane do określenia odwołania dla delegata.

[!code-vb[VbVbalrDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class2.vb#15)]

Sygnatura funkcji musi być zgodna z typem delegata. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../procedures/lambda-expressions.md). Aby uzyskać więcej przykładów wyrażenia lambda i `AddressOf` przypisań do delegatów, zobacz [Swobodna konwersja delegata](relaxed-delegate-conversion.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: wywoływanie metody delegata](how-to-invoke-a-delegate-method.md)|Zawiera przykład, który pokazuje, jak skojarzyć metodę z delegatem, a następnie wywołać tę metodę za pomocą delegata.|
|[Porady: przekazywanie procedur do innej procedury w Visual Basic](how-to-pass-procedures-to-another-procedure.md)|Pokazuje, jak używać delegatów do przekazywania jednej procedury do innej procedury.|
|[Swobodna konwersja delegatów](relaxed-delegate-conversion.md)|Opisuje, w jaki sposób można przypisać funkcje sub i Functions do delegatów lub programów obsługi nawet wtedy, gdy ich podpisy nie są identyczne.|
|[Zdarzenia](../events/index.md)|Zawiera omówienie zdarzeń w Visual Basic.|
