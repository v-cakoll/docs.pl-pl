---
title: Operation — klasa
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 16de8b25594896349ea546d3def52dd256fe5c70
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180942"
---
# <a name="operation-class"></a>Operation — klasa
Operacja  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa Operation nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa Operation ma następujące właściwości:  
  
### <a name="action"></a>Akcja  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Akcja WS-Addressing komunikatu żądania.  
  
### <a name="asyncpattern"></a>Wzorca asynchronicznego  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje, że operacja jest wykonywane asynchronicznie za pomocą `Begin`[/ zamykającego nawiasy kątowe] i `End`pary — metoda [nawiasy otwarte i zamknięte] w kontrakcie usługi.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: zachowanie tablicy  
  
 Dostęp do typu: tylko do odczytu  
  
 Zachowania skojarzone z tą operacją.  
  
### <a name="iscallback"></a>IsCallback  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość true, gdy operacja jest operacji wywołania zwrotnego.  
  
### <a name="isinitiating"></a>IsInitiating  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje, czy metoda implementuje operację, która może zainicjować sesję na serwerze.  
  
### <a name="isoneway"></a>Ustawienie właściwości IsOneWay  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje, czy operacja zwraca komunikat odpowiedzi.  
  
### <a name="isterminating"></a>IsTerminating  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje, czy operacja zwraca komunikat odpowiedzi.  
  
### <a name="methodsignature"></a>MethodSignature  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Podpis metody operacji.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Nazwa operacji.  
  
### <a name="parametertypes"></a>ParameterTypes  
 Typ danych: tablica ciągów  
  
 Dostęp do typu: tylko do odczytu  
  
 Typy parametrów operacji.  
  
### <a name="replyaction"></a>Parametr ReplyAction  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość Akcja SOAP komunikat odpowiedzi operacji.  
  
### <a name="returntype"></a>ReturnType  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Zwracany typ operacji.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.OperationDescription>
