---
title: End &lt;słowo kluczowe&gt; — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 8137434bfd8c26144d78b1761b784cdba4894eaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605267"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>End &lt;słowo kluczowe&gt; — instrukcja (Visual Basic)
Gdy następuje dodatkowe słowo kluczowe, kończy definicję bloku instrukcji wynikające z tego słowa kluczowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## <a name="parts"></a>Części  
 `End`  
 Wymagana. Kończy definicję elementu programowania.  
  
 `AddHandler`  
 Wymagane do zakończenia `AddHandler` akcesor rozpoczyna się od odpowiadającego mu `AddHandler` instrukcji w niestandardowej [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Class`  
 Wymagane do zakończenia definicję klasy rozpoczyna się od odpowiadającego mu [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md).  
  
 `Enum`  
 Wymagane do zakończenia definicja wyliczenia rozpoczyna się od odpowiadającego mu [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 `Event`  
 Wymagane do zakończenia `Custom` definicji zdarzenia uruchomione przez odpowiadającą jej instrukcją [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Function`  
 Wymagane do zakończenia `Function` Definicja procedury rozpoczyna się od odpowiadającego mu [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md). Jeśli wykonanie napotkał `End``Function` instrukcji sterowania zwraca do wywołującego kodu.  
  
 `Get`  
 Wymagane do zakończenia `Property` Definicja procedury rozpoczyna się od odpowiadającego mu [instrukcja Get](../../../visual-basic/language-reference/statements/get-statement.md). Jeśli wykonanie napotkał `End``Get` instrukcji sterowania zwraca do instrukcji żąda wartość właściwości.  
  
 `If`  
 Wymagane do zakończenia `If`... `Then`... `Else` zablokować definicji rozpoczyna się od odpowiadającego mu `If` instrukcji. Zobacz [Jeśli... Następnie... Else — instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md).  
  
 `Interface`  
 Wymagane do zakończenia definicji interfejsu rozpoczętej przez odpowiadającą jej instrukcją [Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md).  
  
 `Module`  
 Wymagane do zakończenia definicji modułu rozpoczyna się od odpowiadającego mu [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).  
  
 `Namespace`  
 Wymagane do zakończenia definicję przestrzeni nazw, rozpoczyna się od odpowiadającego mu [instrukcji Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).  
  
 `Operator`  
 Wymagane do zakończenia definicja operatora rozpoczętej przez odpowiadającą jej instrukcją [operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 `Property`  
 Wymagane do zakończenia definicji właściwości rozpoczyna się od odpowiadającego mu [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md).  
  
 `RaiseEvent`  
 Wymagane do zakończenia `RaiseEvent` akcesor rozpoczyna się od odpowiadającego mu `RaiseEvent` instrukcji w niestandardowej [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `RemoveHandler`  
 Wymagane do zakończenia `RemoveHandler` akcesor rozpoczyna się od odpowiadającego mu `RemoveHandler` instrukcji w niestandardowej [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Select`  
 Wymagane do zakończenia `Select`... `Case` zablokować definicji rozpoczyna się od odpowiadającego mu `Select` instrukcji. Zobacz [wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
 `Set`  
 Wymagane do zakończenia `Property` Definicja procedury rozpoczyna się od odpowiadającego mu [Instrukcja Set](../../../visual-basic/language-reference/statements/set-statement.md). Jeśli wykonanie napotkał `End``Set` instrukcji sterowania zwraca do instrukcji ustawiania wartości właściwości.  
  
 `Structure`  
 Wymagane do zakończenia definicji struktury rozpoczyna się od odpowiadającego mu [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md).  
  
 `Sub`  
 Wymagane do zakończenia `Sub` Definicja procedury rozpoczyna się od odpowiadającego mu [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md). Jeśli wykonanie napotkał `End``Sub` instrukcji sterowania zwraca do wywołującego kodu.  
  
 `SyncLock`  
 Wymagane do zakończenia `SyncLock` zablokować definicji rozpoczyna się od odpowiadającego mu `SyncLock` instrukcji. Zobacz [SyncLock — instrukcja](../../../visual-basic/language-reference/statements/synclock-statement.md).  
  
 `Try`  
 Wymagane do zakończenia `Try`... `Catch`... `Finally` zablokować definicji rozpoczyna się od odpowiadającego mu `Try` instrukcji. Zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 `While`  
 Wymagane do zakończenia `While` pętli definicji rozpoczyna się od odpowiadającego mu `While` instrukcji. Zobacz [podczas... End While — instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md).  
  
 `With`  
 Wymagane do zakończenia `With` zablokować definicji rozpoczyna się od odpowiadającego mu `With` instrukcji. Zobacz [z... End With — instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="remarks"></a>Uwagi  
 [Instrukcji End](../../../visual-basic/language-reference/statements/end-statement.md), bez dodatkowych słowa kluczowego kończy wykonywanie natychmiast.  
  
 Gdy poprzedzone znakiem numeru (`#`), `End` — słowo kluczowe kończy wprowadzone przez odpowiednie dyrektywy przetwarzania wstępnego bloku.  
  
 `#End`  
 Wymagana. Kończy definicję bloku przetwarzania wstępnego.  
  
 `#ExternalSource`  
 Wymagane do zakończenia bloku źródła zewnętrznego rozpoczyna się od odpowiadającego mu [#ExternalSource — dyrektywa](../../../visual-basic/language-reference/directives/externalsource-directive.md).  
  
 `#If`  
 Wymagane do zakończenia bloku kompilacja warunkowa rozpoczyna się od odpowiadającego mu `#If` dyrektywy. Zobacz [#If... Then... #Else — dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md).  
  
 `#Region`  
 Wymagane do zakończenia bloku region źródłowego rozpoczyna się od odpowiadającego mu [#Region — dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md).  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 `End` Instrukcja bez dodatkowych — słowo kluczowe nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz też  
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)
