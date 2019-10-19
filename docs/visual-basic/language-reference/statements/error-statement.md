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
ms.openlocfilehash: c7b2adfe7f6b6ff5e89598cb318a90c51595ff6f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583376"
---
# <a name="error-statement"></a>Error — Instrukcja
Symuluje wystąpienie błędu.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>Części  
 `errornumber`  
 Wymagany. Może być dowolnym prawidłowym numerem błędu.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Error` jest obsługiwana w celu zapewnienia zgodności z poprzednimi wersjami. W nowym kodzie, szczególnie podczas tworzenia obiektów, użyj metody `Raise` `Err` obiektu do wygenerowania błędów w czasie wykonywania.  
  
 Jeśli `errornumber` jest zdefiniowany, instrukcja `Error` wywołuje procedurę obsługi błędów po przypisaniu właściwości obiektu `Err` do następujących wartości domyślnych:  
  
|Właściwość|Wartość|  
|--------------|-----------|  
|`Number`|Wartość określona jako argument instrukcji `Error`. Może być dowolnym prawidłowym numerem błędu.|  
|`Source`|Nazwa bieżącego projektu Visual Basic.|  
|`Description`|Wyrażenie ciągu odpowiadające wartości zwracanej funkcji `Error` dla określonego `Number`, jeśli ten ciąg istnieje. Jeśli ciąg nie istnieje, `Description` zawiera ciąg o zerowej długości ("").|  
|`HelpFile`|W pełni kwalifikowany dysk, ścieżka i nazwa pliku odpowiedniego pliku pomocy Visual Basic.|  
|`HelpContext`|Odpowiedni Visual Basic identyfikator kontekstu pliku pomocy dla błędu odpowiadającego właściwości `Number`.|  
|`LastDLLError`|Zer.|  
  
 Jeśli nie istnieje procedura obsługi błędów lub jeśli żadna nie jest włączona, zostanie utworzony komunikat o błędzie z właściwościami obiektu `Err`.  
  
> [!NOTE]
> Niektóre Visual Basic aplikacje hosta nie mogą tworzyć obiektów. Zapoznaj się z dokumentacją aplikacji hosta, aby określić, czy można tworzyć klasy i obiekty.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa instrukcji `Error` w celu wygenerowania błędu o numerze 11.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Wymagania  
 **Przestrzeń nazw:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume, instrukcja](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Komunikaty o błędach](../../../visual-basic/language-reference/error-messages/index.md)
