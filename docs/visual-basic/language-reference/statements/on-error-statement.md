---
title: "On Error — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96baa5d91d0a600b84ed832fb1e3b1ed71a9d89d
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="on-error-statement-visual-basic"></a>On Error — Instrukcja (Visual Basic)
Włącza procedurę obsługi błędu, i określa lokalizację procedury w ramach procedury; można również wyłączyć procedury obsługi błędów.  
  
 Bez obsługi błędów żadnych błąd w czasie wykonywania jest krytyczny: wyświetlany jest komunikat o błędzie i zatrzymuje wykonywanie.  
  
 Jeśli to możliwe, zaleca się używać wyjątków strukturalnych obsługi w kodzie, zamiast korzystać z obsługi wyjątków bez struktury i `On Error` instrukcji. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  `Error` — Słowo kluczowe jest również używana w [Error — instrukcja](../../../visual-basic/language-reference/statements/error-statement.md), który jest obsługiwany dla zgodności z poprzednimi wersjami.  
  
## <a name="syntax"></a>Składnia  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`GoTo``line`|Włącza procedurę obsługi błędu, która rozpoczyna się w wierszu określonym w wymaganym `line` argumentu. `line` Argument jest każda etykieta wiersza lub numer wiersza. Jeśli wystąpi błąd czasu wykonywania, kontrolować gałęzie, które mają określony wiersz, uaktywnianie program obsługi błędów. Określony wiersz musi być w tej samej procedury co `On Error` nastąpi instrukcji lub błąd kompilacji.|  
|`GoTo` 0|Wyłącza włączony program obsługi błędów w bieżącej procedurze, a ponadto resetuje go do `Nothing`.|  
|`GoTo` -1|Wyłącza włączony wyjątek w bieżącej procedurze, a ponadto resetuje go do `Nothing`.|  
|`Resume Next`|Określa, czy po wystąpieniu błędu czasu wykonywania formantu jest przesyłany do instrukcji bezpośrednio po instrukcji, w którym wystąpił błąd i wykonanie jest kontynuowane od tego momentu. Skorzystaj z tego formularza zamiast `On Error GoTo` podczas uzyskiwania dostępu do obiektów.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Zalecane jest użycie Obsługa wyjątków strukturalnych w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez struktury i `On Error` instrukcji. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Program obsługi błędów "enabled" to taki, który jest włączona `On Error` instrukcji. Program obsługi błędów "active" jest włączony program obsługi, który jest w trakcie obsługi błędu.  
  
 Jeśli wystąpi błąd, gdy program obsługi błędów jest aktywne (między wystąpieniem błędu i `Resume`, `Exit Sub`, `Exit Function`, lub `Exit Property` instrukcji), program obsługi błędów w bieżącej procedurze nie może obsłużyć błąd. Zwraca sterowania do procedury wywołującej.  
  
 Wywołanie procedury ma włączony program obsługi błędów, zostanie aktywowany do obsługi błędu. Jeśli aktywne jest wywołanie procedury obsługi błędów, formant przechodzi wstecz poprzednie wywołanie procedury aż do znalezienia program obsługi błędów włączone, ale nieaktywny. Jeśli zostanie znaleziony bez obsługi błędu, błąd jest krytyczny w momencie, w którym faktycznie wystąpił.  
  
 Zawsze, gdy program obsługi błędów przekazuje kontroli z powrotem na wywołanie procedury, bieżącą procedurę staje się tej procedury. Gdy błąd jest obsługiwany przez program obsługi błędów w każdej procedury, wykonanie wznawia w bieżącej procedurze w momencie wskazywany przez `Resume` instrukcji.  
  
> [!NOTE]
>  Procedura obsługi błędów nie jest `Sub` procedury lub `Function` procedury. Jest sekcji kodu oznaczony przez etykietę wiersza lub numer wiersza.  
  
## <a name="number-property"></a>Właściwość numeru  
 Procedury obsługi błędów polegać na wartość `Number` właściwość `Err` obiekt, aby ustalić przyczynę błędu. Procedury należy przetestować lub zapisać odpowiednie wartości właściwości w `Err` obiekt przed inny błąd może wystąpić lub przed procedury, która może spowodować błąd jest wywoływana. Właściwość wartości w `Err` obiektu odzwierciedlać tylko ostatni błąd. Komunikat o błędzie skojarzony z `Err.Number` znajduje się w `Err.Description`.  
  
## <a name="throw-statement"></a>Throw — Instrukcja  
 Wystąpił błąd, który jest uruchamiany z `Err.Raise` zestawy metody `Exception` właściwości do nowo utworzone wystąpienie <xref:System.Exception> klasy. Aby zapewnić obsługę gromadzenia wyjątków typów pochodnych wyjątek `Throw` instrukcja jest obsługiwana w tym języku. To przyjmuje jeden parametr, który jest wystąpienie wyjątku, który zostanie wygenerowany. W poniższym przykładzie pokazano, jak te funkcje można użyć z istniejących obsługi obsługi wyjątków:  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Zwróć uwagę, że `On Error GoTo` instrukcji traps wszystkie błędy, niezależnie od klasy wyjątku.  
  
## <a name="on-error-resume-next"></a>On Error Resume Next  
 `On Error Resume Next`powoduje wykonanie kontynuować z instrukcją bezpośrednio po instrukcji, która spowodowała błąd czasu wykonywania, lub z instrukcją bezpośrednio po ostatnim wywołać poza zawierająca procedurę `On Error Resume Next` instrukcji. Ta instrukcja zezwala na wykonywanie kontynuowanie działania pomimo błędów czasu wykonywania. Można umieścić procedurę obsługi błędu, w których może wystąpić błąd, a nie transferowanie formantu do innej lokalizacji w ramach procedury. `On Error Resume Next` Instrukcji staje się nieaktywny, gdy jest wywoływana innej procedury, dlatego należy wykonać `On Error Resume Next` instrukcji w każdym nazywanych procedury obsługi w ramach tej procedury błędów w tekście.  
  
> [!NOTE]
>  `On Error Resume Next` Konstrukcja może być wskazane `On Error GoTo` podczas obsługi błędów wygenerowanych podczas dostępu do innych obiektów. Sprawdzanie `Err` po każdej interakcji z obiektem usuwa niejednoznaczności o tym, które obiekt uzyskano dostęp przez kod. Można zapewnić, że obiekt umieścić kod błędu w `Err.Number`, a także obiektu, który pierwotnie wygenerował błąd (obiekt określony w `Err.Source`).  
  
## <a name="on-error-goto-0"></a>On Error GoTo 0  
 `On Error GoTo 0`powoduje wyłączenie obsługi błędów w bieżącej procedurze. Nie go Określ wiersz 0 jako początku kodu obsługi błędu, nawet wtedy, gdy procedura zawiera wiersz numerowane 0. Bez `On Error GoTo 0` instrukcji, program obsługi błędów jest automatycznie wyłączana podczas procedury zostanie zakończone.  
  
## <a name="on-error-goto--1"></a>On Error GoTo -1  
 `On Error GoTo -1`Wyłącza wyjątek w bieżącej procedurze. Nawet jeśli procedura zawiera wiersz numerowane -1 nie określa wiersza -1 jako początku kodu obsługi błędu. Bez `On Error GoTo -1` instrukcji, wyjątek jest automatycznie wyłączana podczas procedury zostanie zakończone.  
  
 Aby zapobiec uruchomiony, gdy wystąpił błąd braku obsługi błędów kodu, umieszczenie `Exit Sub`, `Exit Function`, lub `Exit Property` instrukcji bezpośrednio przed procedury obsługi błędów, jak poniższy fragment:  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 W tym miejscu kodu obsługi błędu następuje `Exit Sub` instrukcji i poprzedza `End Sub` instrukcji, aby oddzielić go od przepływu procedury. Obsługa błędów kodu można umieszczać w dowolnym w procedurze.  
  
## <a name="untrapped-errors"></a>Błędy untrapped  
 Untrapped błędów w obiektach są zwracane do kontroli aplikacji, gdy obiekt jest uruchomiona jako plik wykonywalny. W środowisku programistycznym untrapped błędy są zwracane do kontroli aplikacji tylko wtedy, gdy są ustawione odpowiednie opcje. Zapoznaj się dokumentacją aplikacji opis, którego opcje powinny być ustawione podczas debugowania, sposobu ich ustawiania i czy hosta można utworzyć klasy.  
  
 W przypadku utworzenia obiektu, który uzyskuje dostęp do innych obiektów, należy spróbować obsłużyć nieobsługiwane błędy, które przekazują ponownie. Jeśli nie możesz mapować kody błędów w `Err.Number` jeden z własnych błędy i następnie przekazać je z powrotem do obiektu wywołującego. Ten błąd należy określić, dodając swój kod błędu `VbObjectError` stałej. Na przykład jeśli kod błędu 1052, przypisz go w następujący sposób:  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Błędy systemu podczas wywołania do Windows bibliotek dołączanych dynamicznie (dll) Nie wywołuj wyjątków i nie może być kolor z wyłapywanie błędów języka Visual Basic. Podczas wywoływania funkcji DLL, należy sprawdzić, każda wartość zwracana powodzenie lub Niepowodzenie (według specyfikacji interfejsu API), a w przypadku awarii, sprawdź wartość `Err` obiektu `LastDLLError` właściwości.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie najpierw używane `On Error GoTo` instrukcji, aby określić lokalizację procedury obsługi błędów w procedurze. W tym przykładzie próba dzielenia przez zero generuje 6. numer błędu. Błąd odbywa się w procedurze obsługi błędów, a następnie zwróceniem sterowania do instrukcji, która spowodowała błąd. `On Error GoTo 0` Instrukcji wyłącza wyłapywanie błędów. Następnie przy użyciu `On Error Resume Next` odroczenia błąd generują pułapki, dzięki czemu kontekst dla błędów generowanych podczas następnej instrukcji może być znane dla niektórych używana jest instrukcja. Należy pamiętać, że `Err.Clear` jest używane do czyszczenia `Err` właściwości obiektu po błędu jest obsługiwane.  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>Wymagania  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [End, instrukcja](../../../visual-basic/language-reference/statements/end-statement.md)  
 [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Resume, instrukcja](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Komunikaty o błędach](../../../visual-basic/language-reference/error-messages/index.md)  
 [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
