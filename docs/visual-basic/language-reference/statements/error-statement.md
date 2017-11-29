---
title: "Error — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cd3245fd3e9e62b1b6443e9787c97808a0d179d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="error-statement"></a>Error — Instrukcja
Symuluje wystąpienie błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Części  
 `errornumber`  
 Wymagany. Może być dowolnym prawidłowym numerem błędu.  
  
## <a name="remarks"></a>Uwagi  
 `Error` Instrukcja jest obsługiwana dla zgodności z poprzednimi wersjami. Nowy kod, szczególnie w przypadku tworzenia obiektów, użyj `Err` obiektu `Raise` metodę, aby generować błędy czasu wykonywania.  
  
 Jeśli `errornumber` jest zdefiniowany, `Error` instrukcji wywołuje program obsługi błędów po właściwości `Err` obiektu są przypisane następujące wartości domyślne:  
  
|Właściwość|Wartość|  
|--------------|-----------|  
|`Number`|Wartość określona jako argument `Error` instrukcji. Może być dowolnym prawidłowym numerem błędu.|  
|`Source`|Nazwa bieżącego projektu Visual Basic.|  
|`Description`|Wyrażenie odpowiadające zwracanej wartości tekstowe `Error` funkcja dla określonego `Number`, jeśli istnieje ten ciąg. Jeśli ciąg nie istnieje, `Description` zawiera ciąg o zerowej długości ("").|  
|`HelpFile`|Dysk pełny, ścieżka i nazwa pliku odpowiedniego pliku Pomocy programu Visual Basic.|  
|`HelpContext`|Odpowiednie pomocy programu Visual Basic identyfikator kontekstu błąd odpowiadający do pliku `Number` właściwości.|  
|`LastDLLError`|Zero.|  
  
 Jeśli istnieje bez obsługi błędu, lub jeśli brak jest włączona, komunikat o błędzie jest tworzone i wyświetlane z `Err` właściwości obiektu.  
  
> [!NOTE]
>  Niektóre aplikacje hosta Visual Basic nie można utworzyć obiektów. Zapoznaj się dokumentacją aplikacji do określenia, czy można utworzyć w klas i obiektów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Error` instrukcję do wygenerowania 11. numer błędu.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Wymagania  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [On Error — instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Resume — instrukcja](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Komunikaty o błędach](../../../visual-basic/language-reference/error-messages/index.md)
