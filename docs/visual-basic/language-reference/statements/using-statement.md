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
ms.openlocfilehash: 111dba1316691b9c6c999b4c021ac06dac7c7a8d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615101"
---
# <a name="using-statement-visual-basic"></a>Using — Instrukcja (Visual Basic)
Deklaruje początku `Using` zablokować, a także opcjonalnie uzyskuje zasobów systemowych, które kontroluje bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`resourcelist`|Wymagane, jeśli nie podasz `resourceexpression`. Lista jednego lub więcej zasobów systemowych, że `Using` blokowania formantów, oddzielonych przecinkami.|  
|`resourceexpression`|Wymagane, jeśli nie podasz `resourcelist`. Odwołanie do zmiennej lub wyrażenia odnoszące się do zasobu systemu będą kontrolowane przez to `Using` bloku.|  
|`statements`|Opcjonalna. Blok instrukcji, `Using` block przebiegów.|  
|`End Using`|Wymagana. Kończy definicję `Using` bloku i usuwa wszystkie zasoby, które kontroluje.|  
  
 Każdy zasób w `resourcelist` część zawiera następujące części i składni:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 —lub—  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>Części resourcelist  
  
|Termin|Definicja|  
|---|---|  
|`resourcename`|Wymagana. Zmienną odwołania, która odwołuje się do zasobu systemu, `Using` blokowania formantów.|  
|`New`|Jeśli wymagane `Using` instrukcję pobrania zasobu. Jeśli już posiadasz zasobu, należy użyć drugiej alternatywnej składni.|  
|`resourcetype`|Wymagana. Klasa zasobu. Klasa musi implementować <xref:System.IDisposable> interfejsu.|  
|`arglist`|Opcjonalna. Lista argumentów, które przekazujesz do konstruktora, aby utworzyć wystąpienie `resourcetype`. Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Wymagana. Zmiennej lub wyrażenia odnoszące się do zasobu systemu niespełniających wymagań `resourcetype`. Korzystając z drugiego alternatywnej składni, należy uzyskać zasobu przed przekazaniem kontroli do `Using` instrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 Czasami kod wymaga niezarządzany zasób, takie jak dojście do pliku, otoka COM lub połączenia SQL. A `Using` bloku gwarantuje usuwania co najmniej jeden taki zasób, po zakończeniu swój kod z nimi. Udostępnia je dla innych kod do użycia.  
  
 Zarządzane zasoby są usuwane przez moduł odśmiecania pamięci środowiska .NET Framework (GC) bez żadnych dodatkowych kodowania ze strony użytkownika. Nie ma potrzeby `Using` blok dla zarządzanych zasobów. Jednak nadal można użyć `Using` bloku, aby wymusić likwidacji zasobów zarządzanych, zamiast czekać, aż moduł odśmiecania pamięci.  
  
 A `Using` bloku ma trzy części: pozyskiwanie, użycia i usuwania.  
  
- *Pozyskiwanie* oznacza, że utworzenie zmiennej i inicjując go do odwoływania się do zasobów systemu. `Using` Poufności informacji mogą nabyć jeden lub więcej zasobów lub uzyskiwanie dokładnie jeden zasób przed wejściem bloku i dostarczenia go do `Using` instrukcji. Jeśli podasz `resourceexpression`, należy uzyskać zasobu przed przekazaniem kontrolki `Using` instrukcji.  
  
- *Użycie* oznacza, że dostęp do zasobów i wykonywania związanych z nimi czynności. Instrukcje między `Using` i `End Using` reprezentują użycie zasobów.  
  
- *Usuwanie* oznacza, że wywołanie <xref:System.IDisposable.Dispose%2A> metody dla obiektu w `resourcename`. Dzięki temu obiekt, aby prawidłowo zakończyć jego zasobów. `End Using` Instrukcji usuwa zasobów w ramach `Using` bloku sterowania.  
  
## <a name="behavior"></a>Zachowanie  
 A `Using` blok, który zachowuje się jak `Try`... `Finally` konstrukcji, w którym `Try` bloku używa zasobów i `Finally` bloku usuwa z nich. W związku z tym `Using` bloku gwarantuje likwidacji zasobów, niezależnie od tego, jak zamknąć blok. Ta zasada obowiązuje nawet w przypadku nieobsługiwany wyjątek, z wyjątkiem <xref:System.StackOverflowException>.  
  
 Zakres każdej zmiennej zasobów nabytych przez `Using` instrukcja jest ograniczona do `Using` bloku.  
  
 W przypadku określenia więcej niż jeden zasób systemowy w `Using` instrukcji, efekt jest taki sam, tak, jakby możesz zagnieżdżone `Using` blokuje w innej.  
  
 Jeśli `resourcename` jest `Nothing`, Brak wywołania <xref:System.IDisposable.Dispose%2A> jest wykonywane, i jest zgłaszany żaden wyjątek.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Obsługa w bloku przy użyciu wyjątków strukturalnych  
 Jeśli trzeba obsługiwać wyjątek, który może wystąpić w ciągu `Using` bloku, możesz dodać kompletna `Try`... `Finally` konstrukcji do niego. Jeśli potrzebujesz obsłużyć przypadek, gdzie `Using` instrukcji zakończy się niepowodzeniem podczas uzyskiwania zasobu, można przetestować, aby sprawdzić, czy `resourcename` jest `Nothing`.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Obsługa zamiast przy użyciu bloku wyjątków strukturalnych  
 Jeśli potrzebujesz bardziej precyzyjną kontrolę nad pozyskiwanie zasobów lub potrzebujesz dodatkowego kodu w `Finally` bloku, można napisać ponownie `Using` zablokować, jako `Try`... `Finally` konstrukcji. W poniższym przykładzie przedstawiono szkielet `Try` i `Using` konstrukcji, które są równoważne w pozyskiwanie i likwidacji `resource`.  
  
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
>  Kod wewnątrz `Using` bloku nie należy przypisywać obiektów w `resourcename` do innej zmiennej. Po zakończeniu `Using` bloku, zasób zostanie usunięty, a druga zmienna nie może uzyskać dostępu zasobu, na którą wskazuje.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy plik, który nosi nazwę log.txt i zapisuje dwa wiersze tekstu do pliku. Przykład również odczytuje tego samego pliku i wyświetla wiersze tekstu.  
  
 Ponieważ <xref:System.IO.TextWriter> i <xref:System.IO.TextReader> implementacji klasy <xref:System.IDisposable> interfejsu, można użyć w kodzie `Using` instrukcji, aby upewnić się, czy plik jest poprawnie zamknięte po zapisu i operacji odczytu.  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable>
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Instrukcje: Usuwanie zasobu systemu](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
