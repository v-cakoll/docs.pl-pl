---
title: Error — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 3ecfe18392de15dc937d90565b49641415dd7e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="error-statement"></a>Error — Instrukcja
Symuluje wystąpienie błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Części  
 `errornumber`  
 Wymagana. Może być dowolnym prawidłowym numerem błędu.  
  
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
 [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Resume, instrukcja](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Komunikaty o błędach](../../../visual-basic/language-reference/error-messages/index.md)
