---
title: On Error — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: 9916c7197b260436a447a84b22df9b76dc5af4cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654892"
---
# <a name="on-error-statement-visual-basic"></a>On Error — Instrukcja (Visual Basic)
Włącza procedurę obsługi błędów i określa lokalizację procedury w ramach procedury; można również wyłączyć procedury obsługi błędów.  
  
 Bez obsługi błędów dowolnego błąd w czasie wykonywania jest krytyczny: wyświetlany jest komunikat o błędzie i zatrzymuje wykonywanie.  
  
 Jeśli to możliwe, zalecamy używać wyjątków strukturalnych obsługi w kodzie zamiast korzystać z obsługi wyjątków bez określonej struktury i `On Error` instrukcji. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  `Error` — Słowo kluczowe jest również używany w [Error, instrukcja](../../../visual-basic/language-reference/statements/error-statement.md), które są obsługiwane na potrzeby utrzymywania zgodności z poprzednimi wersjami.  
  
## <a name="syntax"></a>Składnia  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`GoTo``line`|Włącza procedurę obsługi błędów, która rozpoczyna się od wiersza określonego w wymaganym `line` argumentu. `line` Argument jest każda etykieta wiersza lub numer wiersza. Jeśli wystąpi błąd czasu wykonywania, kontrolować gałęzie, które mają określony wiersz, uaktywnianie procedurę obsługi błędów. Określony wiersz musi znajdować się w tej samej procedurze co `On Error` nastąpi instrukcji lub błąd kompilacji.|  
|`GoTo` 0|Wyłącza włączoną procedurę obsługi błędów w bieżącej procedurze, a ponadto resetuje ją do `Nothing`.|  
|`GoTo` -1|Wyłącza włączony wyjątek w bieżącej procedurze, a ponadto resetuje ją do `Nothing`.|  
|`Resume Next`|Określa, że gdy wystąpi błąd czasu wykonywania, formant jest przesyłany do instrukcji od razu następującej po instrukcji, w którym wystąpił błąd, a wykonywanie jest kontynuowane od tego momentu. Użyj tego formularza zamiast `On Error GoTo` podczas uzyskiwania dostępu do obiektów.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Zalecane jest użycie strukturalna Obsługa wyjątków w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez określonej struktury i `On Error` instrukcji. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Procedura obsługi błędów "włączone" to taki, który jest włączona `On Error` instrukcji. Procedura obsługi błędów "aktywny" jest włączony program obsługi, która jest w trakcie obsługi błędu.  
  
 Jeśli wystąpi błąd, gdy procedura obsługi błędów jest aktywna (między wystąpieniem błędu i `Resume`, `Exit Sub`, `Exit Function`, lub `Exit Property` instrukcji), procedura obsługi błędów w bieżącej procedurze nie może obsłużyć błąd. Formant powraca do procedury wywołującej.  
  
 Jeśli wywołanie procedury ma włączoną procedurę obsługi błędów, zostanie aktywowany do obsługi błędu. Jeśli aktywne jest wywołanie procedury obsługi błędów, kontrola przechodzi wstecz przez poprzednie wywołania procedur, aż do znalezienia procedurę obsługi błędów włączona, ale nieaktywne, aby. Jeśli zostanie znaleziony taki obsługi błędów, błąd jest krytyczny w momencie, w którym faktycznie się pojawił.  
  
 Każdorazowo, gdy procedura obsługi błędów przekazuje sterowanie do procedury wywołującej, bieżącą procedurę staje się tej procedury. Gdy błąd jest obsługiwany przez procedurę obsługi błędów w dowolnej procedurze, wykonanie wznawia w bieżącej procedurze w punkcie, w wyznaczonym przez `Resume` instrukcji.  
  
> [!NOTE]
>  Procedura obsługi błędów nie jest `Sub` procedury lub `Function` procedury. Jest sekcji oznaczone etykietą w wierszu lub numer wiersza kodu.  
  
## <a name="number-property"></a>Number — właściwość  
 Procedury obsługi błędów opierają się na wartości w `Number` właściwość `Err` obiektu, aby ustalić przyczynę błędu. Procedura powinna testów lub zapisać odpowiednie wartości właściwości w `Err` obiekt przed innymi błąd może wystąpić, lub przed procedury, która może spowodować nazywa się błędem. Właściwość wartości w `Err` obiektu odzwierciedlają tylko ostatni błąd. Komunikat o błędzie skojarzony z `Err.Number` znajduje się w `Err.Description`.  
  
## <a name="throw-statement"></a>Throw — Instrukcja  
 Błąd, który jest wywoływany z `Err.Raise` metody ustawia `Exception` właściwości nowo utworzone wystąpienie <xref:System.Exception> klasy. W celu obsługi zgłaszania wyjątków, na których typy pochodne wyjątek `Throw` instrukcja jest obsługiwana w tym języku. To przyjmuje jeden parametr, który jest wystąpienie wyjątku, który zostanie wygenerowany. Poniższy przykład pokazuje, jak można użyć tych funkcji przy użyciu istniejących obsługi obsługi wyjątków:  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Należy zauważyć, że `On Error GoTo` instrukcji traps wszystkie błędy, niezależnie od tego, klasy wyjątku.  
  
## <a name="on-error-resume-next"></a>On Error Resume Next  
 `On Error Resume Next` powoduje wykonanie kontynuować z instrukcją natychmiast następującej po instrukcji, które spowodowały błąd czasu wykonywania, lub z instrukcją natychmiast po ostatnim wywołań poza zawierająca procedurę `On Error Resume Next` instrukcji. Ta instrukcja umożliwia kontynuowanie wykonywania pomimo błędów czasu wykonywania. Procedura obsługi błędów, gdy wystąpi błąd, a nie transferowanie formantu do innej lokalizacji w ramach procedury, można umieścić. `On Error Resume Next` Instrukcji staje się nieaktywny po wywołaniu innej procedury, dlatego należy wykonać `On Error Resume Next` instrukcji w każdym o nazwie procedury, jeśli chcesz, aby błąd wbudowanej obsługi w ramach tej procedury.  
  
> [!NOTE]
>  `On Error Resume Next` Konstrukcji może być korzystniejsze `On Error GoTo` podczas obsługi błędów wygenerowanych podczas uzyskiwania dostępu do innych obiektów. Sprawdzanie `Err` po każdym interakcji z obiektem usuwa niejednoznaczności o tym, które obiekt została otwarta przez kod. Można zapewnić, że obiektu, który jest umieszczony kod błędu w `Err.Number`, a także obiektu, który początkowo wygenerował błąd (obiekt określony w `Err.Source`).  
  
## <a name="on-error-goto-0"></a>On Error GoTo 0  
 `On Error GoTo 0` Wyłącza obsługę błędów w bieżącej procedurze. Go nie Określ wiersz 0 jako początek kodu obsługi błędu, nawet wtedy, gdy procedura zawiera wiersz numerowane 0. Bez `On Error GoTo 0` instrukcji, procedura obsługi błędów jest automatycznie wyłączana, jeśli procedura jest został zakończony.  
  
## <a name="on-error-goto--1"></a>On Error GoTo -1  
 `On Error GoTo -1` Wyłącza wyjątek w bieżącej procedurze. Nawet wtedy, gdy procedura zawiera wiersz numerowane -1 nie określa wiersza -1 jako początek kodu obsługi błędu. Bez `On Error GoTo -1` instrukcji, wyjątek jest automatycznie wyłączana, jeśli procedura jest został zakończony.  
  
 Aby zapobiec kodu obsługi błędu wystąpił błąd braku uruchomienia, umieść `Exit Sub`, `Exit Function`, lub `Exit Property` instrukcję tuż przed procedury obsługi błędów, jak poniższy fragment:  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 W tym miejscu kodu obsługi błędu następuje `Exit Sub` instrukcji i poprzedza `End Sub` instrukcję, aby oddzielić go od przepływem procedury. Kodu obsługi błędu można umieścić w dowolnym miejscu w procedurze.  
  
## <a name="untrapped-errors"></a>Błędy untrapped  
 Untrapped błędy w obiektach są zwracane do kontrolowania aplikacji, gdy obiekt jest uruchomiony jako plik wykonywalny. W środowisku deweloperskim untrapped błędy są zwracane do kontrolowania aplikacji, tylko wtedy, gdy są ustawione odpowiednie opcje. W dokumentacji aplikacji opisu, którego opcje powinna być zestaw podczas debugowania, jak ustawić je i tego, czy host można tworzyć klasy.  
  
 Jeśli tworzysz obiekt, który uzyskuje dostęp do innych obiektów, należy próbować obsłużyć nieobsługiwane błędy, które przekazują ponownie. Jeśli nie mapowanie kody błędów w `Err.Number` do jednego z własnych błędy i następnie przekaż ponownie do obiektu wywołującego obiektu. Należy określić błędu, dodając kod błędu do `VbObjectError` stałej. Na przykład jeśli kod błędu jest 1052, przypisać ją w następujący sposób:  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Błędy systemu podczas wywołania do Windows bibliotek dołączanych dynamicznie (dll) nie zgłaszaj wyjątków i nie może być zablokował z wyłapywanie błędów w Visual Basic. Podczas wywoływania funkcji DLL, należy sprawdzić, każda wartość zwracana dla powodzenia lub niepowodzenia (zgodnie ze specyfikacją interfejsu API) i wystąpi awaria, sprawdź wartość `Err` obiektu `LastDLLError` właściwości.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie najpierw zastosowano `On Error GoTo` instrukcję, aby określić lokalizację procedury obsługi błędów w procedurze. W tym przykładzie próba dzielenia przez zero generuje numer błędu 6. Obsługiwany jest błąd w procedurze obsługi błędów, a następnie zwróceniem sterowania do instrukcji, które spowodowały błąd. `On Error GoTo 0` Instrukcji powoduje wyłączenie wyłapywanie błędów. A następnie `On Error Resume Next` instrukcja jest używane, które mają być odroczone błąd generują pułapki, tak aby kontekst dla błędów generowanych podczas następnej instrukcji może być znane, w przypadku niektórych. Należy pamiętać, że `Err.Clear` jest używane do czyszczenia `Err` właściwości obiektu po obsługiwany jest błąd.  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>Wymagania  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Instrukcja End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Resume, instrukcja](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Komunikaty o błędach](../../../visual-basic/language-reference/error-messages/index.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
