---
title: Using — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 346a26ad5751599831d8b0d3e0497e4d488eb76c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957542"
---
# <a name="using-statement-visual-basic"></a>Using — Instrukcja (Visual Basic)
Deklaruje początek `Using` bloku i opcjonalnie uzyskuje zasoby systemowe, które są kontrolkami bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`resourcelist`|Wymagane, jeśli nie podasz `resourceexpression`. Lista co najmniej jednego zasobu systemowego, który `Using` kontroluje ten blok, oddzielone przecinkami.|  
|`resourceexpression`|Wymagane, jeśli nie podasz `resourcelist`. Zmienna odniesienia lub wyrażenie odwołujące się do zasobu systemowego, który `Using` ma być kontrolowany przez ten blok.|  
|`statements`|Opcjonalna. Blok instrukcji, które są `Using` uruchamiane przez blok.|  
|`End Using`|Wymagana. Kończy definicję `Using` bloku i usuwa wszystkie zasoby, które on kontroluje.|  
  
 Każdy zasób w `resourcelist` części ma następującą składnię i części:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 —lub—  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourceList części  
  
|Termin|Definicja|  
|---|---|  
|`resourcename`|Wymagana. Zmienna odniesienia odwołująca się do zasobu systemowego `Using` , który kontroluje blok.|  
|`New`|Wymagane, `Using` Jeśli instrukcja uzyskuje zasób. Jeśli zasób został już pobrany, użyj drugiej alternatywy składni.|  
|`resourcetype`|Wymagane. Klasa zasobu. Klasa musi implementować <xref:System.IDisposable> interfejs.|  
|`arglist`|Opcjonalny. Lista argumentów przekazywana do konstruktora, aby utworzyć wystąpienie `resourcetype`. Zobacz [listę parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Wymagany. Zmienna lub wyrażenie odwołujące się do zasobu systemowego spełniającego `resourcetype`wymagania. Jeśli używasz drugiej alternatywy składni, musisz uzyskać zasób przed przekazaniem kontroli do `Using` instrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 Czasami kod wymaga niezarządzanego zasobu, takiego jak dojście do pliku, otoka COM lub połączenie SQL. `Using` Blok gwarantuje usunięcie jednego lub większej liczby takich zasobów, gdy kod zostanie zakończony. Sprawia to, że są one dostępne do użycia w innym kodzie.  
  
 Zarządzane zasoby są usuwane przez .NET Framework Moduł wyrzucania elementów bezużytecznych (GC) bez żadnego dodatkowego kodowania w części. Nie jest potrzebny `Using` blok dla zarządzanych zasobów. Można jednak nadal używać `Using` bloku, aby wymusić usunięcie zarządzanego zasobu, zamiast czekać na Moduł wyrzucania elementów bezużytecznych.  
  
 `Using` Blok ma trzy części: pozyskiwanie, użycie i usuwanie.  
  
- *Pozyskiwanie* oznacza tworzenie zmiennej i Inicjowanie jej w celu odwoływania się do zasobu systemowego. Instrukcja może uzyskać jeden lub więcej zasobów lub można uzyskać dokładnie jeden zasób przed wprowadzeniem bloku i przekazać go `Using` do instrukcji. `Using` W przypadku podania `resourceexpression`należy nabyć zasób przed przekazaniem kontroli `Using` do instrukcji.  
  
- *Użycie* oznacza uzyskiwanie dostępu do zasobów i wykonywanie do nich działań. Instrukcje między `Using` i `End Using` reprezentowania użycia zasobów.  
  
- *Usuwanie* oznacza wywołanie <xref:System.IDisposable.Dispose%2A> metody dla obiektu w `resourcename`. Dzięki temu obiekt może czyścić swoje zasoby. Instrukcja usuwa zasoby `Using` pod kontrolką bloku. `End Using`  
  
## <a name="behavior"></a>Zachowanie  
 Blok zachowuje się `Try`jak... `Using` konstrukcja, w `Try` której blok `Finally` używa zasobów i blokują elementy Dispose. `Finally` W związku z tym `Using` blok gwarantuje usunięcie zasobów bez względu na sposób zamykania bloku. Jest to prawdziwe nawet w przypadku nieobsłużonego wyjątku, z wyjątkiem <xref:System.StackOverflowException>.  
  
 Zakres każdej zmiennej zasobu uzyskanej przez `Using` instrukcję jest ograniczony `Using` do bloku.  
  
 Jeśli w `Using` instrukcji określono więcej niż jeden zasób systemowy, efekt jest taki sam, jak w przypadku zagnieżdżonych `Using` bloków w innym.  
  
 Jeśli `resourcename` <xref:System.IDisposable.Dispose%2A> jest `Nothing`, żadne wywołanie nie jest wykonywane i nie jest zgłaszany żaden wyjątek.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Obsługa wyjątków strukturalnych w bloku using  
 Jeśli musisz obsłużyć wyjątek, który może wystąpić w `Using` bloku, możesz dodać kompletną `Try`... `Finally` do niego konstrukcja. Jeśli potrzebujesz obsłużyć przypadek, w którym `Using` instrukcja nie powiodła się podczas pobierania zasobu, możesz sprawdzić, czy `resourcename` jest `Nothing`.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Strukturalna obsługa wyjątków zamiast bloku using  
 Jeśli potrzebujesz bardziej precyzyjnej kontroli nad przejęciem zasobów lub potrzebujesz dodatkowego kodu w `Finally` bloku, możesz `Using` ponownie napisać blok jako `Try`... `Finally` konstrukcja. W poniższym przykładzie przedstawiono szkielet `Try` i `Using` konstrukcje, które są równoważne podczas pozyskiwania i usuwania `resource`.  
  
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
> Kod wewnątrz `Using` bloku nie powinien przypisywać `resourcename` obiektu do innej zmiennej. Po zamknięciu `Using` bloku zasób jest usuwany, a druga zmienna nie może uzyskać dostępu do zasobu, do którego wskazuje.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy plik o nazwie log. txt i zapisuje dwa wiersze tekstu do pliku. Przykład odczytuje również ten sam plik i wyświetla wiersze tekstu.  
  
 Ponieważ klasy <xref:System.IO.TextReader> <xref:System.IDisposable> i implementują interfejs, kod może używać `Using` instrukcji, aby upewnić się, że plik jest prawidłowo zamknięty po operacji zapisu i odczytu. <xref:System.IO.TextWriter>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable>
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Instrukcje: Usuwanie zasobu systemowego](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
