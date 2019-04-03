---
title: Error — instrukcja (Visual Basic)
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
ms.openlocfilehash: 8ac7cee2f9959bc75df165d00d3a0a67e1dd9af0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837536"
---
# <a name="error-statement"></a>Error — Instrukcja
Symuluje wystąpieniu błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Części  
 `errornumber`  
 Wymagana. Może być dowolnym prawidłowym numerem błędu.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Error` jest obsługiwana dla zgodności z poprzednimi wersjami. W nowym kodzie, szczególnie w przypadku tworzenia obiektów, użyj metody `Raise` obiektu `Err`, aby generować błędy w czasie wykonywania.  
  
 Jeśli `errornumber` jest zdefiniowany, instrukcja `Error` wywołuje program obsługi błędów po tym, jak do właściwości obiektu `Err` zostaną przypisane następujące wartości domyślne:  
  
|Właściwość|Wartość|  
|--------------|-----------|  
|`Number`||`Number`|Wartość określona jako argument `Error` instrukcji. Może być dowolnym prawidłowym numerem błędu.|  
|`Source`|Nazwa bieżącego projektu języka Visual Basic.|  
|`Description`|Wyrażenie ciągu odpowiadające zwracanej wartości funkcji `Error` dla podanej wartości `Number`, jeśli taki ciąg istnieje. Jeśli ciąg nie istnieje, wartość `Description` zawiera ciąg znaków o zerowej długości ("").|  
|`HelpFile`|W pełni kwalifikowany dysk, ścieżka i nazwa pliku odpowiedniego pliku Pomocy języka Visual Basic.|  
|`HelpContext`|Odpowiedni identyfikator kontekstu pomocy języka Visual Basic dla błędu odpowiadającego właściwości `Number`.|  
|`LastDLLError`|Zero.|  
  
 Jeśli nie istnieje program do obsługi błędów lub jeśli żaden nie jest włączony, zostaje utworzony i wyświetlony komunikat o błędzie zawierający informacje z właściwości obiektu `Err`.  
  
> [!NOTE]
>  Niektóre aplikacje hosta Visual Basic nie mogą tworzyć obiektów. Informacje o tym, czy aplikacja hosta może tworzyć klasy i obiekty, znajdziesz w jej dokumentacji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie instrukcja `Error` została użyta do wygenerowania błędu numer 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Wymagania  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume, instrukcja](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Komunikaty o błędach](../../../visual-basic/language-reference/error-messages/index.md)
