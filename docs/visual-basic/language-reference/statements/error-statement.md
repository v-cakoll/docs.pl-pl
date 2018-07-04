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
ms.locfileid: "33603889"
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
 Instrukcja `Error` jest obsługiwana dla zgodności z poprzednimi wersjami. W nowym kodzie, szczególnie w przypadku tworzenia obiektów, użyj metodę `Raise` obiektu `Err`, aby generować błędy w czasie wykonywania.  
  
 Jeśli `errornumber` jest zdefiniowany, instrukcja `Error` wywołuje program obsługi błędów po tym, jak do właściwości obiektu `Err` są przypisane następujące wartości domyślne:  
  
|Właściwość|Wartość|  
|--------------|-----------|  
|`Number`|Wartość określona jako argument instrukcji `Error`. Może być dowolnym prawidłowym numerem błędu.|  
|`Source`|Nazwa bieżącego projektu Visual Basic.|  
|`Description`|Wyrażenie odpowiadające zwracanej wartości tekstowej funkcji `Error` dla podanego `Number`, jeśli istnieje taki ciąg. Jeśli ciąg nie istnieje, `Description` zawiera ciąg o zerowej długości ("").|  
|`HelpFile`|W pełni kwalifikowany dysk, ścieżka i nazwa pliku odpowiedniego pliku Pomocy Visual Basic.|  
|`HelpContext`|Odpowiedni identyfikator kontekstu pomocy Visual Basic, dla błędu odpowiadającego właściwości `Number`.|  
|`LastDLLError`|Zero.|  
  
 Jeśli nie istnieje uchwyt do obsługi błędu, lub jeśli żaden nie jest włączony, komunikat o błędzie jest tworzone i wyświetlany z właściwości obiektu `Err`.  
  
> [!NOTE]
>  Niektóre aplikacje hosta Visual Basic nie mogą tworzyć obiektów. Zapoznaj się dokumentacją aplikacji aby określić, czy może ona tworzyć klasy i obiekty.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto instrukcję `Error` do wygenerowania błędu numer 11.  
  
```  
On Error Resume Next   ' Wstrzymaj przechwytywanie błędów.  
Error 11   ' Symulacja błędu "Division by zero".  
```  
  
## <a name="requirements"></a>Wymagania  
 **Przestrzeń nazw:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Resume, instrukcja](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Komunikaty o błędach](../../../visual-basic/language-reference/error-messages/index.md)
