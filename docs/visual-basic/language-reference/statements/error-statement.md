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
ms.openlocfilehash: 35ba1f19654d1d23ac1ec73564bc36b0af4f6777
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404748"
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
 Ta `Error` instrukcja jest obsługiwana w celu zapewnienia zgodności z poprzednimi wersjami. W nowym kodzie, szczególnie podczas tworzenia obiektów, użyj `Err` `Raise` metody obiektu do generowania błędów w czasie wykonywania.  
  
 Jeśli `errornumber` jest zdefiniowany, `Error` instrukcja wywołuje procedurę obsługi błędów po `Err` przypisaniu właściwości obiektu do następujących wartości domyślnych:  
  
|Właściwość|Wartość|  
|--------------|-----------|  
|`Number`|Wartość określona jako argument do `Error` instrukcji. Może być dowolnym prawidłowym numerem błędu.|  
|`Source`|Nazwa bieżącego projektu Visual Basic.|  
|`Description`|Wyrażenie ciągu odpowiadające wartości zwracanej `Error` funkcji dla określonej `Number` , jeśli ten ciąg istnieje. Jeśli ciąg nie istnieje, `Description` zawiera ciąg o zerowej długości ("").|  
|`HelpFile`|W pełni kwalifikowany dysk, ścieżka i nazwa pliku odpowiedniego pliku pomocy Visual Basic.|  
|`HelpContext`|Odpowiedni Visual Basic identyfikator kontekstu pliku pomocy dla błędu odpowiadającego `Number` właściwości.|  
|`LastDLLError`|Zero.|  
  
 Jeśli nie istnieje procedura obsługi błędów lub jeśli żadna nie jest włączona, zostanie utworzony komunikat o błędzie z `Err` właściwościami obiektu.  
  
> [!NOTE]
> Niektóre Visual Basic aplikacje hosta nie mogą tworzyć obiektów. Zapoznaj się z dokumentacją aplikacji hosta, aby określić, czy można tworzyć klasy i obiekty.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa `Error` instrukcji w celu wygenerowania błędu o numerze 11.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Wymagania  
 **Przestrzeń nazw:** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error, instrukcja](on-error-statement.md)
- [Resume — Instrukcja](resume-statement.md)
- [Komunikaty o błędach](../error-messages/index.md)
