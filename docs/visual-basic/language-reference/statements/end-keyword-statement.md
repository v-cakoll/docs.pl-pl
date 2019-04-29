---
title: End <keyword> — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 96dc8ce6b0d3b7545f5caeef43358936e426f566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638158"
---
# <a name="end-keyword-statement-visual-basic"></a>Koniec \<— słowo kluczowe > — instrukcja (Visual Basic)

Gdy następuje po nim dodatkowe słowo kluczowe, kończy definicję bloku instrukcji wynikającą z tego słowa kluczowego.

## <a name="syntax"></a>Składnia

```vb
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
|`End`|Wymagana. Kończy definicję elementu programistycznego.|
|`AddHandler`|Wymagane do zakończenia `AddHandler` uruchomione za pasujący obiekt typu metody dostępu `AddHandler` instrukcji w niestandardowym [Event — instrukcja](event-statement.md).|
|`Class`|Wymagane do zakończenia definicję klasy uruchomione za pasujący obiekt typu [Class — instrukcja](class-statement.md).|
|`Enum`|Wymagane do zakończenia definicja wyliczenia uruchomione za pasujący obiekt typu [Enum — instrukcja](enum-statement.md).|
|`Event`|Wymagane do zakończenia `Custom` definicji zdarzenia uruchomione za pasujący obiekt typu [Event — instrukcja](event-statement.md).|  
|`Function`|Wymagane do zakończenia `Function` definicji procedury uruchomione za pasujący obiekt typu [Function — instrukcja](function-statement.md). Jeśli wykonanie napotka `End Function` instrukcji, sterowanie powraca do wywołującego kodu.|
|`Get`|Wymagane do zakończenia `Property` definicji procedury uruchomione za pasujący obiekt typu [instrukcja Get](get-statement.md). Jeśli wykonanie napotka `End Get` instrukcji, sterowanie powraca do instrukcji żąda wartość właściwości.|
|`If`|Wymagane do zakończenia `If`... `Then`... `Else` block definicji uruchomione za pasujący obiekt typu `If` instrukcji. Zobacz [Jeśli... Następnie... Else — instrukcja](if-then-else-statement.md).|
|`Interface`|Wymagane do zakończenia definicji interfejsu uruchomione za pasujący obiekt typu [Interface — instrukcja](interface-statement.md).|
|`Module`|Wymagane do zakończenia definicji modułu, uruchomione za pasujący obiekt typu [Module — instrukcja](module-statement.md).|
|`Namespace`|Wymagane do zakończenia definicję przestrzeni nazw, uruchomione za pasujący obiekt typu [Namespace, instrukcja](namespace-statement.md).|
|`Operator`|Wymagane do zakończenia definicję operatora, uruchomione za pasujący obiekt typu [operator — instrukcja](operator-statement.md).|
|`Property`|Wymagane do zakończenia definicji właściwości uruchomione za pasujący obiekt typu [Property — instrukcja](property-statement.md).|
|`RaiseEvent`|Wymagane do zakończenia `RaiseEvent` uruchomione za pasujący obiekt typu metody dostępu `RaiseEvent` instrukcji w niestandardowym [Event — instrukcja](event-statement.md).|
|`RemoveHandler`|Wymagane do zakończenia `RemoveHandler` uruchomione za pasujący obiekt typu metody dostępu `RemoveHandler` instrukcji w niestandardowym [Event — instrukcja](event-statement.md).|
|`Select`|Wymagane do zakończenia `Select`... `Case` block definicji uruchomione za pasujący obiekt typu `Select` instrukcji. Zobacz [wybierz... Case — instrukcja](select-case-statement.md).  
|`Set`|Wymagane do zakończenia `Property` definicji procedury uruchomione za pasujący obiekt typu [instrukcji Set](set-statement.md). Jeśli wykonanie napotka `End Set` instrukcji, sterowanie powraca do instrukcji, ustawiając wartość właściwości.  
|`Structure`|Wymagane do zakończenia definicji struktury uruchomione za pasujący obiekt typu [Structure — instrukcja](structure-statement.md).  
|`Sub`|Wymagane do zakończenia `Sub` definicji procedury uruchomione za pasujący obiekt typu [Sub — instrukcja](sub-statement.md). Jeśli wykonanie napotka `End Sub` instrukcji, sterowanie powraca do wywołującego kodu.  
|`SyncLock`|Wymagane do zakończenia `SyncLock` block definicji uruchomione za pasujący obiekt typu `SyncLock` instrukcji. Zobacz [SyncLock — instrukcja](synclock-statement.md).  
|`Try`|Wymagane do zakończenia `Try`... `Catch`... `Finally` block definicji uruchomione za pasujący obiekt typu `Try` instrukcji. Zobacz [spróbuj... CATCH... Na koniec instrukcji](try-catch-finally-statement.md).  
|`While`|Wymagane do zakończenia `While` pętli definicji uruchomione za pasujący obiekt typu `While` instrukcji. Zobacz [podczas... Kończy While, instrukcja](while-end-while-statement.md).  
|`With`| Wymagane do zakończenia `With` block definicji uruchomione za pasujący obiekt typu `With` instrukcji. Zobacz [za pomocą... End With — instrukcja](with-end-with-statement.md).  
|||
  
## <a name="directives"></a>Dyrektyw

Jeśli są poprzedzone znakiem numeru (`#`), `End` — słowo kluczowe kończy blok preprocesora wprowadzone przez odpowiednie dyrektywy.  

```vb
#End ExternalSource
#End If
#End Region
```

|Część|Opis|
|---|---|
|`#End`|Wymagana. Kończy definicję bloku przetwarzania wstępnego.|
|`ExternalSource`|Wymagane do zakończenia blokiem zewnętrznego źródła, uruchomione za pasujący obiekt typu [#ExternalSource — dyrektywa](../directives/externalsource-directive.md).|
|`If`|Wymagane do zakończenia bloku kompilacji warunkowej, uruchomione za pasujący obiekt typu `#If` dyrektywy. See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).|
|`Region`|Wymagane do zakończenia bloku regionu źródłowego uruchomione za pasujący obiekt typu [#Region — dyrektywa](../directives/region-directive.md).|
|||

## <a name="remarks"></a>Uwagi

[Instrukcja End](end-statement.md) bez dodatkowego słowa kluczowego kończy wykonywanie natychmiast.

## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów urządzeń inteligentnych  

Instrukcja `End` bez dodatkowego słowa kluczowego nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcja End](end-statement.md)
