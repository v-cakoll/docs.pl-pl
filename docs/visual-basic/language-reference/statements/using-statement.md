---
title: Using — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 6ec0e228b3898f66f27e322b5db2dd7f3bf3d7d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352757"
---
# <a name="using-statement-visual-basic"></a>Using — Instrukcja (Visual Basic)

Deklaruje początek bloku `Using` i opcjonalnie uzyskuje zasoby systemowe, które są kontrolkami bloku.

## <a name="syntax"></a>Składnia

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>Części

|Termin|Definicja|  
|---|---|  
|`resourcelist`|Wymagane, jeśli nie podasz `resourceexpression`. Lista co najmniej jednego zasobu systemowego, który `Using` formantów bloku, rozdzielonych przecinkami.|  
|`resourceexpression`|Wymagane, jeśli nie podasz `resourcelist`. Odwołanie do zmiennej lub wyrażenia odwołującego się do zasobu systemowego, który ma być kontrolowany przez ten blok `Using`.|  
|`statements`|Opcjonalna. Blok instrukcji, które są uruchamiane przez blok `Using`.|  
|`End Using`|Wymagana. Kończy definicję bloku `Using` i usuwa wszystkie zasoby, które kontroluje.|  

 Każdy zasób w części `resourcelist` ma następującą składnię i części:

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 —lub—

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>resourceList części

|Termin|Definicja|  
|---|---|  
|`resourcename`|Wymagana. Zmienna odniesienia odwołująca się do zasobu systemowego, który kontroluje blok `Using`.|  
|`New`|Wymagane, jeśli instrukcja `Using` uzyskuje zasób. Jeśli zasób został już pobrany, użyj drugiej alternatywy składni.|  
|`resourcetype`|Wymagana. Klasa zasobu. Klasa musi implementować interfejs <xref:System.IDisposable>.|  
|`arglist`|Opcjonalna. Lista argumentów przekazywana do konstruktora, aby utworzyć wystąpienie `resourcetype`. Zobacz [listę parametrów](parameter-list.md).|  
|`resourceexpression`|Wymagana. Zmienna lub wyrażenie odwołujące się do zasobu systemowego spełniającego wymagania `resourcetype`. Jeśli używasz drugiej alternatywy składni, musisz uzyskać zasób przed przekazaniem kontroli do instrukcji `Using`.|  
  
## <a name="remarks"></a>Uwagi

 Czasami kod wymaga niezarządzanego zasobu, takiego jak dojście do pliku, otoka COM lub połączenie SQL. Blok `Using` gwarantuje usunięcie jednego lub większej liczby takich zasobów, gdy kod zostanie ukończony z nimi. Sprawia to, że są one dostępne do użycia w innym kodzie.

 Zarządzane zasoby są usuwane przez .NET Framework Moduł wyrzucania elementów bezużytecznych (GC) bez żadnego dodatkowego kodowania w części. Nie jest potrzebny blok `Using` dla zarządzanych zasobów. Można jednak nadal używać bloku `Using`, aby wymusić usunięcie zarządzanego zasobu, zamiast czekać na Moduł wyrzucania elementów bezużytecznych.

 Blok `Using` ma trzy części: pozyskiwanie, użycie i usuwanie.

- *Pozyskiwanie* oznacza tworzenie zmiennej i Inicjowanie jej w celu odwoływania się do zasobu systemowego. Instrukcja `Using` może uzyskać jeden lub więcej zasobów lub można uzyskać dokładnie jeden zasób przed wprowadzeniem bloku i przekazać go do instrukcji `Using`. W przypadku podania `resourceexpression`należy nabyć zasób przed przekazaniem kontroli do instrukcji `Using`.

- *Użycie* oznacza uzyskiwanie dostępu do zasobów i wykonywanie do nich działań. Instrukcje między `Using` i `End Using` reprezentują użycie zasobów.

- *Usuwanie* oznacza wywołanie metody <xref:System.IDisposable.Dispose%2A> na obiekcie w `resourcename`. Dzięki temu obiekt może czyścić swoje zasoby. Instrukcja `End Using` usuwa zasoby w kontrolce `Using` bloku.

## <a name="behavior"></a>Zachowanie

 Blok `Using` zachowuje się jak `Try`...`Finally` konstrukcja, w której blok `Try` używa zasobów i bloku `Finally`. W związku z tym blok `Using` gwarantuje usunięcie zasobów bez względu na sposób zamykania bloku. Jest to prawdziwe nawet w przypadku nieobsłużonego wyjątku, z wyjątkiem <xref:System.StackOverflowException>.

 Zakres każdej zmiennej zasobów uzyskanej przez instrukcję `Using` jest ograniczony do bloku `Using`.

 W przypadku określenia więcej niż jednego zasobu systemowego w instrukcji `Using` efekt jest taki sam jak w przypadku zagnieżdżonych `Using` bloków w innym.

 Jeśli `resourcename` jest `Nothing`, żadne wywołanie do <xref:System.IDisposable.Dispose%2A> nie zostanie wykonane i żaden wyjątek nie jest zgłaszany.

## <a name="structured-exception-handling-within-a-using-block"></a>Obsługa wyjątków strukturalnych w bloku using

 Jeśli musisz obsłużyć wyjątek, który może wystąpić w bloku `Using`, możesz dodać do niego kompletny `Try`...`Finally`. Jeśli potrzebujesz obsłużyć przypadek, w którym instrukcja `Using` nie powiodła się podczas pobierania zasobu, możesz sprawdzić, czy `resourcename` jest `Nothing`.

## <a name="structured-exception-handling-instead-of-a-using-block"></a>Strukturalna obsługa wyjątków zamiast bloku using

 Jeśli potrzebujesz bardziej precyzyjnej kontroli nad przejęciem zasobów lub potrzebujesz dodatkowego kodu w bloku `Finally`, możesz ponownie napisać blok `Using` jako `Try`...`Finally` konstrukcja. W poniższym przykładzie przedstawiono szkielet `Try` i `Using` konstrukcjach, które są równoważne pozyskiwaniu i rozdysponowaniu `resource`.

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> Kod wewnątrz bloku `Using` nie powinien przypisywać obiektu w `resourcename` do innej zmiennej. Po zamknięciu bloku `Using` zasób jest usuwany, a druga zmienna nie może uzyskać dostępu do zasobu, do którego wskazuje.

## <a name="example"></a>Przykład

 Poniższy przykład tworzy plik o nazwie log. txt i zapisuje dwa wiersze tekstu do pliku. Przykład odczytuje również ten sam plik i wyświetla wiersze tekstu:

 Ponieważ klasy <xref:System.IO.TextWriter> i <xref:System.IO.TextReader> implementują interfejs <xref:System.IDisposable>, kod może użyć instrukcji `Using`, aby upewnić się, że plik jest prawidłowo zamknięty po operacji zapisu i odczytu.

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable>
- [Try...Catch...Finally, instrukcja](try-catch-finally-statement.md)
- [Instrukcje: usuwanie zasobu systemu](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
