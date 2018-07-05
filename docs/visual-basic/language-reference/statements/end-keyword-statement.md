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
Gdy następuje po nim dodatkowe słowo kluczowe, kończy definicję bloku instrukcji, wynikającą z tego słowa kluczowego.  
  
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
|Część|Opis|
|---|---|
|`End`|Wymagane. Kończy definicję elementu programowania.|
|`AddHandler`|Wymagane do zakończenia akcesora `AddHandler`, rozpoczętego przez odpowiadającą instrukcję `AddHandler` w niestandardowej [instrukcji Event](../../../visual-basic/language-reference/statements/event-statement.md).|
|`Class`|Wymagane do zakończenia definicji klasy, rozpoczętej przez odpowiadającą [instrukcję Class](../../../visual-basic/language-reference/statements/class-statement.md).|
|`Enum`|Wymagane do zakończenia definicji wyliczenia, rozpoczętej przez odpowiadającą [instrukcję Enum](../../../visual-basic/language-reference/statements/enum-statement.md).|
|`Event`|Wymagane do zakończenia definicji zdarzenia `Custom`, rozpoczętej przez odpowiadającą [instrukcję Event](../../../visual-basic/language-reference/statements/event-statement.md).|
|`Function`|Wymagane do zakończenia definicji procedury `Function`, rozpoczętej przez odpowiadającą [instrukcję Function](../../../visual-basic/language-reference/statements/function-statement.md). Jeśli wykonanie napotka instrukcję `End Function`, sterowanie wraca do wywołującego kodu.|
|`Get`|Wymagane do zakończenia definicji procedury `Property`, rozpoczętej przez odpowiadającą [instrukcję Get](../../../visual-basic/language-reference/statements/get-statement.md). Jeśli wykonanie napotka instrukcję `End Get`, sterowania wraca do instrukcji żądającej wartość właściwości.|
|`If`|Wymagane do zakończenia definicji bloku `If`... `Then`... `Else`, rozpoczętej przez odpowiadającą instrukcję `If`. Zobacz [If... Then... Else — instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md).|
|`Interface`|Wymagane do zakończenia definicji interfejsu, rozpoczętej przez odpowiadającą [instrukcję Interface](../../../visual-basic/language-reference/statements/interface-statement.md).|
|`Module`|Wymagane do zakończenia definicji modułu, rozpoczętej przez odpowiadającą [instrukcję Module](../../../visual-basic/language-reference/statements/module-statement.md).|
|`Namespace`|Wymagane do zakończenia definicji przestrzeni nazw, rozpoczętej przez odpowiadającą [instrukcję Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).|
|`Operator`|Wymagane do zakończenia definicji operatora, rozpoczętej przez odpowiadającą [instrukcję operator](../../../visual-basic/language-reference/statements/operator-statement.md).|
|`Property`|Wymagane do zakończenia definicji właściwości, rozpoczętej przez odpowiadającą [instrukcję Property](../../../visual-basic/language-reference/statements/property-statement.md).|
|`RaiseEvent`|Wymagane do zakończenia akcesora `RaiseEvent`, rozpoczętego przez odpowiadającą instrukcję `RaiseEvent` w niestandardowej [instrukcji Event](../../../visual-basic/language-reference/statements/event-statement.md).|
|`RemoveHandler`|Wymagane do zakończenia akcesora `RemoveHandler`, rozpoczętego przez odpowiadającą instrukcję `RemoveHandler` w niestandardowej [instrukcji Event](../../../visual-basic/language-reference/statements/event-statement.md).|
|`Select`|Wymagane do zakończenia definicji bloku `Select`... `Case`, rozpoczętej przez odpowiadającą instrukcję `Select`. Zobacz [Select... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).|
|`Set`|Wymagane do zakończenia definicji procedury `Property`, rozpoczętej przez odpowiadającą [instrukcję Set](../../../visual-basic/language-reference/statements/set-statement.md). Jeśli wykonanie napotka instrukcję `End Set` sterowanie wraca do instrukcji ustawiającej wartość właściwości.|
|`Structure`|Wymagane do zakończenia definicji struktury, rozpoczętej przez odpowiadającą [instrukcję Structure](../../../visual-basic/language-reference/statements/structure-statement.md).|
|`Sub`|Wymagane do zakończenia definicji procedury `Sub`, rozpoczętej przez odpowiadającą [instrukcję Sub](../../../visual-basic/language-reference/statements/sub-statement.md). Jeśli wykonanie napotka instrukcję `End Sub` sterowanie wraca do wywołującego kodu.|
|`SyncLock`|Wymagane do zakończenia definicji bloku `SyncLock`, rozpoczętej przez odpowiadającą [instrukcję SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md)|
|`Try`|Wymagane do zakończenia definicji bloku `Try`... `Catch`... `Finally`, rozpoczętej przez odpowiadającą instrukcję `Try`. Zobacz [Try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).|
|`While`|Wymagane do zakończenia definicji pętli `While`, rozpoczętej przez odpowiadającą instrukcję `While`. Zobacz [While... End While — instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md).|
|`With`|Wymagane do zakończenia definicji bloku `With`, rozpoczętej przez odpowiadającą instrukcję `With`. Zobacz [With... End With — instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md).|
|||

## <a name="directives"></a>Dyrektywy
 Gdy poprzedzone znakiem `#`, słowo kluczowe `End` kończy blok przetwarzania wstępnego wprowadzony przez odpowiadającą dyrektywę.  
 ```
 #End ExternalSource
 #End If
 #End Region
 ```
  |Część|Opis|
  |---|---|
  |`#End`|Wymagane. Kończy definicję bloku przetwarzania wstępnego.|
  |`ExternalSource`|Wymagane do zakończenia bloku źródła zewnętrznego, rozpoczętego przez odpowiadającą [dyrektywę #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md).|
  |`If`|Wymagane do zakończenia bloku kompilacji warunkowej, rozpoczętego przez odpowiadającą dyrektywę `#If`. Zobacz [#If... Then... #Else — dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md).|
  |`Region`|Wymagane do zakończenia bloku źródłowego region, rozpoczętego przez odpowiadającą [dyrektywę #Region](../../../visual-basic/language-reference/directives/region-directive.md).|
  |||

## <a name="remarks"></a>Uwagi  
 [Instrukcja End](../../../visual-basic/language-reference/statements/end-statement.md) bez dodatkowego słowa kluczowego kończy wykonywanie natychmiast.  
  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów urządzeń inteligentnych  
 Instrukcja `End` bez dodatkowego słowa kluczowego nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz też  
 [End — instrukcja](../../../visual-basic/language-reference/statements/end-statement.md)
