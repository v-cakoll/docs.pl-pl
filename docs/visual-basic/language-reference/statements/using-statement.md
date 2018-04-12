---
title: Using — Instrukcja (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed9cc0d04c89eac1fe342a0924dd89bb1e258a11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-visual-basic"></a>Using — Instrukcja (Visual Basic)
Deklaruje początku `Using` blokować i opcjonalnie uzyskuje zasobów systemowych, które kontroluje bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`resourcelist`|Wymagane, jeśli nie podasz `resourceexpression`. Lista zasobów systemowych, co najmniej jeden tego `Using` blokowania formantów, oddzielonych przecinkami.|  
|`resourceexpression`|Wymagane, jeśli nie podasz `resourcelist`. Odwołanie do zmiennej lub wyrażenie odwołuje się do zasobu systemu kontrolowany przez to `Using` bloku.|  
|`statements`|Opcjonalny. Blok instrukcji który `Using` blokowanie działa.|  
|`End Using`|Wymagany. Kończy definicję `Using` bloku i usuwa wszystkie zasoby, które kontroluje.|  
  
 Każdy zasób w `resourcelist` części ma następujące składni i części:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 —lub—  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>Części resourcelist  
  
|Termin|Definicja|  
|---|---|  
|`resourcename`|Wymagany. Odwołanie do zmiennej, która odwołuje się do zasobu systemu który `Using` blokowania formantów.|  
|`New`|Jeśli wymagane `Using` instrukcji uzyskuje zasobu. Jeśli już zostały nabyte zasobu, należy użyć drugiej alternatywnej składni.|  
|`resourcetype`|Wymagany. Klasa zasobu. Klasa musi implementować <xref:System.IDisposable> interfejsu.|  
|`arglist`|Opcjonalny. Lista argumentów jest przekazywany do konstruktora w celu utworzenia wystąpienia `resourcetype`. Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Wymagany. Zmiennej lub wyrażenie odwołujących się do zasobu systemu spełniających wymagania `resourcetype`. Użycie drugiej alternatywnej składni, należy uzyskać zasobu przed przekazaniem kontroli do `Using` instrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 Czasami kodu wymaga zasób niezarządzany, np. dojście do pliku, otoki COM lub połączenia SQL. A `Using` bloku gwarantuje usuwania jeden lub więcej takich zasobów, po zakończeniu kodu z nimi. Udostępnia je dla innych kodu do użycia.  
  
 Zarządzane zasoby są usuwane przez moduł zbierający elementy bezużyteczne .NET Framework (GC) bez żadnych dodatkowych kodowania ze strony użytkownika. Nie trzeba `Using` blok dla zarządzanych zasobów. Jednakże, nadal można `Using` bloku, aby wymusić usuwania zarządzanych zasobów, zamiast czekać na moduł garbage collector.  
  
 A `Using` bloku ma trzy części: nabycie, użycia i usuwania.  
  
-   *Nabycia* oznacza tworzenia zmiennej i inicjowania go do odwoływania się do zasobu systemowego. `Using` Instrukcji można pobrać co najmniej jeden zasób, lub można uzyskać dokładnie jeden zasób przed wprowadzeniem bloku i dostarczenia go do `Using` instrukcji. Jeśli podasz `resourceexpression`, należy uzyskać zasobu przed przekazaniem kontroli do `Using` instrukcji.  
  
-   *Użycie* oznacza, że uzyskanie dostępu do zasobów i wykonywania związanych z nimi czynności. Instrukcje między `Using` i `End Using` reprezentują użycia zasobów.  
  
-   *Usuwanie* sposób wywoływania <xref:System.IDisposable.Dispose%2A> metody dla obiekt w `resourcename`. Dzięki temu obiekt, aby prawidłowo zakończyć jego zasoby. `End Using` Instrukcji usuwa zasobów w ramach `Using` bloku kontroli.  
  
## <a name="behavior"></a>Zachowanie  
 A `Using` bloku zachowuje się jak `Try`... `Finally` konstrukcji, w którym `Try` bloku używa zasobów i `Finally` bloku usuwa z nich. W związku z tym `Using` bloku gwarantuje usuwania tych zasobów, niezależnie od tego, jak zakończyć bloku. Dotyczy to nawet w przypadku nieobsługiwany wyjątek, z wyjątkiem <xref:System.StackOverflowException>.  
  
 Zakres zmiennej zasobu, co uzyskaną przez `Using` instrukcji jest ograniczona do `Using` bloku.  
  
 Jeśli określono więcej niż jeden zasób systemowy w `Using` instrukcji, efekt jest taki sam, jakby użytkownik zagnieżdżone `Using` blokuje jedną w innym.  
  
 Jeśli `resourcename` jest `Nothing`, Brak wywołania <xref:System.IDisposable.Dispose%2A> następuje, i nie jest wyjątek.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Obsługa w bloku przy użyciu wyjątków strukturalnych  
 Jeśli należy do obsługi wyjątku, który może wystąpić w ramach `Using` bloku, możesz dodać pełnego `Try`... `Finally` konstrukcji do niego. Jeśli wymagana jest obsługa w przypadku których `Using` instrukcji zakończy się niepowodzeniem podczas uzyskiwania zasobu, możesz przetestować, aby sprawdzić, czy `resourcename` jest `Nothing`.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Obsługi zamiast za pomocą bloku wyjątków strukturalnych  
 Jeśli potrzebujesz bardziej precyzyjną kontrolę nad nabywania zasobów lub konieczne dodatkowy kod w `Finally` bloku, można ponownie napisać `Using` zablokować jako `Try`... `Finally` konstrukcji. W poniższym przykładzie przedstawiono szkielet `Try` i `Using` konstrukcje, które są równoważne nabycia i usuwania `resource`.  
  
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
>  Kodu wewnątrz `Using` blok, nie należy przypisywać obiektu w `resourcename` do innej zmiennej. Po zakończeniu `Using` bloku, zasób zostanie usunięty i innej zmiennej nie może uzyskać dostęp do zasobu którą wskazuje.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy plik o nazwie log.txt i zapisuje dwóch wierszy tekstu do pliku. W przykładzie również odczytuje tego samego pliku i wyświetla wiersze tekstu.  
  
 Ponieważ <xref:System.IO.TextWriter> i <xref:System.IO.TextReader> implementacji klasy <xref:System.IDisposable> interfejsu, można użyć kodu `Using` instrukcje, aby upewnić się, że plik jest poprawnie zamknięte po wykonaniu operacji zapisu i operacje odczytu.  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IDisposable>  
 [Try... CATCH... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Porady: usuwanie zasobu systemu](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
