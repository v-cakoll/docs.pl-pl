---
title: With...End With — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: eb8790d0d8f82232a4b10e4e0e30165745c065c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352734"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With — Instrukcja (Visual Basic)

Wykonuje szereg instrukcji, które wielokrotnie odwołują się do pojedynczego obiektu lub struktury, dzięki czemu instrukcje mogą używać uproszczonej składni podczas uzyskiwania dostępu do członków obiektu lub struktury.  W przypadku korzystania ze struktury można odczytać tylko wartości elementów członkowskich lub wywołać metody, a w przypadku próby przypisania wartości do elementów członkowskich struktury używanej w instrukcji `With...End With` należy uzyskać błąd.

## <a name="syntax"></a>Składnia

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`objectExpression`|Wymagana. Wyrażenie, które zostaje oszacowane do obiektu. Wyrażenie może być dowolnie złożone i jest sprawdzane tylko raz. Wyrażenie może być dowolnego typu danych, w tym typów podstawowych.|
|`statements`|Opcjonalna. Jedna lub więcej instrukcji między `With` i `End With`, które mogą odwoływać się do elementów członkowskich obiektu, który jest produkowany w wyniku oceny `objectExpression`.|
|`End With`|Wymagana. Kończy definicję bloku `With`.|

## <a name="remarks"></a>Uwagi

Za pomocą `With...End With`można wykonać serię instrukcji dla określonego obiektu bez podawania nazwy obiektu wiele razy. W bloku instrukcji `With` można określić element członkowski obiektu, rozpoczynając od kropki, tak jakby obiekt instrukcji `With` poprzedzał go.

Na przykład aby zmienić wiele właściwości dla jednego obiektu, należy umieścić instrukcje przypisania właściwości wewnątrz bloku `With...End With`, odwołując się do obiektu tylko raz, a nie jeden raz dla każdego przypisania właściwości.

Jeśli kod uzyskuje dostęp do tego samego obiektu w wielu instrukcjach, uzyskasz następujące korzyści przy użyciu instrukcji `With`:

- Nie musisz szacować złożonego wyrażenia wiele razy ani przypisywać wyniku do zmiennej tymczasowej, aby odwołać się do jego członków wiele razy.

- Kod staje się bardziej czytelny dzięki eliminacji powtarzających się wyrażeń kwalifikujących.

Typem danych `objectExpression` może być dowolny typ klasy lub struktury, Visual Basic a nawet typ podstawowy, taki jak `Integer`.  Jeśli `objectExpression` wyniki są inne niż obiekt, można odczytać tylko wartości elementów członkowskich lub wywołać metody, a w przypadku próby przypisania wartości do elementów członkowskich struktury używanej w instrukcji `With...End With` zostanie wyświetlony komunikat o błędzie.  Jest to ten sam błąd, który można uzyskać w przypadku wywołania metody, która zwróciła strukturę i od razu uzyskuje dostęp do wartości elementu członkowskiego wyniku funkcji, takiej jak `GetAPoint().x = 1`.  Problem w obu przypadkach jest taki, że struktura istnieje tylko na stosie wywołań i nie ma żadnego sposobu, aby członek zmodyfikowanej struktury w takich sytuacjach mógł pisać do takich lokalizacji, żeby inny kod w programie mógł obserwować zmiany.

`objectExpression` jest oceniane jednokrotnie przy wpisie do bloku. Nie można ponownie przypisać `objectExpression` z poziomu bloku `With`.

W bloku `With` można uzyskać dostęp do metod i właściwości tylko określonego obiektu bez ich kwalifikowania. Możesz użyć metod i właściwości innych obiektów, ale musisz je zakwalifikować z ich nazwami obiektów.

Można umieścić jedną instrukcję `With...End With` w innej. Zagnieżdżone instrukcje `With...End With` mogą być mylące, jeśli obiekty, które są określane jako nie są jasne z kontekstu. Musisz podać w pełni kwalifikowane odwołanie do obiektu, który znajduje się w zewnętrznym bloku `With`, gdy odwołanie do obiektu jest przywoływane wewnątrz wewnętrznego bloku `With`.

Nie można rozgałęzić do bloku instrukcji `With` spoza bloku.

Instrukcje są wykonywane tylko raz, chyba że blok zawiera pętlę. Możesz zagnieździć różne rodzaje struktur sterujących. Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

> [!NOTE]
> Możesz również użyć słowa kluczowego `With` w inicjatorach obiektów. Aby uzyskać więcej informacji i przykładów, zobacz [Inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) oraz [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).
>
> Jeśli używasz bloku `With` tylko do inicjowania właściwości lub pól obiektu, który został właśnie utworzony, rozważ użycie inicjatora obiektów.

## <a name="example"></a>Przykład

W poniższym przykładzie każdy blok `With` wykonuje serię instrukcji na pojedynczym obiekcie.

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a>Przykład

Poniższy przykład zagnieżdża instrukcje `With…End With`. W instrukcji `With` zagnieżdżonej składnia odwołuje się do obiektu wewnętrznego.

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.List%601>
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
