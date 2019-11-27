---
title: End <keyword>, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343735"
---
# <a name="end-keyword-statement-visual-basic"></a>End \<słowo kluczowe > instrukcji (Visual Basic)

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

|Części|Opis|
|---|---|
|`End`|Wymagana. Kończy definicję elementu programowania.|
|`AddHandler`|Wymagany do zakończenia metody dostępu `AddHandler` rozpoczętej przez zgodną instrukcję `AddHandler` w niestandardowej [instrukcji zdarzenia](event-statement.md).|
|`Class`|Wymagane, aby zakończyć definicję klasy rozpoczętą przez zgodną [instrukcję klasy](class-statement.md).|
|`Enum`|Wymagane, aby zakończyć definicję wyliczenia rozpoczętą przez zgodną [instrukcję enum](enum-statement.md).|
|`Event`|Wymagane, aby zakończyć `Custom` definicję zdarzenia rozpoczętą przez zgodną [instrukcję zdarzenia](event-statement.md).|  
|`Function`|Wymagane, aby zakończyć `Function` definicję procedury rozpoczętą przez zgodną [instrukcję Function](function-statement.md). Jeśli wykonanie napotka instrukcję `End Function`, sterowanie powraca do kodu wywołującego.|
|`Get`|Wymagane, aby zakończyć `Property` definicję procedury rozpoczętą przez zgodną [instrukcję Get](get-statement.md). Jeśli wykonanie napotka instrukcję `End Get`, sterowanie powraca do instrukcji żądającej wartości właściwości.|
|`If`|Wymagany do zakończenia `If`...`Then`...`Else` definicji bloku rozpoczętej przez zgodną instrukcję `If`. Sprawdź, [czy... Następnie... Else — instrukcja](if-then-else-statement.md).|
|`Interface`|Wymagane, aby zakończyć definicję interfejsu rozpoczętą przez zgodną [instrukcję interfejsu](interface-statement.md).|
|`Module`|Wymagane, aby zakończyć definicję modułu rozpoczętą przez zgodną [instrukcję modułu](module-statement.md).|
|`Namespace`|Wymagane, aby zakończyć definicję przestrzeni nazw rozpoczętą przez zgodną [instrukcję Namespace](namespace-statement.md).|
|`Operator`|Wymagane, aby zakończyć definicję operatora rozpoczętą przez zgodną [instrukcję operatora](operator-statement.md).|
|`Property`|Wymagane do zakończenia definicji właściwości rozpoczętej przez zgodną [instrukcję właściwości](property-statement.md).|
|`RaiseEvent`|Wymagany do zakończenia metody dostępu `RaiseEvent` rozpoczętej przez zgodną instrukcję `RaiseEvent` w niestandardowej [instrukcji zdarzenia](event-statement.md).|
|`RemoveHandler`|Wymagany do zakończenia metody dostępu `RemoveHandler` rozpoczętej przez zgodną instrukcję `RemoveHandler` w niestandardowej [instrukcji zdarzenia](event-statement.md).|
|`Select`|Wymagany do zakończenia `Select`...`Case` definicji bloku rozpoczętej przez zgodną instrukcję `Select`. Zobacz [Wybierz... Case — instrukcja](select-case-statement.md).  
|`Set`|Wymagane, aby zakończyć `Property` definicję procedury rozpoczętą przez zgodną [instrukcję SET](set-statement.md). Jeśli wykonanie napotka instrukcję `End Set`, sterowanie powraca do instrukcji ustawiania wartości właściwości.  
|`Structure`|Wymagane, aby zakończyć definicję struktury rozpoczętą przez zgodną [instrukcję struktury](structure-statement.md).  
|`Sub`|Wymagane, aby zakończyć `Sub` definicję procedury rozpoczętą przez pasującą [instrukcję sub](sub-statement.md). Jeśli wykonanie napotka instrukcję `End Sub`, sterowanie powraca do kodu wywołującego.  
|`SyncLock`|Wymagany do zakończenia definicji bloku `SyncLock` rozpoczętej przez zgodną instrukcję `SyncLock`. Zobacz [SyncLock instrukcji](synclock-statement.md).  
|`Try`|Wymagany do zakończenia `Try`...`Catch`...`Finally` definicji bloku rozpoczętej przez zgodną instrukcję `Try`. Zobacz [try... Catch... Finally — instrukcja](try-catch-finally-statement.md).  
|`While`|Wymagany do zakończenia `While`j definicji pętli uruchomionej przez pasującą instrukcję `While`. Zobacz [while... Instrukcja End while](while-end-while-statement.md).  
|`With`| Wymagany do zakończenia definicji bloku `With` rozpoczętej przez zgodną instrukcję `With`. Zobacz [z... End With — instrukcja](with-end-with-statement.md).  
|||
  
## <a name="directives"></a>Dyrektyw

Gdy jest poprzedzona znakiem numeru (`#`), słowo kluczowe `End` kończy blok przetwarzania wstępnego wprowadzony przez odpowiednią dyrektywę.  

```vb
#End ExternalSource
#End If
#End Region
```

|Części|Opis|
|---|---|
|`#End`|Wymagana. Kończy definicję bloku przetwarzania wstępnego.|
|`ExternalSource`|Wymagane, aby zakończyć zewnętrzny blok źródłowy rozpoczęty przez zgodną [#ExternalSource dyrektywą](../directives/externalsource-directive.md).|
|`If`|Wymagane, aby zakończyć blok kompilacji warunkowej rozpoczęty przez zgodną `#If` dyrektywę. Zobacz [#If... Następnie... #Else dyrektywy](../directives/if-then-else-directives.md).|
|`Region`|Wymagane, aby zakończyć blok regionu źródłowego rozpoczęty przez zgodną [#Region dyrektywę](../directives/region-directive.md).|
|||

## <a name="remarks"></a>Uwagi

[End](end-statement.md), bez dodatkowego słowa kluczowego, kończy wykonywanie natychmiast.

## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów urządzeń inteligentnych  

Instrukcja `End` bez słowa kluczowego New nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz także

- [End, instrukcja](end-statement.md)
